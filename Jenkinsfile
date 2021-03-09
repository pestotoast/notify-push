node {
    try {
        sh 'printenv'
        checkout scm
        def image = docker.build("pestotoast/notify_push", "--no-cache  --pull .")
        image.push()
    }
	catch (ex) {
		mail to: 'jenkins@pestotoast.de',
                subject: "Build error ${currentBuild.fullDisplayName}",
                body: "Build error at ${env.BUILD_URL} after ${currentBuild.durationString}
		error "Build failed."
	}
    finally {
        deleteDir()
    }  
}
