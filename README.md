# az_os

![image](https://user-images.githubusercontent.com/49773554/207243902-344f12b0-6d9f-4e7d-9f73-2b5c68ddfec2.png)

![image](https://user-images.githubusercontent.com/49773554/207273674-23af7e54-0b80-477f-8b07-94d4044ccb7c.png)



def call(){
	dir("${env.workspace}')/$(env.SERVICE_PATH)" {
	  sh "version='1.0.0'"
	  sh  "echo ${version}"
	}
}


1
#!/bin/bash
for i in {1..5}
do
   Replace <JENKINS_JOB_NAME> with the actual name of your Jenkins job
   curl -X POST https://<JENKINS_SERVER>/job/<JENKINS_JOB_NAME>/build --user <JENKINS_USERNAME>:<JENKINS_API_TOKEN>
done


Here's how to use the script:

    Replace <JENKINS_JOB_NAME> with the actual name of your Jenkins job.
    Replace <JENKINS_SERVER> with the URL of your Jenkins server.
    Replace <JENKINS_USERNAME> with your Jenkins username.
    Replace <JENKINS_API_TOKEN> with your Jenkins API token. You can find your API token in your Jenkins user profile.

Save the script as a file, e.g. run-jenkins-job.sh, and make it executable by running the following 
command:
chmod +x run-jenkins-job.sh

Then, run the script by running the following command:
dot/run-jenkins-job.sh

2
#!/bin/bash

#Define variables
jenkins_url="http://<jenkins-server>:<port>/"
job_name="<job-name>"
username="<jenkins-username>"
api_token="<jenkins-api-token>"
num_of_runs=5

# Loop through the number of runs and trigger the Jenkins job each time
for i in $(seq 1 $num_of_runs); do
    curl -X POST "${jenkins_url}/job/${job_name}/build" \
    --user "${username}:${api_token}" \
    --header "Jenkins-Crumb:<jenkins-crumb>"
done

Here's how to use the script:

    Replace <jenkins-server> and <port> with the URL and port of your Jenkins server, respectively.
    Replace <job-name> with the name of the Jenkins job that you want to trigger.
    Replace <jenkins-username> with your Jenkins username.
    Replace <jenkins-api-token> with your Jenkins API token. You can find your API token in your Jenkins user profile.
    Replace <jenkins-crumb> with the crumb that Jenkins uses to prevent cross-site request forgery (CSRF) attacks. You can obtain the crumb value by making a GET request to the Jenkins /crumbIssuer/api/xml endpoint. The value will be returned in the crumb field of the response.

Save the script as a file, e.g. run-jenkins-job.sh, and make it executable by running the following command:
chmod +x run-jenkins-job.sh

Then, run the script by running the following command:
./run-jenkins-job.sh

	
	3

#!/bin/bash

# Define variables
jenkins_url="http://<jenkins-server>:<port>/job/<job-name>/buildWithParameters?param1=value1&param2=value2"
num_of_runs=5

# Loop through the number of runs and trigger the Jenkins job each time
for i in $(seq 1 $num_of_runs); do
    curl -X POST "${jenkins_url}"
done


Here's how to use the script:

    Replace <jenkins-server> and <port> with the URL and port of your Jenkins server, respectively.
    Replace <job-name> with the name of the Jenkins job that you want to trigger.
    Replace param1=value1&param2=value2 with the parameters and their values that your Jenkins job expects. If your Jenkins job doesn't expect any parameters, you can remove this part of the URL.
    Replace num_of_runs with the number of times you want to trigger the Jenkins job.

Save the script as a file, e.g. run-jenkins-job.sh, and make it executable by running the following command:
chmod +x run-jenkins-job.sh

Then, run the script by running the following command:
./run-jenkins-job.sh

curl -X POST https://jenkins.example.com/job/MyJob/build --user user:password
java -jar jenkins-cli.jar -s https://jenkins.example.com/ -auth user:password build MyJob
https://jenkins.example.com/job/MyJob/buildWithParameters?param1=value1&param2=value2

