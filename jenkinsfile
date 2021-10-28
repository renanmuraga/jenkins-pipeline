pipeline  {
      agent any 
       stages {
       
       	stage('Cleanup') {
		steps {
		deleteDir()
		}
	}
	 
	    stage ('Distro Info') {
            steps {
                sh 'echo "Informacoes da Distro utilizada $(hostname -i):" >> assessment.txt'
				sh 'cat /etc/*-release >> assessment.txt'
            }
        }
		
		stage ('Kernal Info') {
            steps {
                sh 'echo "Informacoes do Kernel do Servidor $(hostname -i):" >> assessment.txt'
				sh 'uname -a >> assessment.txt'	
            }
        }
		
		        stage ('User Info') {
            steps {
                sh 'echo "Lista de Usuarios Presente no Servidor $(hostname -i):" >> assessment.txt'
				sh 'cat /etc/passwd | cut -d: -f1 >> assessment.txt'
            }
        }
        stage ('Packages Info') {
            steps {
                sh 'echo "Pacotes instalados no Servidor $(hostname -i):" >> assessment.txt'
				sh 'dpkg -l >> assessment.txt'
            }
        }

        
    }
    
    post {
        always { echo "Compilação finalizada"}
        success { echo "Sucesso"}
        failure { echo "Falha !!!"}
    }
}
