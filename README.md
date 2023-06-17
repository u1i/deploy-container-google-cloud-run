# Deploy a container to Google Cloud Run

## 1: Open Google Cloud Shell

[https://ssh.cloud.google.com/cloudshell/editor?hl=en_GB&fromcloudshell=true](https://ssh.cloud.google.com/cloudshell/editor?hl=en_GB&fromcloudshell=true)

## 2: Get the template Container Image

`git clone https://github.com/u1i/docker-hello`

## 3: Make changes

modify index.html in the app directory

## 4: Build Container

change into the directory: 
`cd docker-hello`

`docker build . -t myhello`

## 5: Run Container – Test if it works

`docker run -d -p 8080:8080 myhello`

## 6: Open Google Cloud Container Registry

[Google GCR](https://console.cloud.google.com/gcr)

## 7: Push your Container to GCR

you need to know your Google project ID. E.g. joechip02

if you cannot find your project [look here](https://console.cloud.google.com/billing/projects)

### Tag the container -> it's going to be on GCR
`docker tag myhello2 gcr.io/<PROJECT_ID>/myhello`

so in this case it would be:

`docker tag myhello2 gcr.io/joechip02/myhello`

### Push it to the registry

`docker push gcr.io/<PROJECT_ID>/myhello`

so in this case it would be

`docker push gcr.io/joechip02/myhello`

## 8: Open Google Cloud Run

Open (and initialize if needed!) [Google Cloud Run](https://console.cloud.google.com/run)

## 9: Create a Service in Google Cloud Run

click on "Create Service" button (alternatively, [click here](https://console.cloud.google.com/run/create?project=joechip02)

In the section "Deploy one revision from an existing container image" click the "SELECT" button.

On the right side, select "Container Registry". There, select the container image and version you have just pushed to the registry.






