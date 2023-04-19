pipeline {
  agent any
  triggers {
    pollSCM("* * * * *")
  }
  environment {
    WEBHOOK_URL = "https://discord.com/api/webhooks/1098211719777624155/vdFOJrTIxHsMmbOr6yjsQQq6gL_ivnO31t3phfeOWIYD_90H-AxZyeMED024sNpGarvE"
    WEBHOOK_URL_MULESOFT_SERV = "https://discord.com/api/webhooks/1098218163516215357/3VsoUEipTMtldBX1IG0ydv48SGrqyKx93Dr4itdvlO1K1vzesP46STJmBAwmVf6SiT0b"
  }
  stages {
    stage('Discord message') {
      steps {
        discordSend webhookURL: "${WEBHOOK_URL_MULESOFT_SERV}",
                    result: currentBuild.currentResult,
                    customUsername: "Custom username test",
                    description: "Bonjour depuis Jenkins @everyone !" 
      }
    }
    stage('Discord build message') {
      steps{
        discordSend webhookURL: WEBHOOK_URL,
            title: "${env.JOB_BASE_NAME} #${env.BUILD_NUMBER}",
            result: currentBuild.currentResult,
            description: "**Build:** ${env.BUILD_NUMBER}\n**Status:** ${currentBuild.currentResult}\n\u2060", /* word joiner character forces a blank line */
            enableArtifactsList: true,
            showChangeset: true
      }
    }
  }
}
