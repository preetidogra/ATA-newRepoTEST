pipeline{

	agent any
	stages{
	stage('Checkout code') {
        	steps {
		// Get some code from a GitHub repository
    	checkout([$class: 'GitSCM',
        branches: [[name: '*/main']],
        extensions: [[$class: 'CloneOption', timeout: 120]],
        gitTool: 'Default', 
        userRemoteConfigs: [[url: 'https://github.com/preetidogra/ATA-newRepoTEST']]
    ])
           	checkout scm
        }
    }
	stage("Compile stage"){
		steps{
		// Get some code from a GitHub repository
    		checkout([$class: 'GitSCM',
       		branches: [[name: '*/main']],
        	extensions: [[$class: 'CloneOption', timeout: 120]],
        	gitTool: 'Default', 
        	userRemoteConfigs: [[url: 'https://github.com/preetidogra/ATA-newRepoTEST']]
    		])
		withMaven(maven: 'maven_3_8_4') {
                    sh 'mvn clean install'
		 }}}
			  
	stage("Test stage"){
		steps{
			// Get some code from a GitHub repository
    		checkout([$class: 'GitSCM',
        	branches: [[name: '*/main']],
       		extensions: [[$class: 'CloneOption', timeout: 120]],
        	gitTool: 'Default', 
        	userRemoteConfigs: [[url: 'https://github.com/preetidogra/ATA-newRepoTEST']]
   		 ])
		withMaven(maven: 'maven_3_8_4'){
		sh'mvn test'}}}
			  
	stage("Cucumber Report"){
		steps{
			// Get some code from a GitHub repository
    		checkout([$class: 'GitSCM',
        	branches: [[name: '*/main']],
        	extensions: [[$class: 'CloneOption', timeout: 120]],
        	gitTool: 'Default', 
        	userRemoteConfigs: [[url: 'https://github.com/preetidogra/ATA-newRepoTEST']]
			 ]) 
		cucumber buildStatus: "UNSTABLE",
		fileIncludePattern: "**/cucumber.json",
                jsonReportDirectory: 'target'}}

}

}
