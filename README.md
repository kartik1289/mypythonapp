# mypythonapp index.py
from flask import Flask
app = Flask(__name__)
@app.route("/")
def hello():
    return "Hello GITLAB!"
if __name__ == "__main__":
    app.run(host="0.0.0.0", port=int("5000"), debug=True)

#requirments.txt
flask

#docker file Dockerfile
FROM python:alpine3.7
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
EXPOSE 5000
CMD python ./index.py

#GIT LAB and Cloud Run Integration

How to install git lab runner :- https://docs.gitlab.com/runner/install/
Deploy to Cloud Run using GitLab CI :- https://medium.com/google-cloud/deploy-to-cloud-run-using-gitlab-ci-e056685b8eeb
# Download the binary for your system
sudo curl -L --output /usr/local/bin/gitlab-runner https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64

# Give it permissions to execute
sudo chmod +x /usr/local/bin/gitlab-runner

# Create a GitLab CI user
sudo useradd --comment 'GitLab Runner' --create-home gitlab-runner --shell /bin/bash

# Install and run as service
sudo gitlab-runner install --user=gitlab-runner --working-directory=/home/gitlab-runner
sudo gitlab-runner start
sudo gitlab-runner register --url https://gitlab.com/ --registration-token $REGISTRATION_TOKEN
