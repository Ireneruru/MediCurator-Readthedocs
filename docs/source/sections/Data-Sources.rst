************
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

DICOMWeb is the web standard for medical imaging. Since it has become more and more popular, now talk about it more detailly.

DICOMWeb has two main kinds of API that will be used, retrieve and download.

To extend to DICOMWeb, you should add a DICOMWebDataSource.java
and DICOMWebDataSet.java basicly.

In DICOMWebDataSource.java:

    you should at least implement the function:

    public abstract UUID getRootDataSet();

In DICOMWebDataSet.java:

    you should at least implement the functions:

    public abstract UUID getParent();
    public abstract UUID[] getSubsets();
    public abstract UUID[] getImages();
    public abstract boolean updated();
    public abstract String getKeyword();

The function getSubsets() and getImage() is the most complicate because you should use it to make the DICOMWeb and MediCurator unify.

Besides, you can add some more classes, such as DICOMWebQuery to help you parse the API. This is up to your coding style.


