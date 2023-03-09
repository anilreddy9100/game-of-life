pipeline{
    agent { label'node_1' }
    triggers { pollSCM ('H/15 * * * *') }
    stages{
        stage('vcs'){
        steps{
            git branch: 'declaretive', url: 'https://github.com/anilreddy9100/game-of-life.git'
        }
    }
        stage('build'){
        tools{
            jdk 'jdk_8'
        }
        steps{
           sh 'mvn package'
        }
        }
        stage('postbuild'){
            steps{
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
        stage('echo'){
            steps{
                sh 'echo $path'
            }
        }
    }
}