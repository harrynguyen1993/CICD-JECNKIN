pipeline {
    environment {
        SERVER = "luan.nguy"
    }
   agent any
   
   stages {
       stage('Clear folder') {
          parallel {
              stage('Clear folder 1') {
                    steps {
                    bat '''
                        cd C:/Users/Dell/Desktop/
                        rmdir /q/s "C:/Users/Dell/Desktop/jenkin"
                        echo "Success to locate jenkin"
                        mkdir jenkin
                    '''
                }
              }
              stage('Clear folder 2') {
                    steps {
                        bat '''
                        cd C:/Users/Dell/Desktop/
                        rmdir /q/s "C:/Users/Dell/Desktop/jenkin2"
                        echo "Success to locate jenkin2"
                        mkdir jenkin2
                    '''
                }
              }
          }
      }
        stage ('Deploy To Prod'){
             steps {
                script {
                    def deploymentDelay = input id: 'Deploy', message: 'Deploy to production?', submitter: 'rkivisto,admin', parameters: [choice(choices: ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18', '19', '20', '21', '22', '23', '24'], description: 'Hours to delay deployment?', name: 'deploymentDelay')]
                    sleep time: deploymentDelay.toInteger(), unit: 'HOURS'
                }
            }
        }
      stage('Create new Folders') {
         parallel {
             stage('new Folders 1') {
                steps {
                    bat '''
                        cd C:/Users/Dell/Desktop/jenkin
                        echo "Success to locate jenkin"
                    '''
                }
             }
            stage('new Folders 2') {
                steps {
                bat '''
                    cd C:/Users/Dell/Desktop/jenkin2
                    echo "Success to locate jenkin2"
                '''
                }  
            }
         }
      }
       stage('Clone new git') {
         parallel {
            stage('Clone new git 1') {
                steps {
                    bat '''
                    cd C:/Users/Dell/Desktop/jenkin
                    git clone https://github.com/harrynguyen1993/vieon-androidtv.git
                    cd vieon-androidtv
                    git pull 
                    git checkout develop
                    '''
                }
            }
            stage('Clone new git 2') {
                    steps {
                        bat '''
                        cd C:/Users/Dell/Desktop/jenkin2
                        git clone https://github.com/harrynguyen1993/vieon-androidtv.git
                        cd vieon-androidtv
                        git pull 
                        git checkout develop
                    '''
                }
             }
         }
      }
      stage ('Done progress'){
        steps
            {
                bat '''
                echo "Done"
                '''
            }
        }
   }
      post {
            always {
                echo 'I will always say Hello again!'

               emailext body: "${SERVER} ${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
                    recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
                    subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
                   }
     }
}
