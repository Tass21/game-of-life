#!/usr/bin/env groovy

/* Only keep the 10 most recent builds. */
def projectProperties = [
    [$class: 'BuildDiscarderProperty',strategy: [$class: 'LogRotator', numToKeepStr: '5']],
]
def imageName = 'jenkinsciinfra/jenkinsio'

if (!env.CHANGE_ID) {
    if (env.BRANCH_NAME == null) {
        projectProperties.add(pipelineTriggers([cron('H/30 * * * *'), pollSCM('H/5 * * * *')]))
        projectProperties.add(disableConcurrentBuilds())
    }
}

properties(projectProperties)

node{


	stage ('Checkout source'){
       checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'BitbucketCredentials', url: 'https://github.com/Tass21/game-of-life.git']]])
	}

	stage ('Test'){
	  echo 'Testing ... '
	}

	stage ('Deploy'){
	  echo 'Deploying ... '
	}

}