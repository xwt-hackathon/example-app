podTemplate(containers: [
    containerTemplate(name: 'golang', image: 'golang:1.16.5', command: 'sleep', args: '99d')]) {
      node() {
          stage('test') {
            container('kaniko') {
                stage('Say Hi') {
                    sh'echo "Hello World!"'
            }
        }
      }
    }
}