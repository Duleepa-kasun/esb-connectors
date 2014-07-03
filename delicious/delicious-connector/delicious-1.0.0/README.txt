Product: Integration tests for WSO2 ESB Delicious connector

Pre-requisites:

 - Maven 3.x
 - Java 1.6 or above


Tested Platform: 

 - UBUNTU 13.04
 - WSO2 ESB 4.8.1

STEPS:

 1. Make sure WSO2 ESB 4.8.1 to the {basedir}/test folder.
    If you want to use another location, please change it accordigly in the pom.xml as follows.

          <carbon.zip>
            ${basedir}/../test/wso2esb-${esb.version}.zip
          </carbon.zip>

 2. This ESB should be configured as below;
  Please make sure that the below mentioned Axis configurations are enabled (\repository\conf\axis2\axis2.xml).

   <messageFormatter contentType="text/html" class="org.wso2.carbon.relay.ExpandingMessageFormatter"/>
   
   <messageFormatter contentType="application/x-www-form-urlencoded" class="org.apache.axis2.transport.http.XFormURLEncodedFormatter"/>
   
   <messageFormatter contentType="text/javascript" class="org.wso2.carbon.relay.ExpandingMessageFormatter"/>  
   
   <messageFormatter contentType="application/octet-stream" class="org.wso2.carbon.relay.ExpandingMessageFormatter"/> 
   
   <messageBuilder contentType="text/html" class="org.wso2.carbon.relay.BinaryRelayBuilder"/>
   
   <messageBuilder contentType="application/x-www-form-urlencoded" class="org.apache.synapse.commons.builders.XFormURLEncodedBuilder"/>
   
   <messageBuilder contentType="text/javascript" class="org.wso2.carbon.relay.BinaryRelayBuilder"/>
   
   <messageBuilder contentType="application/octet-stream" class="org.wso2.carbon.relay.BinaryRelayBuilder"/>
   

 3. Create a Delicious account and derive the access token:
  i)  Using the URL "https://www.delicious.com/" create a Delicious account.
  ii) Derive the access token by following the instructions.

    a)  Create an application in Delicious
        Then you will get a Client ID and Client Secret

    b)  Use that Client ID Send the request for users’ authorization.
        https://delicious.com/auth/authorize?client_id="CLIENT_ID"& redirect_uri=http://www.example.com/redirect

    c)  Then you will get a Response like 
        http://www.example.com/redirect?code="AUTHORIZAN-CODE"

    d)  Then send the above code for get Access Token
        https://avosapi.delicious.com/api/v1/oauth/token?client_id="CLIENT-ID"
        &client_secret="CLIENT-SECRETE" &grant_type=code&code="AUTHORIZAN-CODE"

  4. Update the Delicious properties file at location "{PATH_TO_SOURCE_BUNDLE}/delicious-connector/delicious-connector-1.0.0/org.wso2.carbon.connector/src/test/resources/artifacts/ESB/connector/config" as below.
   
    i) accessToken - Use the access token you got from step 3.
        
        or

    ii) use your delicious userneme and password.

    
 5. Navigate to "{PATH_TO_SOURCE_BUNDLE}/delicious-connector/delicious-connector-1.0.0/org.wso2.carbon.connector/" and run the following command.
      $ mvn clean install


 NOTE : Following Delicious account, can be used for run the integration tests.
      username: wso2delicious
      password: !2qwasZX
      access token: 10005597-dbbb1db699dec98931cc432f944f714f




