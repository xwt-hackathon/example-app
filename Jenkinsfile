podTemplate(containers: [
    containerTemplate(name: 'kaniko', image: 'gcr.io/kaniko-project/executor:latest', command: '/busybox/cat')],
    volumes:[secretVolume( mountPath:"/root/.aws", secretName: "aws-secret")]) {
      node() {
          stage('test') {
            container('kaniko') {
                stage('Say Hi') {
                    sh 'echo "Hello World!"'
            }
        }
      }
}