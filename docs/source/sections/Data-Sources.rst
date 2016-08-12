***********
Data Sources
************

MediCurator version 1.0 has extensively been developed for The Cancer Imaging Archive (TCIA) and local data file system, while maintaining relevant interfaces for extension to the other data sources.


MediCurator has an abstract data source. It is mainly about the management of the heterogeneous data sources such as  CSV, caMicroscope, Amazon S3, TCIA and so on. 

The main function is to get the UUID of the datasource, to get the UUID of the root Dataset and store the DataSource to the infinispan.

Especially, it has an abstract function :

    public abstract UUID getRootDataSet();

If you want to extend to other data sources, you should finish the abstract function and have a constuction function of the new class.

Take tcia for example,
     it add the function: 
    
    //DataSource type is 'tcia'
    public TciaDataSource()
    {
	super("tcia");
	rootDataSet = null;
	store();
    }

    //get a ROOT TciaDataSet
    public UUID getRootDataSet() 
    {
	if (rootDataSet == null)
	{
	    rootDataSet = (new TciaDataSet(TciaHierarchy.ROOT, null, new Metadata())).getID();
	    store();
	}
	return rootDataSet;
    }

This is not enough.

Since you want to change a data source, you should change the function: "getSubsets" and the method to modify the "boolean updated" in the DataSet.java.

In this way, you can have extension to any other data source as you want.
