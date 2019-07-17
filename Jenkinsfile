pipeline{
 agent{ label 'master'
      }
 tools { maven 'maven' 
       }
  parameters{ 
            booleanParam (
            defaultValue: true,
            description: 'boolean parameter',
            name: 'BUILD' )
               booleanParam (
            defaultValue: true,
            description: 'boolean parameter',
             name: 'SONAR' )
             
             booleanParam (
            defaultValue: true,
            description: 'third parameter desc',
            name: 'COMPILE' )
            }
 
 stages{
  
 stage( 'Build'){
  when { 
   expression { params.BUILD }
       } 
 steps { sh 'mvn clean package' 
        }
 }

  stage('sonar-scan') {
   when {
           expression { params.SONAR } 
        } 
   
  steps { sh 'mvn install sonar:sonar -D sonar.login=admin -D sonar.password=admin -Dsonar.url=http://35.199.14.26:9000' 
        }
 }

  stage('compile'){
   
    when {
           expression { params.COMPILE } 
          } 
  steps { sh 'mvn clean compile'
       }
   
         }
       }
        }
