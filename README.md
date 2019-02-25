# WSO2-2.6.0 OIDC Feature Install
Based on files and instructions from: https://github.com/wso2/docker-apim, https://docs.wso2.com/display/ADMIN44x/Working+with+Features#WorkingwithFeatures-pom_approachInstallingfeaturesusingpomfiles

Installing OIDC feature in WSO2 APIM binaries and building resulting Docker image.

Tested on Ubuntu 18.04(Other OS's require a different Dockerfile, see above links).

# Installing feature

- Download base WSO2 APIM binaries from https://wso2.com/api-management/ and extract it to apim/files (Make sure the extracted folder is named wso2am-2.6.0)
- Download JDK 1.8(for Linux x64) from https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html and extract it to apim/files
- Install OIDC feature by running:
```
maven clean install
```
(Note: There is a known bug with WSO2 and newer versions of Java, so you must be running Java 1.8 for this to not throw an error)

# Builing Docker Image

Build Docker image with the command:
```
docker build -t wso2am:2.6.0 .
```

# Testing

- Run the Docker image with the command:
```
docker run -it -p 9443:9443 wso2am:2.6.0
```

- Access management console with navigating your broswer to https://<Docker Host>:9443/carbon

- Check the feature is installed by navigating to Configure->Features->Installed Features and searching for "OIDC"
