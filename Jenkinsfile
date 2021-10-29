node {

    stage('Clone du projet ') {
        // get depot with credentials
        git branch: 'main', credentialsId: 'a995d9c5-a16f-4f87-8c33-7b40e16f9f20' , url: 'git@github.com:MGNetworking/ghoverblog_Documentation-.git'
    }
    
    stage('Récupération de l\'environement Python ') {
        // recupération de l'environement Python a partir du fichier requirements.txt
        sh '''  pip install -r requirements.txt '''
     }

    stage('Build to documentation ') {
        // Compilation du projet dans le repertoire de jnekins
        sh '''  .\make.bat html '''
     }

    stage('Suppression de l\'ancienne version ') {
        // supression de la version précedante 
        sh '''rm -r /home/prod/www/*'''
    }

    stage('Déplacement du build vers répertoir d\'accueil ' ) {
        //  déplacement du build vers le fichier html
        sh '''cp -r /var/lib/jenkins/workspace/Documentation-ghoverblog/_build/html/* /home/prod/doc-ghoverblog/'''
    }

}