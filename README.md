# Objectives

This example covers how to install and deploy the mDrive microservice to the edgeSDK runtime. The mimik team created this microservice for mimik access to enable file sharing among edge devices. These are the main functionalities:

1. Allow generating a link to share files through mDrive POST /files request

2. Other devices can get the file through mDrive GET /files request

3. Device also has option of deleting share files and add authentication keys to secure the access

## Run example microservice

1. Install the drive-v1.tar image on edgeSDK mCM container using bearer token 

```curl -i -H 'Authorization: Bearer **replaceWithYourToken**' -F "image=@drive-v1.tar" http://localhost:8083/mcm/v1/images```


2. Initialize drive microservice in edgeSDK mCM contatiner using bearer token

``` curl -i -H 'Authorization: Bearer **replaceWithYourToken**' -d '{"name": "drive-v1", "image": "drive-v1", "env": {"MCM.BASE_API_PATH": "/drive/v1", "AUTHORIZATION_KEY": "**yourCustomAuthorizationKey**"} }' http://localhost:8083/mcm/v1/containers``` 

3. Verify that mBeam microservice registered and works properly by calling following curl commands:

```curl -i http://localhost:8083/drive/v1/files```

## Recommended guides

* [mimik serverless JavaScript programming API](https://github.com/mimikgit/edgeSDK/wiki/How-to-use-mimik-serverless-JavaScript-programming-API)
