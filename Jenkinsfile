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
              script{
                  try {
               isApproved = input(
                    id: 'someId',
                    message: 'Approve?',
                    submitter: 'someuser', // <== 'does not query Keycloak; ignores this 
                     parameters: [choice(
                            choices: ['No', 'Yes'],
                            description: 'some description',
                            name: 'some name')]
                        ) == 'Yes'
                  }
                  catch(exp)
                  {
                      bat 'echo "Error when confirm"'
                  }
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
