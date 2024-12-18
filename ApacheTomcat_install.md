# ApacheTomcat-Handson

#### -----JDK & Maven Installation----

```shell
sudo apt-get update -y
sudo apt install openjdk-17-jre -y
sudo apt-get install maven -y
```

## Commands To Setup:

```shell
##################----INSTALL TOMCAT----##################
cd /opt
sudo wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.65/bin/apache-tomcat-9.0.65.tar.gz
sudo tar -xvf apache-tomcat-9.0.65.tar.gz

cd /opt/apache-tomcat-9.0.65/conf
sudo vi tomcat-users.xml
# ---add-below-line at the end (2nd-last line)----
# <user username="admin" password="admin1234" roles="admin-gui, manager-gui"/>

sudo ln -s /opt/apache-tomcat-9.0.65/bin/startup.sh /usr/bin/startTomcat
sudo ln -s /opt/apache-tomcat-9.0.65/bin/shutdown.sh /usr/bin/stopTomcat

sudo vi /opt/apache-tomcat-9.0.65/webapps/manager/META-INF/context.xml

comment:
<!-- Valve className="org.apache.catalina.valves.RemoteAddrValve"
  allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->

sudo vi /opt/apache-tomcat-9.0.65/webapps/host-manager/META-INF/context.xml

comment:
<!-- Valve className="org.apache.catalina.valves.RemoteAddrValve"
  allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->

sudo stopTomcat
sudo startTomcat
```
## Commands To create war file and deploy on Tomcat:
```shell
git clone https://github.com/jaiswaladi246/Petclinic.git
mvn clean package

sudo cp target/*.war /opt/apache-tomcat-9.0.65/webapps/

# hit the publicIP:8080 you will see the application displayed on the browser
```

#### After copying the Artifact in webapps folder we can see the deployed application
![alt text](https://github.com/jaiswaladi246/30-Days-Of-DevOps/blob/main/Images/2.png?raw=true)
