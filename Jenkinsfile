podTemplate(containers: [
    containerTemplate(name: 'kaniko', image: 'gcr.io/kaniko-project/executor:latest', command: '/busybox/cat')],
    volumes:[secretVolume( mountPath:"/root/.aws", secretName: "aws-secret")]) {
      node() {
          stage('test') {
            container('kaniko') {
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
                    --context=`pwd` \\
                    --dockerfile=\${DOCKERFILE} \\
                    --destination=\${REGISTRY}/\${IMAGE}:\${TAG} \\
                    --verbosity
                    '''
                }
            }
        }
      }
}