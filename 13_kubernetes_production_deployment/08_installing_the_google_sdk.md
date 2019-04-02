# Installing the Google Cloud SDK 
1. cd into the root of the project and create a ```.travis.yml```file.  
2. Add this code.  
```
sudo: required
services:
  - docker
before_install:
  # Download and install Google Cloud SDK. The last part is going to install it.
  - curl https://sdk.cloud.google.com | bash > /dev/null;
  # Look at the default install directory and modify the shell via the source command
  - source $HOME/google-cloud-sdk/path.bash.inc
  # Update kubectl
  - gcloud components update kubectl
  # Authorize gcloud to get access to our account
  - gcloud auth activate-service-account --key-file service-account.json
```
