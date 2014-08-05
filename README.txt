NUGG_ZSLIM.nugg 
	- contains an RFC function module to de-serialize the request from FitNesse and all the classes to handle the functionality so far. 	  
	  
To use FitNesse I suggest copying the FitNesse folder directly to your C drive - C:\Fitnesse

Fitnesse\ABAPSlim.jar
	- FitNesse will launch this Java application so it can call the SAP FM that  de-serializes the request. Since we can't open a port and listen for TCP  requests in SAP we need this Java application to listen for the request and forward it on to SAP. 
	
Fitnesse\NSP.jcoDestination
	- change the file name to be the SID of your SAP instance instead of NSP
	- update the file with the settings for your system, your user name and password

FitNesse\fitness-standalone.jar
	- Run this file to launch FitNesse. 
	- When it's running you can browse to http://localhost/ to use FitNesse
	- Have a look at the ABAPSlim test suite: http://localhost/AbapSlim

You need to configure the AbapSlim test suite to point to your SAP instance and depending on where you put the FitNesse folder you may need to change some other parameters. When you browse to http://localhost/AbapSlim simply click the edit button and change the parameters listed below. The file and folder locations should be pretty straight-forward and the -sap parameter at the end of the 'COMMAND_PATTERN' should be the SID of your SAP instance:

!define TEST_SYSTEM {slim}
!define TEST_RUNNER {C:\Fitnesse\ABAPSlim.jar}
!path C:\Fitnesse\
!define COMMAND_PATTERN {java -Djava.library.path=C:\Fitnesse\ABAPSlim_lib\ -jar C:\Fitnesse\ABAPSlim.jar -sap NSP}
			 