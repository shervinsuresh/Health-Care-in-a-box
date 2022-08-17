# OpenEMR AMI that connects to an external rds database  
- the cloud formation template is still not created that deploys an RDS database 

## AMI  
### ami-07136f548aa975ea0  
- this ami is a modified instance of ubuntu running an OpenEMR container  
- in order to change the database the application speaks to:  
0. make sure when you are deploying the ami, you click the box where it says "assign a public Ipv4 address"
1. connect to this instance through ssh client (on mac you can use the terminal)
2. navigate to the folder where you have saved the key pair used when launching this ami
3. use a command as such to ssh into the instance: 
```
ssh -i "key-file.pem" ubuntu@ec2-##-###-#-###.us-west-2.compute.amazonaws.com
```
4. assume root: 
```
sudo su
```
5. navigate to the correct directory:
```
cd openemr-devops/packages/standard/
```
6. run ``` docker-compose down``` stops the running docker
7. add the docker-compose.yaml file given at: (you might want to use ```nano docker-compose.yaml```  
[docker-compose.yaml](/OpenEMR%20Application%20and%20Database/OpenEMR%20AMIs/docker-compose/docker-compose.yaml)
8. make sure you change the endpoint and credentials for the rds database you have created
9. save the edited file
10. run ```docker-compose up``` 
11. check if the docker is running (you might need to run a new terminal connected to the instance following steps 1-4)  
``` docker ps -a```  
12. if all good you should see 1 container running called something like openEMR  
