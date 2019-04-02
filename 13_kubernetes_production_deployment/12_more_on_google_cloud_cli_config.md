# More on Google Cloud CLI Config
1. Go to the .travis.tml file and add this code.  
To get the project name click select project in the google console and copy the id.  
To get the data location go to kubernetes engine in the google console.  
```
  # The project id from google console
  - gcloud config set project learned-alcove-236015
  # Specify your data location
  - gloaud config set compute/zone europe-north1-a
  # Tell what cluster we are going to work with(the name we gave it when we created the cluster)
  - gcloud container clusters get-credentials multi-cluster
```
