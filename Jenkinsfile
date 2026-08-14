pipeline{
  agent any
  environment{
      SONAR_HOME= tool "sonar"

  }
  stages{
    stage("clone code from GitHub"){
      steps{
        git url:"https://github.com/sushil8744/wanderlust.git" , branch:"devops"
      }
    }
    stage("SonarQube Quality Analysis"){
      steps{
        withSonarQubeEnv("sonar"){
          sh "$SONAR_HOME/bin/sonar-scanner -Dsonar.projectName=wonderlust -Dsonar.projectKey=wanderlust"
        }
      }
    }
    stage("OWASP Dependancy check"){
      steps{
         dependencyCheck additionalArguments: '--scan ./', odcInstallation:'owasp'
         dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
      }
    }
    stage("Sonar Quality gate Scan"){
        steps{
            timeout(time: 5, unit: "MINUTES"){
                waitForQualityGate abortPipeline: false
            }
        }
    }
    stage("Trivy File System Scan"){
      steps{
         sh "trivy fs --format table -o trivy-fs-report.html ."
      }
    }
    stage("Deploy using Docker compose"){
       steps{
        sh "docker compose up -d"
       }
    }
  }

 }