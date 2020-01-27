#  API Secure Code Review cheat sheet. 
##  Focused on microservice architecture with no user or browser interaction.

The category list is based on OWASP API Security Project.

##  API1:2019 Broken Object Level Authorization
N/A in most of the cases of internal APIs that provide raw data.

##  API2:2019 Broken User Authentication
N/A in most cases due to lack of user-API interaction and different roles to access resources 

## API3:2019 Excessive Data Exposure

Trust no one. All data should filter, sanitize and validate the input and output data.
No excessive or sensitive information should be exposed or send with the response.

## API4:2019 Lack of Resources & Rate Limiting
Since APIs usually don't limit incoming requests numbers and throttling might not be the best solution, another mechanism should be applied. 
For example, it could be limited by Who can access what. Like specific addresses requests should come from. 
This process should be performed according to the policies and strictly monitored.

## API5:2019 Broken Function Level Authorization
N/A in most cases due to lack of user-api interaction and different roles to access resources 

## API6:2019 Mass Assignment
All input data should be whitelisted while binding to the model to avoid misuse of object properties. 

## API7:2019 Security Misconfiguration
The application should be properly configured using the framework mechanism (i.e. Spring Security). All data should be transmitted encrypted and with forced HTTPS and enabled either CSRF or using JWT.
HTTP headers should be configured properly. Error messages should contain no sensitive information or reveal system configuration in any way.
Debug log level should be disabled in production and debug logs shouldn't contain any CRD.
Another risk here is the use of obsolete or insecure components (the components with known vulnerabilities). Those should be replaced with new and safe libraries.

## API8:2019 Injection
The most relevant in this case injection types are SQL and NoSQL injections.
To avoid the risk of this kind of threat use parametrized and bound queries at all times. 
Never use concatenation, especially for any input data. 

## API9:2019 Improper Assets Management
All endpoints information should be documented and up to date. The proper inventory of host and deployment information such as API versions deployed should be in place to keep track of actual and obsolete endpoints.

## API10:2019 Insufficient Logging & Monitoring
Business logic events should be logged properly without exposing sensitive information but sufficient for possible future investigations.
On a higher level, all activities should be monitored in order to notice suspicious activities as soon as possible.
