pipeline {
    agent any
    parameters {         
        string(name: 'wzrost', description: 'Wzrost w centymetrach', defaultValue: '')        
        string(name: 'waga', description: 'Waga w kilogramach', defaultValue: '')
    }
        tools {
        jdk 'Java'
    }
    environment {
        JAVA_HOME = tool 'Java'
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
                        // Wysyłanie emaila z wynikiem BMI                         
                        emailext body: "Twój wskaźnik BMI to: $BMI",                                  
                                  subject: "Wynik BMI",                                  
                                  to: "k.kapitula.063@studms.ug.edu.pl"                     
                    } else {                         
                        echo "Proszę podać wzrost i wagę jako argumenty."                     
                    }                 
                }             
            }         
        }     
    }     
}
