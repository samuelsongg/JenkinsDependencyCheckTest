pipeline {
    agent any
    tools {
        owaspDependencyCheck 'OWASP Dependency-Check Vulnerabilities'
    }
    stages {
        stage('Checkout SCM') {
            steps {
                git url: 'https://github.com/samuelsongg/JenkinsDependencyCheckTest.git', branch: 'master'
            }
        }
        stage('OWASP DependencyCheck') {
            steps {
                dependencyCheck additionalArguments: '--format HTML --format XML --suppression suppression.xml', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
            }
        }
    }
    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
