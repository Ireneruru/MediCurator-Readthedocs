*****************************************
Installation and Execution of MediCurator 
*****************************************

You can easily install Mediurator with only a few staps.

First, you need to get a copy of MediCurator from the following website https://bitbucket.org/BMI/medicurator. Here is the quick start.


Set the Constants
#################

Basicly, the user should set the following the arguments.

1. Set the API_KEY in ./config.sh

2. Set DATA_BASE_DIR in ./src/main/java/edu/emory/bmi/medicurator/Constants.java

3. Set PROXY_HOST, PROXY_PORT if necessary.

The user can choose use HdfsStorage or LocalStorage by changing STORAGE (hdfs/local) in Constants.java. To use HDFS, you should config HDFS_URI and HDFS_BASEDIR in Constants.java. For example, HDFS_URI = "hdfs://localhost:9000/" and HDFS_BASEDIR = "/user/xxx/medicurator/"


Building and Executing Using Apache Maven 3.3.x
###############################################

**Building**

    $./compile.sh

**Testing**

    $mvn test

**Run web application**

    $./run_servlet.sh

It is expected to have the TCIA_API_KEY set in the Constants.java to build with tests.

The webapp runs at http://localhost:2222/Index

You may want to run

    $mvn exec:java -Dexec.mainClass="edu.emory.bmi.medicurator.infinispan.StartInfinispan"

first so that data you hava stored beforehand won't be lost although the web server has been closed.

**Run Restful API**

    $./run_api.sh

Extend or leverage the exposed APIs, or simply test using a REST client such as the Postman Chrome application.


Dependencies
############

This project depends on the below major projects.
    
    1. Infinispan 8.2 stable

    2. dcm4che 3

    3. Apache HTTP Client

    4. Tomcat 7

    5. Hadoop 2.7.2

    6. Spark Java 2.5


