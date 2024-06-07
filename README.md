# setup-java-webapp-stack-locally
In this project we are going to setup this stack locally on different VMs we will use nginx service to create the load balancer experience, we will configure it to route any request comes to the tomcat server which is a java web application service, our app is written in java as per this we used tomcat to host it, In backend sevices we will deploy rabbitMQ which is a message broker 'queing agent', mem cache which is a database cashing and it will be connected to our mysql server
# Steps to Follow

- First we are going to bring up five VMs as mentioned in our vagrant file

- Every vm host file 'etc/hosts' should have the entry of the name and the matching ip address of the VMs so we can connect to them through names not ips, cause ip address may change

- In mysql db vm first update our os and enable extra repos to download extra packages, install mariadb-server'mysql db',after installing service we have to start and enable it,after this clone our source 
  code to apply our db config, create db with name accounts. a user with pass .

- In memcashe vm install memcashe service start and enable it, in memcashe config file we will replace local ip with 0.0.0.0 to avoid this svc from listening only for local connections which means that it 
  can connect to other machines

- In tomcat server we will install java 11 and maven, download tomcat package and extract it , add tomcat user and home directory for this user . after this create systemctl config file,to run systemctl 
  command, now time to build the artifact using maven and deploy this artifact to be the default one

- Be aware of the application properties file it contains backend service info, and how does the app machine will connect to backend 

- In nginx we will replace the default config file with our config and create a link to make our website is the default website for nginx
