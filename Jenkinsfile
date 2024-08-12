pipeline{
  agent any

  // options{
    // parallelAlwaysFailFast()
  // }

  tools{
    gradle 'gradle8.10'   // 'gradle8.10' est le nom qu'on a donné au tool sur jenkins interface
    nodejs 'nodejs22.6.0'
  }

  stages{
    stage('tools'){
      steps{
        sh 'gradle -v'
        sh 'node -v'
      }
    }
    stage('application build and test'){
      matrix{
        axes{
          axis{
            name 'PLATEFORM'
            values 'linux', 'macos', 'windows'
          }
          axis{
            name'BROWSER'
            values 'firefox', 'microsoft', 'chrome'
          }
        }
        stages{
          stage('build'){
            steps{
              sh 'echo "Build ... pour ${PLATEFORM} - ${BROWSER}" > my_first_artefact.txt' //Ici on crée un file
              archiveArtifacts(artifacts: '*.txt') //Ici on récupère le etoile point txt au premier niveau
            }
          }
          stage('test'){
            steps{
              echo "Test... pour ${PLATEFORM} - ${BROWSER}"
            }
          }
        }       
      }
    }

    stage('deployment'){
      steps{
        echo "Deploy application ..."
      }
    }

  }
}