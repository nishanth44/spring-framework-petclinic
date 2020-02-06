def label = "mypodtemplate-v1"
podTemplate(label: label, containers: [
        containerTemplate(name: 'maven', image: 'maven:3.3.9-jdk-8-alpine', ttyEnabled: true, command: 'cat')
    ]) {
    node(slave-1) {
        stage('Run maven') {
            container('maven') {
                sh 'mvn --version'
            }
        }
    }
}
