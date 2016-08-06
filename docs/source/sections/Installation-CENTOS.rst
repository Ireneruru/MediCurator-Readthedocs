*****************************
Installing MEDIator on CentOS
*****************************


Installing the Core Dependencies
################################

**Install wget**

$ yum install wget


**Install Oracle JDK 8**

cd /opt

sudo wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" \
"http://download.oracle.com/otn-pub/java/jdk/8u25-b17/jdk-8u25-linux-x64.tar.gz"

sudo tar xvf jdk-8u25-linux-x64.tar.gz

sudo chown -R root: jdk1.8.0_25

export JAVA_HOME=/opt/jdk1.8.0_25/

export PATH=$JAVA_HOME/bin:$PATH


**Install Maven 3**

wget http://mirror.cc.columbia.edu/pub/software/apache/maven/maven-3/3.0.5/binaries/apache-maven-3.0.5-bin.tar.gz

sudo tar xzf apache-maven-3.0.5-bin.tar.gz -C /usr/local

cd /usr/local

sudo ln -s apache-maven-3.0.5 maven

sudo vi /etc/profile.d/maven.sh

export M2_HOME=/usr/local/maven

export PATH=${M2_HOME}/bin:${PATH}


**Install git**

sudo yum install git


Configure MEDIator
##################

git clone https://pradeeban@bitbucket.org/BMI/datareplicationsystem.git

cd datareplicationsystem


Execute the MEDIator web app
############################

mvn package

sh modules/repl-server/target/bin/webapp


with nohup

nohup sh modules/repl-server/target/bin/webapp > nohup.out &


To view the logs

tail -f nohup.out


Go to http://localhost:<EMBEDDED_TOMCAT_PORT>/ using your browser.


Execute with multiple data sources
##################################

java -classpath lib/repl-server-1.0-SNAPSHOT.jar:lib/*:conf/ edu.emory.bmi.datarepl.ds_impl.DSIntegratorInitiator


