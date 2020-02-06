pipeline {
  agent {
    kubernetes {
      label 'slave-1'
      defaultContainer 'jnlp'
      yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: some-label-value
spec:
  containers:
  - name: maven
    image: maven:3.3.9-jdk-8-alpine
    command:
    - cat
    tty: true
"""
    }
  }
  stages {
    stage('Run maven') {
      steps {
        container('maven') {
          sh 'mvn -version'
        }
      }
    }
  }
}
Scripted pipeline
def label = "mypodtemplate-v1"
podTemplate(label: label, containers: [
        containerTemplate(name: 'maven', image: 'maven:3.3.9-jdk-8-alpine', ttyEnabled: true, command: 'cat')
    ]) {
    node(label) {
        stage('Run maven') {
            container('maven') {
                sh 'mvn --version'
            }
        }
    }
}
