
/*node {
    // Get Artifactory server instance, defined in the Artifactory Plugin administration page.
    def server = Artifactory.server "artifactory"
    // Create an Artifactory Maven instance.
    def rtMaven = Artifactory.newMavenBuild()
    def buildInfo
    
 rtMaven.tool = "maven"

    stage('Clone sources') {
        git url: 'https://github.com/manishrajani/WebApp.git'
    }

    stage('Artifactory configuration') {
        // Tool name from Jenkins configuration
        rtMaven.tool = "maven"
        // Set Artifactory repositories for dependencies resolution and artifacts deployment.
        rtMaven.deployer releaseRepo:'libs-release-local', snapshotRepo:'libs-snapshot-local', server: server
        rtMaven.resolver releaseRepo:'libs-release', snapshotRepo:'libs-snapshot', server: server
    }

    stage('Maven build') {
        buildInfo = rtMaven.run pom: 'pom.xml', goals: 'clean install'
    }

    stage('Publish build info') {
        server.publishBuildInfo buildInfo
    }
    }
	
	
	
	*/
pipeline {				//indicate the job is written in Declarative Pipeline 
	agent any
    stages {
        stage ("Compile Web App") 
        {		//an arbitrary stage name
            steps 
            {
                build 'compile-web-app'	//this is where we specify which job to invoke.
            }
            
        }
        stage ("Deploy To QA") 
        {		//an arbitrary stage name
        steps 
            {
                build 'deploytoqa'	//this is where we specify which job to invoke.
            }
        }
        stage ("Upload Artifacts to Artifactory") 
        {       //an arbitrary stage name
        steps 
            {
                build 'artifactory-deployment'  //this is where we specify which job to invoke.
            }
        }
        stage ("Functional Testing") 
        {		//an arbitrary stage name
        steps 
            {
                build 'functional-testing'	//this is where we specify which job to invoke.
            }
        }
        stage ("Performance Testing") 
        {		//an arbitrary stage name
        steps 
            {
                build 'Performance-testing'	//this is where we specify which job to invoke.
            }
        }
        stage ("Deployment to Production") 
        {		//an arbitrary stage name
        steps 
            {
                build  'deploy-to-prod'	//this is where we specify which job to invoke.
            }
        }
        stage ("Production Sanity Testing") 
        {		//an arbitrary stage name
        steps 
            {
                build  'Sanity-test-on-production'	//this is where we specify which job to invoke.
            }
        }
    }
}
