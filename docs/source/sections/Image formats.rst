************
Image format
************

MediCurator version 1.0 has extensively been developed for the Dicom image while maintaining relevant interfaces for extension to the other image formats.

Image is the actual data to be managed in MediCurator. Each Image consists of a Metadata and a byte[] as its raw data. Each Image has a relative path as its storage location. We calculate the MD5 value as hash code for comparing two Images' raw data. 

MediCurator has an abstract Image class which deals with the above matters. 

Especially, it has two abstract functions :

    public abstract Metadata getMetadata();

    public abstract byte[] getRawImage();

If you want to extend to some other image format, you just need to add a class like DicomImage.java. What's the most important, you should add the way to parse the image, like appling dcm4che to parsing the dicom images.


