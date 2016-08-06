*******************
Update Replica Sets
*******************

A replica set can either be replaced entirely with new contents, or be appended along with the existing content, by the
user.


Replace Replica Set
###################

A replica set can be replaced with pointers to new content. While the replica set ID remains the same, the entire of its
content would be replaced with pointers to the updated data sets or images.

Replica sets can be replaced by a POST call of a following format.

/POST

/replicaset/:id


For the ease of expression, port 9090 is used as an example in all the examples below.

Make sure to replace 9090 above with the correct value as defined in REST_PORT in MEDIator CommonConstants.



**Sample POST request**

http://localhost:9090/replicaset/-5841894688098285105?iStudyInstanceUID=1.3.6.1.4.1.14519.5.2.1.4591.4001.151679082681232740021018262895&iSeriesInstanceUID=1.3.6.1.4.1.14519.5.2.1.4591.4001.179004339156422100336233996679


This replaces the replica set with the given ID with the newly given information.


**Sample POST response**

true

or

false


If the replica set was successfully replaced, 'true' will be returned. Otherwise, 'false' will be returned.



Append Replica Set
##################

Practically, it is convenient to append an existing replica set than entirely replacing it. Replica sets can be appended
by a PUT call of the following format.

/PUT

/replicaset/:id


**Sample PUT request**

http://localhost:9090/replicaset/-5841894688098285105?iCollection=TCGA-GBM

This appends the existing replica set of the given ID with pointers to the newly given subsets of data.


**Sample PUT response**

If the replica set was successfully updated, 'true' will be returned. Otherwise, 'false' will be returned.