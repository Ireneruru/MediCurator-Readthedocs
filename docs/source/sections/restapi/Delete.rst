******
Delete
******

Remove Dataset from replica Set
###############################

    http://localhost:4567/removeDataSet?replicasetID=***&datasetID=***

remove the Dataset from the replicaset but not delete from the storage

return the status of the operation "succeed" or "failure"

Delete Dataset
##############

    http://localhost:4567/deleteDataSets?datasetID=***

recursively delete the Dataset and you can download again 

return the status of the operation "succeed" or "failure"

Delete the images under a dataset
#################################

    http://localhost:4567/deleteOneDataSet?datasetID=***

Only Delete the images below the dataset 

return the status of the operation "succeed" or "failure"


