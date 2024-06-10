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
                    def BMI
                    def wzrost = params.wzrost ?: ''
                    def waga = params.waga ?: ''
                    if (wzrost && waga) {                         
                        double wzrostValue = Double.parseDouble(wzrost)                         
                        double wagaValue = Double.parseDouble(waga)                         
                        BMI = wagaValue / ((wzrostValue / 100) * (wzrostValue / 100))                         
                        echo "Twój wskaźnik BMI to: $BMI"                                                                  
                    } else {                         
                        echo "Proszę podać wzrost i wagę jako argumenty."                     
                    }                 
                }             
            }         
        }     
    }
    post {
        failure {
            emailext body: "Wystąpił błąd podczas wykonywania pipelinu",                                  
                    subject: "BŁĄD",                                  
                    to: "k.kapitula.063@studms.ug.edu.pl"
        }
    }
}
