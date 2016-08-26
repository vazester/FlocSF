Here's how a developer can get started working on the FLOC Site using the Sitefinity CMS.

	1. Decide the folder where you want to the project folder to go on your desktop, for example: C:\Working\FlocSF.  Don't create this folder yet.

	2. Right-click on the parent folder (e.g., C:\Working) in Windows Explorer and choose SVN Checkout.  
	   Enter https://wush.net/svn/apex/FLOC/FlocSF/trunk in the URL field.  Enter the desired folder in the Checkout directory: C:\Working\FlocSF.
	
	3. Open the FlocSF.sln file in Visual Studio 2010.
	
	4. Drill into WebApp\App_Data\Sitefinity\Configuration.  Copy the file DataConfig.user.config to DataConfig.config.  
	   When you copy the file, do it in such a way that the DataConfig.config file won't be considered included in the project.  
	   You can either do it via Windows Explorer or do it with Visual Studio.  If you do it with VS, right click on DataConfig.config and choose Exclude from Project.
	
	5. Edit DataConfig.config and make sure that the database connection string is correct.  By default, it points to a database on tsibsdb2.ibsdev.local.  
	
	6. Build the project and start it without debugging.
	
	7. The front-end of the site will display.  
	
	8. To login to the back-end of the site, append Sitefinity to the URL.  Enter admin as the username and password as the password.

-----------------------------------------------------------------------------------------------------------------------------

Here are the initial deployment instructions:

	1. While in Release configuration, publish the WebApp project to a local folder...say C:\Pub\FlocSF

	2. On the server, create a folder where the IIS site will live (e.g., C:\Inetpub\wwwroot\FlocSF.  

	3. Create a site in IIS with this as the site's folder.  Give it a unique port number.

	4. Set the .NET version of the created App Pool to 4.0.

	5. Give Full Control of the FlocSF folder to the user named "iis apppool\FlocSF"

	6. Zip up the contents of the folder where you published the application:  C:\Pub\FlocSF.

	7. Transfer the .zip file using Remote Desktop to the server

	8. Unzip the .zip file into the site's folder

	9. Copy the DataConfig.user.config to DataConfig.config in the C:\inetpub\wwwroot\FlocSF\App_Data\Sitefinity\Configuration folder

	10. Make sure that the DataConfig.config has the right settings to point to the correct database.

	11. Hit the site from a browser directly on the server (using the port #)

	12. Answer any questions about licensing.

	13. Now you have two options for accessing the site remotely.  Either you stick with using the port number in the URL...or 
	    you give the site a host header, like flocsf.terpsys.com and put that host in your hosts file


-----------------------------------------------------------------------------------------------------------------------------
Here are the instructions for deploying an update:

	1. While in Release configuration, publish the WebApp project to a local folder...say C:\Pub\FlocSF

	2. Go to the publish folder and rename the web.config to web.config.new.  This is just a precaution in case the deployed 
	   web.config was modified.  

	3. Zip up the files in the publish folder and transfer the .zip to the server.

	3. Go the server and zip up a copy of the deployed site before applying the update.  This way, we can go back if we break 
	   something.

	4. Unzip the .zip file that you copied from the publish folder on top of the site.

	5. Check if any web.config changes were made.
	   


-----------------------------------------------------------------------------------------------------------------------------

How we did the initial installation/setup of Sitefinity

	1. Download and Install Sitefinity 6.0 Community Edition

	2. Go into IIS and create a new site in a folder of your choosing.  Set the App Pool for that site to be .NET 4.0.  

	3. Give "iis apppool/FlocSF" modify access to the folder where you placed the site

	4. Create a new SQL Database called FlocSF.  Create a login named like FlocSFApp and map it to a user of the same name in that  database.

	5. Run the Project Manager.  Create a Default site/project.

	6. Follow the normal process of creating the top level folders in SVN.

	7. Do a Checkout Module starting with FLOC\FlocSF\trunk to a local folder like C:\Working\FlocSF

	8. Create an empty solution in the main folder called FlocSF.

	9. Copy the Default project to a subfolder of the solution naming it WebApp

	10. Add the existing web application to the solution.

	11. Copy the DataConfig.config file to DataConfig.user.config in the App_Data\Sitefinity\Configuration folder.

	12. Fix various issues with the web application project...mostly by including files that weren't considered to be in the project 
	    and by resolving missing references.

	13. Commit the project to SVN

	14. Add ignores for DataConfig.config and for WebApp.dll and WebApp.pdb.

	15. Commit again
