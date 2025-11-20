# Jenkins Setup Instructions from Scratch

BEFORE STARTING PLEASE SWITCH TO AIRD

## 1. Run Jenkins Container
```
docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts

```

## 2. Access Jenkins UI
Open browser:
```
http://localhost:8080

```

## 3. Initial Jenkins Setup
Copy admin password from:
```
/var/jenkins_home/secrets/initialAdminPassword OR COPY AND PASTE FROM THE TERMINAL

```

## 4. Create GitHub Repository
Push files:

- Jenkinsfile
- train.py
- predict.py
- model.py
- requirements.txt

## 5. Install python and pip in the jenkins image of docker (only needed the first time)

-docker ps
- (search for the name of the image)
- docker exec -u root -it (friendly_lederberg) bash (replace that freindly thing with your image name)
- apt-get update 
- apt-get install -y python3 python3-venv python3-pip
- python3 --version 
- exit

## 6. Configure Jenkins Job
- Create Pipeline job
- Select "Pipeline from SCM"
- Provide GitHub repo link
- Change */master to */main
- Run the job

## 7. Retrieve Artifacts
Artifacts saved inside Jenkins:
```
Workspace → artifacts/
tiny_char_rnn.pt
meta.json

download these files push these into git repo under a new folder called artifacts 

so it should look something like this 
-artifacts
    -tiny_char_rnn.pt
    -meta.json
-model.py
-train.py
-requirements.txt
-predict.py
```

## 8. Run Prediction Locally
```
cd into the git folder
python3 predict.py

```

after doing this once try changing the model run a more complex model with a different dataset and run the pipeline again
