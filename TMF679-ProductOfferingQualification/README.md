# PRODUCTOFFERINGQUALIFICATION-CTK
Installing and Running the Product Offering Qualification CTK
The Product Offering Qualification CTK is dependent on the installation of node.js and Newman to work.
The installation instructions for Newman are found here: https://www.getpostman.com/docs/newman_intro
Node.js can be downloaded and installed from:
http://nodejs.org/download/ 
Once Node.js and Newman are installed download and unzip the TMF679-ProductOfferingQualification ZIP file within your test directory.

You should see the following files:
-ProductOfferingQualificationV#.postman_collection : the postman collection for the Mandatory tests
-TMFENV : the Environment variable for the REST API Endpoint

Open the TMForumR2018.0-PaneOn.postman_environment.json file and change the following host value to match your endpoint. Note that by default the environment is pointing to the Sandbox endpoint. 
{
      "key": "schema",
      "value": "https",
      "enabled": true
},
{
	"key": "host",
	"value": "paneon.no",
	"enabled": true
},
{
	"key": "port",
	"value": "8080",
	"enabled": true
},
now look for the ProductOfferingQualificationAPI key and change it so that it matches the URL for the ServiceQualification resource:
{
	"key": "ProductOfferingQualificationAPI",
	"value": "{{schema}}://{{host}}:{{port}}/tmf-api/productOfferingQualificationManagement/v1",
	"description": "",
	"enabled": true
},
Save the new values and exit.

Go to your test directory and type the following command:

> newman run CTK-TMF679-ProductOfferingQualification.postman_collection.json -e TMForumR2018.0-PaneOn.postman_environment.json --reporters html --reporter-html-export TMF679-ProductOfferingQualification-report.html

where ServiceQualificationCTKResult.html and ServiceQualificationCTKResult.json will contain the results of the CTK execution. You should see something like the following example:

Newman Report
Collection
CTK-TMF679-ProductOfferingQualification
Description
This is Swagger UI environment generated for the TMF Trouble Ticket specification 
Time
Fri Aug 17 2018 16:13:29 GMT+0100 (IST)
Exported with
Newman v
 
 
Total
Failed
Iterations
1
0
Requests
12
0
Prerequest Scripts
0
0
Test Scripts
12
0
Assertions
188
0
 
Total run duration
5.6s
Total data received
44.86KB (approx)
Average response time
428ms
 
Total Failures
0


If they are no failures then you have passed the CTK and your API is conformant with all
the Mandatory features.

The results of the CTK are also in  the TMF679-ProductOfferingQualification-report.html
While all the information related to the execution of the CTK will be contained in the ServiceQualificationCTKResult.json file


