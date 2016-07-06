node('master') {
    
   // Mark the code checkout 'stage'....
   stage 'Checkout'

   // Get the code from the Stash repository
   checkout scm

   // Mark the code build 'stage'....
   stage 'Build'
   
   // Make sure script is runnable
   sh "chmod a+x ./gradlew"
   
   // Run gradle build and deploy
   wrap([$class: 'ConfigFileBuildWrapper', managedFiles: [[fileId: 'org.jenkinsci.plugins.configfiles.custom.CustomConfig1453803770046', replaceTokens: false, targetLocation: 'gradle.properties', variable: '']]]) {
    sh "./gradlew snapshot generateHtml5 --stacktrace"
   }
   
   publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'build/asciidoc/html5', reportFiles: 'semantic-versioning.html', reportName: 'Documentation'])

}