pipeline{
 agent{ label 'master'
      }
 tools { maven 'maven' 
       }

  
 stage( 'Build'){ 
 steps { sh 'mvn clean package' }
  parameters{ booleanParam (
            defaultValue: true,
            description: 'boolean parameter',
           name: 'FIRSTPARAMETER')}}

  stage('sonar-scan') {
  steps { sh 'mvn install sonar:sonar -D sonar.login=admin -D sonar.password=1234 -Dsonar.url=http://35.199.14.26:8081' }
 parameters{ booleanParam (
            defaultValue: true,
            description: 'boolean parameter',
             name: 'FIRSTPARAMETER')}}

  stage('compile'){
  steps { sh 'mvn clean compile'}
   parameters{booleanParam (
            defaultValue: true,
            description: 'third parameter desc',
            name: 'THIRDPARAMETER')}}
       }
        }
