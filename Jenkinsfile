podTemplate(containers: [
    containerTemplate(name: 'kaniko', image: 'gcr.io/kaniko-project/executor:latest', volume:[secretVolume( mountPath:"/root/.aws", secretName: "aws-secret")] command: '/busybox/cat')
  ]) {
      node() {
          stage('test') {
            container('kaniko', shell: '/busybox/sh') {
                stage('Build a Kaniko image') {
                    environment {
                        DOCKERFILE  = "Dockerfile"
                        GITREPO     = "git://github.com/xwt-hackathon/example-app.git"
                        CONTEXT     = "/workspace"
                        REGISTRY    = '404458385382.dkr.ecr.us-west-2.amazonaws.com/kaniko-test'
                        IMAGE       = 'kaniko-test'
                        TAG         = 'latest'
                    }
                    sh '''#!/busybox/sh
                    /kaniko/executor \\
                    --context=\${GITREPO} \\
                    --dockerfile=\${DOCKERFILE} \\
                    --destination=\${REGISTRY}/\${IMAGE}:\${TAG}
                    '''
                }
            }
        }
      }
}