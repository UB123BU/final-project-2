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
                    def wzrost = params.wzrost ?: ''
                    def waga = params.waga ?: ''
                    def BMI = wzrost && waga ? 
                              (Double.parseDouble(waga) / 
                               ((Double.parseDouble(wzrost) / 100) * (Double.parseDouble(wzrost) / 100))) : 
                              null
 
                    if (BMI != null) {                         
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
