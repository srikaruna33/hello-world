pipeline{
    agent any
    stages{
        stage("Git Clone"){
            steps{
		    echo("Cloning Git Repo")
            checkout scm: scmGit(branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://github.com/srikaruna33/hello-world.git']])
            }
	    }

	    stage("Maven Build"){
	    	steps{
	    		sh 'mvn clean package'

	    	}
	    }
	    stage("Deploy"){
	    	steps{
	    		//sh 'ansible-playbook kube-dev.yaml'
                echo("Deploying to tomcat")
                sh 'sudo scp /home/ubuntu/hello-world/webapp/target/webapp.war root@172.31.11.95:/var/lib/tomcat9/webapps'

	    	}
	    }
    }
}
