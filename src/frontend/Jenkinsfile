#!/usr/bin/env groovy

@Library('deployhub') _

def app="ChiliUptimeApp"
def environment=""
def cmd=""
def url="https://console.deployhub.com"
def user="stella99"
def pw="1234"

def dh = new deployhub();

node {
	
    stage('Clone sources') {
        git url: 'https://github.com/ortelius/microservices-demo.git'
    }
    
    stage ('Testing') {
   
def comp="GLOBAL.Chasing Horses LLC.Vintage LLC.Hipster Store.Front End.frontend"
def version = "0.1.0"
def imagename = "frontend"

echo "${url}";
echo "${version}";

// create component version
// def newComponentVersion(String url, String userid, String pw, String compname, String compvariant, String compversion)
data = dh.newComponentVersion(url, user, pw, comp, "", version);
echo "Creation Done " + data.toString();

// // update attrs
def attrs = [
	     BuildId: env.BUILD_ID,
	     BuildUrl: env.BUILD_URL,
             Chart: "harbor-lib/"+imagename, 
	     chartversion: version,
	     operator: "Kubernetes operator",
	     DockerBuildDate: "timestamp",
	     DockerSha: "sha for the docker image",
	     DockerRepo: "url for the docker registry",
	     GitCommit: "git commit",
	     GitRepo: "git repo",
	     GitTag: "git tag",
	     GitUrl: "git url",
	     buildnumber: env.BUILD_ID, 
	     buildjob: "GLOBAL.test-project",
	     ComponentType: "Application File",
	     ChangeRequestDS: "GLOBAL.JiraUnisys",
	     Category: "General",
	     AlwaysDeploy: "N",
	     DeploySequentially: "N",
	     BaseDirectory: "tmp",
	     PreAction: "",
	     PostAction: "",
	     CustomAction: "GLOBAL.HelmChart",
	     Summary: "Pipeline Comp"
	    ];
echo "${attrs}";
// // def updateComponentAttrs(String url, String userid, String pw, String compname, String compvariant, String compversion, Map Attrs)
data = dh.updateComponentAttrs(url, user, pw, comp, "", version , attrs);
echo "Update Done " + data.toString();
	    
    }  
}
