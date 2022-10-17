# Overview
- Setup an ec2 with tomcat installed with the sample.war
- To demo app2c installation and usage
- Refer to my google slides on this.

## Preq-req: Setting up ec2 with tomcat and sample.war installed
- the ec2 will be used to test app2c

    MUST TURN OFF AWS CISCO VPN ELSE WE WON'T BE ABLE TO ACCESS THE TOMCAT SERVER FROM LAPTOP

- New ec2 based pn amazon linuz ami 2
- use the standard dev-cpe vpc and choose public subnets
- SG to allow access to port 8080 and port 22 (in case need to ssh in)
- The user data in the following section to setup tomcat
- use my normal key: bk-mac
- Access the tomcat app:
    http://PUBLIC_IP:8080/sample


### User data
``` 
#!/bin/bash

sudo yum -y install tomcat git
sudo systemctl enable --now tomcat
pushd /tmp
curl https://tomcat.apache.org/tomcat-7.0-doc/appdev/sample/sample.war -o sample.war 
sudo cp -r sample.war /usr/share/tomcat/webapps/
popd
```

---

## Demo app2c installation
1. ssh to the ec2 server running tomcap sample app

2. Download app2c:  

    ```
    curl -o AWSApp2Container-installer-linux.tar.gz https://app2container-release-us-east-1.s3.us-east-1.amazonaws.com/latest/linux/AWSApp2Container-installer-linux.tar.gz
    ```

    > Taking note app2 also supports remote methods. The lab uses the 'local'i
      methods where app2c and the app server are on the same machine

3. Extract the tar file for app2c into a temp direcgtory
  
    ```
    mkdir app2c
    cd app2c
    tar xvf ../AWSApp2Container-installer-linux.tar.gz 
    ```
4. Show the extracted contents (highligting the *install.sh* script)
5. Run the install.sh script. 

    ```
    ./install.sh
    ```
    
    > Files as it needs root permission
6. Re-reun with root permissions. 

    ```
    sudo ./install.sh
    ```

   app2container is installed to */usr/local/app2container/AWSApp2Container*. 
   

7. app2container is now installed



## app2container phases
Using app2container involves 'phases'

Typical PHASES in a simple workflow:

**INITIALIZE** --> **INVENTORIZE** --> **ANALYZE** --> **TRANSFORM** --> **DEPLOY**


### Initialize Phase

blah about this phase. 

  ```
  sudo app2container init
  ```
    