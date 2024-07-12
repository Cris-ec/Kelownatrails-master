pipeline{
    agent any
    environment {
    FIREBASE_DEPLOY_TOKEN = credentials('firebase-token')
    //TOKENAWS = credentials('ssh-production-key')
    }

 stages{
        stage('Building'){
            steps{
           // sh 'npm install -g firebase-tools'
                echo 'Biulding...'
            }
        } 
        stage('Testing Environment'){
            steps{
            sh 'firebase deploy -P testing-enviroment-e4934 --token "$FIREBASE_DEPLOY_TOKEN"'
            input message: 'After testing. Do you want to continue with Staging Environment? (Click "Proceed" to continue)'
            //sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@54.209.10.245 " sudo dnf update; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo rm -Rf /var/www/html/; sudo git clone https://github.com/Cris-ec/Kelownatrails-master.git /var/www/html"'
            }
        } 
        stage('Staging Environment'){
            steps{
             sh 'firebase deploy -P staging-environment-aefd9 --token "$FIREBASE_DEPLOY_TOKEN"'
             //sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@18.234.72.147 " sudo dnf update; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo rm -Rf /var/www/html/; sudo git clone https://github.com/Cris-ec/Kelownatrails-master.git /var/www/html"'
            }
        } 
        stage('Production Environment'){
            steps{
            sh 'firebase deploy -P production-3c1cf --token "$FIREBASE_DEPLOY_TOKEN"'
            //sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@54.159.194.49 " sudo dnf update; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo rm -Rf /var/www/html/; sudo git clone https://github.com/Cris-ec/Kelownatrails-master.git /var/www/html"'
            }
        } 
    }

}
