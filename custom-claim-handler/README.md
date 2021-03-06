## Custom Claim Handler
### Introduction / Use case.
This custom claim handler will add some external claims. Refer \[1] for more details.

### Applicable product versions.
Tested with IS-5.3.0

### How to use.
1) Stop the server if it is already running.
2) Build the project using following command,
  ```mvn clean install```
3) Copy the jar file __org.wso2.custom.claimhandler-1.0-SNAPSHOT.jar__ from the target directory to __<IS_HOME>/repository/components/dropins__ folder.
4) Change the default claim handler configuration in __<IS_HOME>/repository/conf/identity/application-authentication.xml__ as follows.
```<ClaimHandler>org.wso2.custom.claim.handler.CustomClaimHandler</ClaimHandler>```
5) Start the server.

### Testing the project.
6) Create custom local claim called ```http://test.wso2.org/claims/keplerNumber``` and map it to an attribute which is available in your user store.
7) Then mapped this claims to an oidc claim.
8) Don’t forget to add the oidc claims to the registry.
9) Add a service provider by selecting the requested claim as "http://test.wso2.org/claims/keplerNumber"
10) Get an id token for this service provider.
11) Parse the id token using \[2], now you should be able to see the claim __keplerNumber__ as a json attribute.


\[1] https://medium.com/@nilasini/sso-within-two-sps-while-using-a-custom-authenticator-and-a-custom-claim-handler-wso2is-5-3-0-bd473361ddf6
\[2] https://jwt.io/



