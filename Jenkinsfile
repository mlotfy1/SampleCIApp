//pipeline {
//  agent { label 'Android'}
node('test') {
  stages {
//    stage ("Checkout Git Repo") {
//      steps {
//        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '4250c329-cb83-4d62-ac3c-bd7ac7aef127', url: 'https://github.vodafone.com/Mohamed-Hendy/SampleCIApp.git']]])
//      }
//    }

    stage ("Build clean") {
      steps {
        sh "chmod a+x ./gradlew"
        sh "./gradlew clean --info"
      }
    }
     
    stage ("Build package") {
      steps {
        sh "./gradlew build"
      }
    }
    
    stage ("Sonar Static Analysis") {
      steps {
        sh "./gradlew sonarqube"
         
      }
    }

    stage ("Assemble the APK ") {
      steps {
        sh "./gradlew assembleDebug"
      }
    }

    stage ("App Upload to Nexus") {
      steps {
        sh "./gradlew uploadArchives"
      }
    }
//          
//  stage ("Stage Archive") {
//    steps {
//    tell Jenkins to archive the apks
//    archiveArtifacts artifacts: '**/*.apk', fingerprint: true
//    }
//  }
//  stage("Sign"){
//    steps {
//      signAndroidApks (
//          keyStoreId: "testSign",
//          keyAlias: "key0",
//          apksToSign: "**/*-unsigned.apk",
//      )
//    }
//  }     
          
  }
}
