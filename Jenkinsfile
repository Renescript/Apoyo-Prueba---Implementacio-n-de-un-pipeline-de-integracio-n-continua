pipeline { 
    agent any 
    environment { 
        NODE_VERSION = '18.16'
    } 
 
    stages { 
        stage('Clonar Repositorio') {
            steps {
                echo "** Clonando repositorio"
               // git 'https://github.com/Renescript/Apoyo-Prueba---Implementacio-n-de-un-pipeline-de-integracio-n-continua.git'
                checkout scm
            }

        }
 
        stage('Dependencias') { 
            steps { 
                script { 
                    try { 
                        echo "⚙️ Instalando dependencias..." 
                        sh 'npm install' 
                    } catch (Exception e) { 
                        error("❌ Error en la etapa de dependencias") 
                    } 
                } 
            } 
        } 
 
        stage('Test') { 
            steps { 
                script { 
                    try { 
                        echo "🧪 Ejecutando pruebas..." 
                        sh 'npm test' 
                    } catch (Exception e) { 
                        error("❌ Error en la etapa de Test") 
                    } 
                } 
            } 
        } 

        stage('Docker') {
            steps {
                script {
                    // Stop any existing containers with the same name
                    sh 'docker ps -q --filter name=desafio_jenkins | xargs -r docker stop'
                    sh 'docker ps -aq --filter name=desafio_jenkins | xargs -r docker rm'
                    
                    // Build and run with new container name
                    sh "docker build -t desafio_jenkins ."
                    sh "docker run -d --name desafio_jenkins_instance -p 3000:3000 desafio_jenkins"
                }
            }
        }
    } 
 
    post { 
        success { 
            echo "✅ Pipeline completado con éxito" 
        } 
        failure { 
            echo "❌ El pipeline ha fallado" 
        } 
    } 
}
