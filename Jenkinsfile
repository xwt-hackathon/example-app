podTemplate(containers: [
    containerTemplate(name: 'hack-agent', image: 'public.ecr.aws/p2j7w3g3/hack-agent:1', command: 'sleep', args: '99d')
  ]) {
      node() {
          stage('test') {
            container('hack-agent') {
                stage('Build a Go project') {
                    sh '''
                    echo "HI"
                    '''
                }
            }
        }
      }
}