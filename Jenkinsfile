node {
  checkout scm
  stage ('Deploy application release'){
    writeFile file: 'extra.json', text: "{'image_tag':'${IMAGE_TAG}','ecs_tasks':[${TASKS}]}"
    withEnv("[VAULT_PASSWORD]=${VAULT_PASSWORD}"){
      sh 'ansible-playboo site.yml --vault-password-file vault.py -e "@extras.json"'
    }
  }
}
