###############################
Test Client for SIEM OPEN API
###############################

Description: Executable test client to run diagnostics for debugging purposes.

Setup:
Update properties file with your credentials, as outlined in “Setting up properties section” below.

Usage:
java -jar SIEMSampleClient.jar [pathToPropertiesFile]

Example
java -jar SIEMSampleClient.jar sampleProperties.txt
			  		
#############################
Setting up properties file
#############################

Generating user credentials 
http://developer.akamai.com/introduction/Prov_Creds.html

Parameters:

1. accessToken: Required parameter for authorization
				Example: akab-qxcpf2dex642-tjfcc1dvtx3fqulyeo7
				
2. clientToken: Required parameter for authorization
				Example: akab-cffa2gcryx3agqip-uefe6gqkokyeooxb
				
3. clientSecret: Required parameter for authorization
				Example: EneQRTBD56/D6pYNVNGfNe5678jvRW3NAZrtOysSsc8=

4. host: Required parameter to ingest data
				Example: w34rogxcvxv2nsfrhxp-wfs5nvizxczc5lj.cloudsecurity.akamaiapis.net


5. configIDs: Required for ingest data from particular security configuration
			  Example: 6456 (Single config ID)
			  	   6456;6566 (multiple config ID’s should be separated by semi-colon)
	
OPTIONAL query parameters		  		   
6. from: Time based parameter to set START of a specified time range, expressed in epoch seconds. Example: 1499695200
	 If left empty connector will start with offset=NULL i.e. current time
			  

7. to: Time based Parameter to set END of a specified time range, expressed in epoch seconds. Example: 1499706000
	If left empty connector will start with “from” epoch time and continue with offset returned by SIEM API.
			 

8. requestPollTime: Parameter defined in seconds,to send request after intervals specified in poll time 
		    It is defaulted to 60 secs.

9. limit: Number of security events returned in each fetch. Defaults to 10000 
		
##########################################################			  		
Sample properties file for offset based mode
##########################################################

accessToken=akab-qxcpf2dex642-tjfcc1dvtx3fqulyeo7
clientToken=akab-cffa2gcryx3agqip-uefe6gqkokyeooxb
clientSecret=EneQRTBD56/D6pYNVNGfNe5678jvRW3NAZrtOysSsc8=
host=akab-w34rogxcvxv2nsfrhxp-wfs5nvizxczc5lj.cloudsecurity.akamaiapis.net
configIds=6456
from=
to=
requestPollTime=
limit=1000		  		
			  
			  	
##########################################################			  		
Sample properties file with multiple confgIDs
##########################################################

accessToken=akab-qxcpf2dex642-tjfcc1dvtx3fqulyeo7
clientToken=akab-cffa2gcryx3agqip-uefe6gqkokyeooxb
clientSecret=EneQRTBD56/D6pYNVNGfNe5678jvRW3NAZrtOysSsc8=
host=akab-w34rogxcvxv2nsfrhxp-wfs5nvizxczc5lj.cloudsecurity.akamaiapis.net
configIds=6456;6566
from=
to=
requestPollTime=
limit=1000				  	
			  		
##########################################################			  		
Sample properties file for time based mode with START time
##########################################################

accessToken=akab-qxcpf2dex642-tjfcc1dvtx3fqulyeo7
clientToken=akab-cffa2gcryx3agqip-uefe6gqkokyeooxb
clientSecret=EneQRTBD56/D6pYNVNGfNe5678jvRW3NAZrtOysSsc8=
host=akab-w34rogxcvxv2nsfrhxp-wfs5nvizxczc5lj.cloudsecurity.akamaiapis.net
configIds=6456
from=1499695200
to=
requestPollTime=
limit=1000		

##################################################################			  		
Sample properties file for time based mode with START and END Time
##################################################################

accessToken=akab-qxcpf2dex642-tjfcc1dvtx3fqulyeo7
clientToken=akab-cffa2gcryx3agqip-uefe6gqkokyeooxb
clientSecret=EneQRTBD56/D6pYNVNGfNe5678jvRW3NAZrtOysSsc8=
host=akab-w34rogxcvxv2nsfrhxp-wfs5nvizxczc5lj.cloudsecurity.akamaiapis.net
configIds=6456
from=1499695200
to=1499706000
requestPollTime=
limit=1000			  	
