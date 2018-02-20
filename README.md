# FastAnnotationMultipleObjects
This tool can be used to annotate large number of images (draw bounding boxes and assign label) in PASCAL VOC format very fast.
Our tool is at least 2 times faster than LabelImg(https://github.com/tzutalin/labelImg) for images containing multiple objects per image. You can annotate around 1500 images per man day (8 hours).
If your data set containg only one objrct per image, use our other tool FastAnnotationSingleObject https://github.com/udaypk/FastAnnotationSingleObject which is can be 10x faster than LabelImg (1000 images per man hour).


1. Description: 
	AnnotationToolMultipleObjects.exe should be used if your image set has multiple objects per image.  <br>
		The tool automates many steps comapred to LableImg and other such tools. <br>
		Number of clicks, assigning a tag and saving xml are all done automatically without any user intervention. <br>
		If your image set has only one object per image, use AnnotationToolSingleObject.exe which is much faster. https://github.com/udaypk/FastAnnotationSingleObject <br>
2. Prerequisites and requirements:<br>
	a. Install MATLAB 2017a MCRInstaller.exe <br>
	   Windows http://ssd.mathworks.com/supportfiles/downloads/R2017a/deployment_files/R2017a/installers/win64/MCR_R2017a_win64_installer.exe <br>
	   Linux   http://ssd.mathworks.com/supportfiles/downloads/R2017a/deployment_files/R2017a/installers/glnxa64/MCR_R2017a_glnxa64_installer.zip <br>
	   MacOS   http://ssd.mathworks.com/supportfiles/downloads/R2017a/deployment_files/R2017a/installers/maci64/MCR_R2017a_maci64_installer.dmg.zip <br>

3. Usage:
        a. Download AnnotationToolMultipleObjects.exe and AnnotationToolMultipleObjectsConfig.xml fron Executables folder. <br>
	b. It is mandatory to follow Pascal VOC directory structure for stroing the images you want to annotate. <br>
	      All images should be in VOC2012\JPEGImages <br>
	      All annotation xmls will be generated in VOC2012\Annotations <br>
	c. Update AnnotationToolMultipleObjectsConfig.xml as per your requirement before running AnnotationToolMultipleObjects.exe. See below for details of xml configuration. <br>
	d. Double click on AnnotationToolMultipleObjects.exe to start annotation. <br> 
	e. You will see a pop up asking for confirmation of the image folder path and object tag.<br> 
	f. On pressing "Proceed" the tool loads first image.<br>
	g. Draw the bounding box on that image. The tool will prompt to select a tag for the bounding box based on tags configured in AnnotationToolMultipleObjectsConfig.xml. <br> 
	h. You can draw multiple bounding boxes to annotate all the objects in the image. <br>
	i. After completing annotating all objects in the image press "d" on keyboard. The tool automatically creates an annotation file in Annotations folder and loads next image without any manual intervention.<br>
	j. Proceed annotationg all images. <br>
	k. If you have drawn a wrong bounding box, you can simply press "x" to cancel the previous bounding box and tag. <br>
	l. You can reload current image deleting all previous bounding boxes in the current image by pressing "s".<br>
	m. Press "d" to go to next image. <br>
	n. Press "a" to go back to previous image. <br>

4. Updating AnnotationToolMultipleObjectsConfig.xml<br>
        Modify the parameters in config tag before starting the exe.<br>

        folderPath::is absolute path to basefolder. 
        Example: If you want to annotate cat images and all your images are located in C:\Data\Corpus\CatsAndDogs\VOC2012\JPEGImages
        <folderPath>C:\Data\Corpus\CatsAndDogs\VOC2012\</folderPath> 

        firstImage::Tool starts loading images in alphabetical order. This tag indicates the first image you want to load.
        Example: If you have images Cat001.jpg, Cat002.jpg ...Cat999.jpg
        You have annotated upto Cat245.jpg yesterday, you can modify the firstImage tag to: 
        <firstImage>Cat246.jpg</firstImage> 
        and the tool will load images Cat246.jpg. 
        
        objectName::defines the class tag. This tool allows you to tag multiple classes per folder.
        Example: 
        <objectName>cat</objectName>
        <objectName>dog</objectName>
        
        You can have any number of objectName tags but at least one objectName is mandatory.
 
 5. Usage Example: <br>
        Usage video: "ToDO" <br>
 	This tool should be used if your image set contains multiple objects per image. <br>
 	Your goal is build an annotated corpus for object classification for cat and dog. <br>
 	You have images that contain any number of cat or dogs per image. <br>
 	Create a folder CatsAndDogs <br>
 	Copy all your images into CatsAndDogs\VOC2012\JPEGImages directory.<br>
 	Update the AnnotationToolMultipleObjectsConfig.xml file as shown: <br>
 	\<folderPath\>C:\Data\Corpus\CatsAndDogs\VOC2012\\<\/folderPath\> <br>
 	\<firstImage\>Cat001.jpg\<\/firstImage\> <br>
 	\<objectName\>cat\<\/objectName\> <br>
 	\<objectName\>dog\<\/objectName\> <br>
 	Run AnnotationToolMultipleObjects.exe. <br>
 	Draw bounding boxes in each image. <br>
 	All the annotation files will be created in C:\Data\Corpus\CatsAndDogs\VOC2012\Annotations folder <br>
