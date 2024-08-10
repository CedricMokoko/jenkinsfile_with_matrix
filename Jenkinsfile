pipeline{
  agent any

  // options{
    // parallelAlwaysFailFast()
  // }

  stages{
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
              sh 'echo "Build ... pour ${PLATEFORM} - ${BROWSER}" > my_first_artefact.txt'
              archiveArtifacts(artifacts: '*.txt')
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