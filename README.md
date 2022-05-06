# push-artifact-s3-with-gitlab

# Pre-requisites
    GitLab SetUp
    Gitlab Runner with Docker Executor
# GitLab SetUp
  [GitLab](https://github.com/Naresh240/Gitlab-Setup/blob/main/README.md)
# Create Project
    Open GitLab account and create new project
# Install GitLab Runner
1. Add the official GitLab repository:
   
    curl -L "https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.rpm.sh" | sudo bash
2. Install the latest version of GitLab Runner

    yum install gitlab-runner -y
  
  Go to the project’s Settings > CI/CD and expand the Runners section and get URL and token
  go to ```Settings > CI/CD and expand the Runners section```
    
    sudo gitlab-runner register -n \
        --url http://<URL>/ \
        --registration-token bszC6hSfL8fxaW4yQief \
        --executor docker \
        --description "docker-runner"
   Here We can you different executors, like shell, ssh, docker, kubernetes etc..,
 # Goto WebUI and check Runner
   Go to the project’s Settings > CI/CD and expand the Runners section
   Click on Expand
   
   ![image](https://user-images.githubusercontent.com/58024415/104083102-d0018d00-5261-11eb-8064-51d33e1de759.png)

If you want to push artifacts to S3 bucket follow below steps
1. Create user with S3 full access
2. Create S3 bucket
3. Create below variables in gitlab repo under settings --> CICD --> Variable section
    AWS_ACCESS_KEY_ID
    AWS_SECRET_ACCESS_KEY_ID
