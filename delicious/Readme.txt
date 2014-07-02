Product: Integration tests for WSO2 Delicious connector

Pre-requisites:

 - Maven 3.x
 - Java 1.6 or above

Tested Platform:

 - Linux 3.11.0-19-generic (Ubuntu 13.10)
 - WSO2 ESB 4.8.1

STEPS:

1. Add the WSO2 ESB 4.8.1 to the {basedir}/test folder.
    If you want to use another location, please change it accordigly in the pom.xml as follows.

          <carbon.zip>
            ${basedir}/../test/wso2esb-${esb.version}.zip
          </carbon.zip>

2. Make sure the delicious test suite is enabled (as given below) and all other test suites are commented in the "testng.xml" file.

      <test name="Delicious-Connector-Test" preserve-order="true" verbose="2">
        <packages>
            <package name="org.wso2.carbon.connector.integration.test.delicious"/>
        </packages>
      </test>


3. Update the delicious.properties file with your details if you have any or you can use the default account details as it is.

    username: wso2delicious
    password: !2qwasZX

4. Navigate to "${basedir}" and run the following command.
     $ mvn clean install