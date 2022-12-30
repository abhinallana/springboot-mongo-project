node{
     
    stage('SCM Checkout'){
        git credentialsId: 'GIT_CREDENTIALS', url:  'https://github.com/MithunTechnologiesDevOps/spring-boot-mongo-docker.git',branch: 'master'
    }
    
    stage(" Maven Clean Package"){
      def mavenHome =  tool name: "Maven-3.6.1", type: "maven"
      def mavenCMD = "${mavenHome}/bin/mvn"
      sh "${mavenCMD} clean package"
      
    } 
    
    
    stage('Build Docker Image'){
        sh 'docker build -t abhinallana/spring-boot-mongo .'
    }
    
    stage('Push Docker Image'){
        withDockerRegistry([ credentialsId: "dockercreds", url: "" ]) {
            sh 'docker push dockerhandson/spring-boot-mongo'
            echo "pushed Success"
          } 
        
     }
     
    //  stage("Deploy To Kubernetes Cluster"){
    //    kubernetesDeploy(
    //      configs: 'springBootMongo.yml', 
    //      kubeconfigId: 'KUBERNATES_CONFIG',
    //      enableConfigSubstitution: true
    //     )
    //  }
	 
	  /**
      stage("Deploy To Kuberates Cluster"){
        sh 'kubectl apply -f springBootMongo.yml'
      } **/
     
}


