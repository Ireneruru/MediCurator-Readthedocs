*******************************
Building and Deploying MEDIator
*******************************


Building from the source
########################
Checkout the source code

git clone https://<user-name>@bitbucket.org/BMI/datareplicationsystem.git


**Constants**

edu.emory.bmi.datarepl.constants package contains the constants to be modified.

The class DataSourcesConstants contains the constants.


**Configuring Sample Data**

Download a set of medical source from The Cancer Genome Atlas (TCGA)

https://tcga-data.nci.nih.gov/tcga/

When you pick the data and click download, it will send the files in a tar, along with a file map, "FILE_SAMPLE_MAP.txt".

Download the tar, extract them, and upload to S3.

NOTE: The tar contains the associated “blob” that will be linked with the clinical data. The blob in itself does not have any metadata.


*Meta data*

Place all the meta data files in the root folder of the data replication system source code.


Configurations
##############
Set the name of the CSV file that is used to load the CSV meta data into Infinispan.

    public static final String META_CSV_FILE = "getAllDataAsCSV";


NOTE: This is the clinical data

Also set the name of the file sample map of TCGA that is uploaded to S3.

    public static final String S3_META_CSV_FILE = "FILE_SAMPLE_MAP.txt";


NOTE: This is the mapping between the clinical data and the associated “blob” that was uploaded to S3


*S3 constants*

S3 base url contains https://s3.amazonaws.com/ and the bucket name, (dataReplServer was chosen for this prototype).

    public static final String S3_BASE_URL = "https://s3.amazonaws.com/dataReplServer/";


*Folder names.*

The meta data comes into multiple folders, with level1 as the default. If you want to change the default folder, change the value of the constant S3_LEVEL1.

    public static final String S3_LEVEL1 = "level1";

    public static final String S3_LEVEL2 = "level2";

    public static final String S3_LEVEL3 = "level3";


*API Key*

Provide your TCIA API Key in TCIAConstants for the below field.

    public static String API_KEY = "";

NOTE: This is the TCIA API Key.


*CA constants.*

Check the caMicroscope base url and sample query url that is used in the prototype, in DataSourcesConstants class.

    public static final String CA_MICROSCOPE_BASE_URL = "http://imaging.cci.emory.edu/camicroscope/camicroscope/";

    public static final String CA_MICROSCOPE_QUERY_URL = "osdCamicroscope.php?tissueId=";



**Build from the source code root**

$ mvn package


*To execute the DSIntegratorIntegrator:*

$ java -classpath lib/repl-server-1.0-SNAPSHOT.jar:lib/*:conf/ edu.emory.bmi.datarepl.ds_impl.DSIntegratorInitiator



Dependencies
############
This project depends on the below major projects.

* Infinispan
* Apache Tomcat (Embedded)
* Apache HTTP Client
* Apache Velocity
* Apache Log4j2
* Mashape Unirest


Setting the Environment Variables
#################################

Set the API_KEY, MASHAPE_AUTHORIZATION, and BASE_UR as environment variables.

For example, in Linux.

    export API_KEY=your-api-key

    export MASHAPE_AUTHORIZATION=your-mashape-authorization

    export BASE_URL=services.cancerimagingarchive.net/services/v4/TCIA/query


Building and Executing Using Apache Maven 3.x.x
###############################################

mvn package

It is expected to have the TCIA API_KEY set in the environment variables to build with tests.


If you do not have a TCIA API_KEY yet, please build with skipping the tests.

mvn package -DskipTests


Logging
#######
Make sure to include log4j2-test.xml into your class path to be able to configure and view the logs. Default log level
is [WARN].



