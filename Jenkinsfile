pipeline{
  agent any
  stages{
  	stage('version-control'){
  		steps{
  			checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkins-build', url: 'https://github.com/Orbit-Etech/jenkins-parallel-job.git']]])
  		}
  	}
    stage('parallel-job'){
      parallel{
        stage('sub-job1'){
          steps{
            sh './jenkins-parallel-job/simpletest.sh'
          }
        }
        stage('sub-job2'){
          steps{
            sh 'lsblk'
          }
        }
        stage('sub-job3'){
            steps{
                sh 'lscpu'
            }
        }
      }
    }
    stage('codebuild'){
    	steps{
    		sh 'cat /etc/passwd'
    	}
    }
  }
}
