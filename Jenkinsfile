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
                    def BMI = wzrost && waga ?                               (Double.parseDouble(waga) /                                ((Double.parseDouble(wzrost) / 100) * (Double.parseDouble(wzrost) / 100))) :                               null                     echo BMI != null ? "Twój wskaźnik BMI to: $BMI" : "Proszę podać wzrost i wagę jako argumenty."                                          // Wysyłanie emaila z wynikiem BMI, jeśli BMI nie jest null                     if (BMI != null) {                                                  emailext body: "Twój wskaźnik BMI to: $BMI",                                                                     subject: "Wynik BMI",                                                                     to: "k.kapitula.063@studms.ug.edu.pl"                                          }                 }                          }                  }          }      }
