node {
  // Mark the code checkout 'stage'....
  stage 'Stage Checkout'

  // Checkout code from repository and update any submodules
  checkout scm
  sh 'git submodule update --init'

  stage 'Stage Build'

  //branch name from Jenkins environment variables
  echo "Build branch: ${env.BRANCH_NAME}"

  //build your gradle flavor, passes the current build number as a parameter to gradle
  sh "./gradlew clean assemble"

  stage 'Stage Archive'
  //tell Jenkins to archive the apks
  archiveArtifacts artifacts: 'app/build/outputs/apk/*.apk', fingerprint: true
}