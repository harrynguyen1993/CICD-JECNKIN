pipeline {
   agent any

   stages {
       stage('Clear folder') {
         steps {
            bat '''
                cd C:/Users/Dell/Desktop/
                rmdir /q/s "C:/Users/Dell/Desktop/jenkin"
                echo "Success to locate C"
                mkdir jenkin
            '''
         }
      }
      stage('Create new Folder') {
         steps {
            bat '''
                cd C:/Users/Dell/Desktop/jenkin
                echo "Success to locate C"
            '''
         }
      }
       stage('Clone new git') {
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
   }
}
