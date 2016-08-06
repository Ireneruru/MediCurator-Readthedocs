*********************
Retrieve Replica Sets
*********************

A list of the replica sets of the given user, as well as the specifics of each of the replica sets can be retrieved
through the relevant GET calls.


For the ease of expression, port 9090 is used as an example in all the examples below.

Make sure to replace 9090 above with the correct value as defined in REST_PORT in MEDIator CommonConstants.



Retrieve Replica Sets of the user
#################################

This follows the format of

/GET

/replicasets/:id

**Sample GET request**

http://localhost:9090/replicasets/12


**Sample GET response**

If the user has created replica sets, the IDs of the replica sets would be returned as an array, as below.

[-7466653342708752832, -7059417815353339196, -6908825180316283930, -6365519002970140943]


If he does not have any replica sets created, the lack of replica sets would be indicated.

 Replicasets not found for the user: 123




Retrieve A Replica Set
######################

This follows the format of

/GET

/replicaset/:id


**Sample GET request**

http://localhost:9090/replicaset/-9176938584709039161


**Sample GET response**

If the replica set exists, it would be returned as below.

Collection Names: [TCGA-GBM]. Patient IDs: [TCGA-06-6701, TCGA-08-0831]. StudyInstanceUIDs: [1.3.6.1.4.1.14519.5.2.1.4591.4001.151679082681232740021018262895]. SeriesInstanceUIDs: [1.3.6.1.4.1.14519.5.2.1.4591.4001.179004339156422100336233996679]


If the replica set retrieval failed, it would cause an internal error as below.

         <html>
         <body>
         <h2>500 Internal Error</h2>
         </body>
         </html>