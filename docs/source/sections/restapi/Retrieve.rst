********
Retrieve
********

Retrieve Replica Sets of the user
#################################

The user can use the following API to retrieve the replica Set.

    http://localhost:4567/getReplicaSets?userid=***

It can return all the replica Sets of a user in its UUID.


Retrieve A Replica Set
######################


**Retrieve the DataSets in a replicaSet**
    
    http://localhost:4567/getDataSets?replicasetID=***

return the name and UUID of the Datasets in  a replica set.

Retrieve the subsets of a dataset
#################################

    http://localhost:4567/getSubsets?datasetID=***

return the list of all the subsets in a dataset 

Retrieve the root dataset
#########################

    http://localhost:4567/getRootDataSets

return the root dataset



