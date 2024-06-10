pipeline {
    agent any
    parameters {         
        string(name: 'wzrost', description: 'Wzrost w centymetrach', defaultValue: '')        
        string(name: 'waga', description: 'Waga w kilogramach', defaultValue: '')
    }
    stages {         
        stage('Calculate BMI') {             
            steps {                 
                script {                     
                    def BMI = params.waga / ((params.wzrost/100)*(params.wzrost/100))
                    echo "Twój wskaźnik BMI to: $BMI"                                                                                    
                    }                 
                }             
            }         
        }     
    post {
        failure {
            emailext body: "Wystąpił błąd podczas wykonywania pipelinu",                                  
                    subject: "BŁĄD",                                  
                    to: "kapidospamu@gmail.com"
        }
    }
}
