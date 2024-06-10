pipeline {
  agent any
    parameters {         
    string(name: 'wzrost', description: 'Wzrost w centymetrach', defaultValue: '')        
    string(name: 'waga', description: 'Waga (w kilogramach)', defaultValue: '')
    }
  stages {         
    stage('Calculate BMI') {             
      steps {                 
        script {                     
          def BMI                     
          if (params.wzrost && params.waga) {                         
            double wzrost = Double.parseDouble(params.wzrost)                         
            double waga = Double.parseDouble(params.waga)                         
            BMI = waga / ((wzrost / 100) * (wzrost / 100))                         
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
