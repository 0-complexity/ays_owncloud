# New features test plan (26 Oct 2016)
This is only a start plan which can be extended later on while more understanding each feature requirements.
 
Prepared by:
	(Ramez Saeed) 
	(26 Oct 2016)

## TABLE OF CONTENTS
    1.0  INTRODUCTION                         
    2.0  OBJECTIVES AND TASKS                         
        2.1  Objectives                                         
        2.2  Tasks                         
    3.0  SCOPE                                 
    4.0  Features to Be Tested     
    5.0  Testing Strategy                                                  
        5.1  System and Integration Testing                 
        5.2  Performance and Stress Testing                                                              
    6.0  Environment Requirements                                                                                                                      
    7.0  Resources/Roles & Responsibilities                                   
    8.0  Dependencies
    9.0  RISKS/ASSUMPTIONS
                                 
###1.0 INTRODUCTION
This test plan is a high level test overview for the mentioned new features,
more details about the test steps itself should be added in the future when have more info about
each feature and try them manually.
 
###2.0 OBJECTIVES AND TASKS
####2.1    Objectives
	create test coverage for all the mentioned new features.

####2.2    Tasks
	https://github.com/gig-projects/org_quality/issues/509

###3.0 SCOPE
	Functional testing
	Performance testing 

### 4.0 FEATURES TO BE TESTED
	1- AYS own cloud
	

### 5.0 TESTING STRATEGY
	we need to use the cockpit and AYS blue prints to drive test in these features.

### 5.1    System and Integration Testing
	
	1- AYS own cloud
		Reference:
			https://github.com/0-complexity/ays_owncloud/blob/master/specs/initial.md
		test1:
			1. Input parameters that customers will need to pass when buying an OwnCloud system
			   [domain (optional), ItsYou.Online organization of people allowed to login,
         ItsYou.Online organization of people allowed to administer]
			2. create blueprint template with different combination for the needed params
			3. assert that the passed params are reflected correctly in the created ownclod
			4. update the bluprint to login/administer with not authenticated user, should fail
    
    test2:
			1. create blueprint to upload VMs to ownclowd
      2. check the storage used on ownclowd
      3. update blueprint to upload more VMs
      4. test Dynamic storage capacity, should be updated and increased.
      
		test3:
			1. create blueprint to upload VMs to owncloud
      2. test storage setup done correctly as described in the specs
			3. update blueprint to test Cockpit API results after deploying blueprint
			4. update blueprint to test export a VM to the deployed owncloud for the same VDC, should succeed
			5. update blueprint to create another ownclowd on different VDC
			6. update blueprint to test export a VM to the deployed owncloud for the different VDC, should fail

### 5.2    Performance and Stress Testing
	1- AYS own cloud
		1. lots of storage: push over 5tb to the owncloud ==> expected result automatic scaling of the owncloud ays service kicks in and dynamically adds storage to the owncloud machine / btrfs /data filesystem
		   Hints:
		      create 100 mb random file
		      encrypt random file
		      encrypt encrypted random file
		      ...
		2. lots of clients: mount owncloud over webdav for 100, 1000, 10000 times and trigger filemodification on 10% of the mounts


### 6.0 ENVIRONMENT REQUIREMENTS
	1- Virtual machine to have the cockpit installed.
	2- test environment has all the new features installed and updated.

### 7.0 RESOURCES/ROLES & RESPONSIBILITIES
	QA team members who are involved in this:
		Ramez Saeed
		Islam Taha

### 8.0 DEPENDENCIES
	- stable cockpit deployment and installation
	- stable AYS installation
	- support from the development team to help adding AYS templates as per tests requirements

### 9.0 RISKS/ASSUMPTIONS
	- Please note that there is maybe delay of delivery because of there is no knowledge about these new features
		in the testing team, so testing team will need some time for learning curve and manual tries for these features.
	- will use the new testing procedure which is running everything through cockpit and AYS which is not fully clear
		for the testing team yet.

