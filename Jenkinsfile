pipeline {
  agent any
  triggers {
    pollSCM("* * * * *")
  }
  environment {
    WEBHOOK_URL = "https://discord.com/api/webhooks/1098211719777624155/vdFOJrTIxHsMmbOr6yjsQQq6gL_ivnO31t3phfeOWIYD_90H-AxZyeMED024sNpGarvE"
  }
  stages {
    stage('Discord message') {
      steps {
        discordSend webhookURL: "${WEBHOOK_URL}" description: "Bonjour depuis Jenkins !"
      }
    }
  }
}
