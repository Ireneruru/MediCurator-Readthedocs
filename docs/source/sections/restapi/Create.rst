******************
Create Replica Set
******************

Users may create replica sets to point to their interested sub sets of data at different granularity. They may do so, by
creating a replica set from the scratch, or by duplicating an existing replica set. The created (or duplicated) replica
sets can later be modified by the user.

For the ease of expression, port 9090 is used as an example in all the examples below.

Make sure to replace 9090 above with the correct value as defined in REST_PORT in MEDIator CommonConstants.


Create Replica Set from Scratch
###############################

Replica sets can be created using a POST call following the format of,

/POST

/replicasets


**Sample POST request**

http://localhost:9090/replicasets?iUserID=12&iCollection=TCGA-GBM&iPatientID=TCGA-06-6701%2CTCGA-08-0831&iStudyInstanceUID=1.3.6.1.4.1.14519.5.2.1.4591.4001.151679082681232740021018262895&iSeriesInstanceUID=1.3.6.1.4.1.14519.5.2.1.4591.4001.179004339156422100336233996679

This creates a replica set for the user with the user ID 12, with the given attributes of the images hosted in TCIA.


**Sample POST response**

The expected response of the REST call is the ID of the replica set that was created in the previous replica set
creation POST request.

This is a random generated number.

-4764762120292626164



Duplicate Replica Set
#####################

Instead of creating a replica set from scratch, users may share their replica sets with their friends who may duplicate
the replica set to have it as their own. The POST call for the duplicate replica set follows the format as below,

/POST

/replicaset


**Sample POST request**

http://localhost:9090/replicaset?userID=1234567&replicaSetID=-7196077834010820228

The inputs to this POST method are the ID of the current user who is duplicating the replica set, as well as the ID of
the replica set that has been duplicated by the user.


**Sample POST response**

-5054196249282594410

Similar to the create replica set method above, the duplicate method too returns the ID of the newly created replica set.
This is because the internals of the create and duplicate replica set methods function in a similar way, generating a
replica set with a randomly generated replica set ID.