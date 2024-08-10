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
            value 'firefox', 'microsoft', 'chrome'
          }
        }
        stages{
          stage('build'){
            steps{
              echo "Build ... pour ${PLATEFORM} - ${BROWSER}"
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