GROUP PROJECT MEMBERS:
1.	Ajay Kumar Addike (G01398832)
2.	Rohith Tangudu (G01409971)
3.	Arun Chakravarthy Annadata (G01409888)
4.	Venkata Ravi Sridhar Devarakonda (G01449062)
5.	Harshitha Maguluri (G01423354)

********************************************************************************************************
PROJECT MEMBERS CONTRIBUTION:

a)Jenkinsfile and pipeline Implementation:Ajay Kumar, Rohith Tangudu
b)Rancher Cluster creation and creating Deployment:Ajay Kumar,Rohith Tangudu,Arun Chakravarthy
c)Dockerfile creation and Implementation:Venkata Ravi Sridhar,Harshitha Maguluri
d)Video Demonstration:Ajay Kumar, Rohith Tangudu
e)Documentation and screenshots: Venkata Ravi Sridhar, Arun Chakravarthy
f)Github url and repository setup: Ajay Kumar


********************************************************************************************************
PROJECT SUBMISSION ZIP FILE FOLDER STRUCTURE:

The zip file contains the following:
	a)videos folder-contains the video demonstrations of installation and demo of the CI-CD project
	b)Rancher files folder-contains following:
		i)survey.yaml-kubeConfig file of the deployment named survey
		ii)k8s.yaml-kubeConfig file of the cluster named k8s
		iii)survey-lb.yaml-KubeConfig file of the deployment as LoadBalancer as a service called survey-lb
	c)Installation-Guide:Contains instructions and screenshots for all the steps
	d)Assign1Part2.war-Contains war file of the Java based Dynamic Web Application
	e)SWE-645-part2 folder-Contains the whole application containing source code including Dockerfile and Jenkinsfile(This code is already posted on github repo 	https://github.com/Ajay-Addike/SWE645HW2)


*********************************************************************************************************
Links:
1) Github repository Link-https://github.com/Ajay-Addike/SWE645HW2
   Description: This is my public github repository link which is used to integrate with Jenkins.

2) Both demo videos (Installation and working demo) were created using teams meeting.
	Link: https://gmuedu-my.sharepoint.com/personal/aaddike_gmu_edu/_layouts/15/stream.aspx?id=%2Fpersonal%2Faaddike%5Fgmu%5Fedu%2FDocuments%2FRecordings%2FCall%20with%20Rohith%20Tangudu%2D20240320%5F211507%2DMeeting%20Recording%2Emp4&ga=1&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview

3) Rancher URLS(Links might not be accessible due to learner lab. These urls are just for reference and proof of implementation)
	a)Deploymentone- https://ec2-18-233-14-73.compute-1.amazonaws.com/k8s/clusters/c-m-xnwhb6hl/api/v1/namespaces/default/services/http:survey:8080/proxy/Assign1Part2/
    
	b)Deploymentone-lb= https://ec2-18-233-14-73.compute-1.amazonaws.com/k8s/clusters/c-m-xnwhb6hl/api/v1/namespaces/default/services/http:survey-lb:8080/proxy/Assign1Part2/

4) Dockerhub url-https://hub.docker.com/repository/docker/venkataravisridhardevarakonda/survey/tags?page=1&ordering=last_updated

5) We used two Ec2 Instances one for Jenkins and the other for Rancher 
	a)For opening Rancher on this instance:https://ec2-18-233-14-73.compute-1.amazonaws.com/dashboard/home
    
	b)For opening Jenkins on this instance:http://52.44.31.224:8080


***********************************************************************************************************
MISCELLANEOUS DETAILS:
1) I have placed the Dockerfile and Jenkinsfile in the root directory of my GitHub repository.

2) The Docker image initially utilized for creating the application was `venkataravisridhardevarakonda/survey:latest`.

3) EC2 instances have been established with inbound rules enabled for ports 8080, 22, 443, and 80, and the security group is set to `vockey` (default option in learner labs).

4) The Rancher clusters were created using the Custom cluster method.