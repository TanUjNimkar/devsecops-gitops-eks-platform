pipeline {
    agent { label 'agent' }

    environment {
        FRONTEND_IMAGE = "tanuj7777777/wanderlust-frontend"
        BACKEND_IMAGE  = "tanuj7777777/wanderlust-backend"
        IMAGE_TAG      = "${BUILD_NUMBER}"
        SCANNER_HOME   = tool 'SonarScanner'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-token',
                    url: 'https://github.com/TanUjNimkar/devsecops-gitops-eks-platform.git'
            }
        }

        stage('Trivy Scan') {
            steps {
                sh '''
                trivy fs . --severity HIGH,CRITICAL
                '''
            }
        }

        stage('OWASP Dependency Check') {
            steps {

                catchError(
                    buildResult: 'SUCCESS',
                    stageResult: 'UNSTABLE'
                ) {

                    withCredentials([
                        string(
                            credentialsId: 'nvd-api-key',
                            variable: 'NVD_API_KEY'
                        )
                    ]) {

                        sh '''
                        /opt/dependency-check/bin/dependency-check.sh \
                        --nvdApiKey $NVD_API_KEY \
                        --scan . \
                        --format XML \
                        --format HTML \
                        --out .
                        '''
                    }
                }
            }
        }

        stage('Publish OWASP Report') {
            steps {

                catchError(
                    buildResult: 'SUCCESS',
                    stageResult: 'UNSTABLE'
                ) {

                    dependencyCheckPublisher(
                        pattern: 'dependency-check-report.xml'
                    )
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {

                withSonarQubeEnv('sonarqube') {

                    sh """
                    ${SCANNER_HOME}/bin/sonar-scanner \
                    -Dsonar.projectKey=wanderlust \
                    -Dsonar.projectName=wanderlust \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=http://3.110.168.240:9000
                    """
                }
            }
        }

        stage('Build Frontend Image') {
            steps {

                dir('frontend') {

                    sh """
                    docker build \
                    -t ${FRONTEND_IMAGE}:${IMAGE_TAG} .
                    """
                }
            }
        }

        stage('Build Backend Image') {
            steps {

                dir('backend') {

                    sh """
                    docker build \
                    -t ${BACKEND_IMAGE}:${IMAGE_TAG} .
                    """
                }
            }
        }

        stage('Push Images') {
            steps {

                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub',
                        usernameVariable: 'DOCKER_USER',
                        passwordVariable: 'DOCKER_PASS'
                    )
                ]) {

                    sh """
                    echo \$DOCKER_PASS | docker login \
                    -u \$DOCKER_USER \
                    --password-stdin

                    docker push ${FRONTEND_IMAGE}:${IMAGE_TAG}
                    docker push ${BACKEND_IMAGE}:${IMAGE_TAG}
                    """
                }
            }
        }

        stage('Update GitOps Files') {
            steps {

                sh """
                sed -i 's|image: .*wanderlust-frontend.*|image: ${FRONTEND_IMAGE}:${IMAGE_TAG}|g' kubernetes/frontend.yaml

                sed -i 's|image: .*wanderlust-backend.*|image: ${BACKEND_IMAGE}:${IMAGE_TAG}|g' kubernetes/backend.yaml
                """
            }
        }

        stage('Commit And Push Changes') {
            steps {

                withCredentials([
                    usernamePassword(
                        credentialsId: 'github-token',
                        usernameVariable: 'GIT_USER',
                        passwordVariable: 'GIT_PASS'
                    )
                ]) {

                    sh """
                    git config user.email "tanujnimkar2016@gmail.com"
                    git config user.name "Tanuj Nimkar"

                    git add kubernetes/frontend.yaml
                    git add kubernetes/backend.yaml

                    git commit -m "Update image tag ${IMAGE_TAG}" || true

                    git push https://\$GIT_USER:\$GIT_PASS@github.com/TanUjNimkar/devsecops-gitops-eks-platform.git HEAD:main
                    """
                }
            }
        }
    }

    post {

        success {
            echo '✅ Pipeline completed successfully'
        }

        unstable {
            echo '⚠️ Pipeline completed with warnings (OWASP/NVD issue)'
        }

        failure {
            echo '❌ Pipeline failed'
        }

        always {
            cleanWs()
        }
    }
}
