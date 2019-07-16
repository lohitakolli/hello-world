pipeline{
 agent{ label 'master'
      }
 tools { maven 'maven' 
       }
  parameters{ 
            booleanParam (
            defaultValue: true,
            description: 'boolean parameter',
           name: 'FIRSTPARAMETER' )
               booleanParam (
            defaultValue: true,
            description: 'boolean parameter',
             name: 'SECONDPARAMETER' )
             
             booleanParam (
            defaultValue: true,
            description: 'third parameter desc',
            name: 'THIRDPARAMETER' )
            }
 
 stages{
  
 stage( 'Build'){ 
 steps { sh 'mvn clean package' 
        echo "trying: ${params.FIRSTPARAMETER}" }
 }

  stage('sonar-scan') {
  steps { sh 'mvn install sonar:sonar -D sonar.login=admin -D sonar.password=1234 -Dsonar.url=http://35.199.14.26:8081' 
        echo "trying: ${params.SECONDPARAMETER}"}
 }

  stage('compile'){
  steps { sh 'mvn clean compile'
        echo "trying: ${params.THIRDPARAMETER}"}
   
         }
       }
        }
