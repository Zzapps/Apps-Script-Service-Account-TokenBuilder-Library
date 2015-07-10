# Apps-Script-Service-Account-tokenBuilder-Library  
##### This is an improved Google service account library for Google Apps Script. This uses NodeJS to run a micro service to complete the signing process.  

My previous service account library ran the RSA Signing code in Google Apps Script. This proved to be too encumbersome for the limited resources allocated for each script.  Working with Riël Notermans we put together a solution to use node as a micro signing service.  Riël put together the node server code and I adapted my previous library to use this service.  

#### Using this Library  
##### Create a Service Account
1) Create a new API Project in your developers console, or use one associated with your script.   
2) Select APIs and Auth -> Credentials  
3) Click 'Create New Client Id'  
4) Select Service Account and p12 key  
5) Click 'Create Client Id'. The p12 key will autodownload.  

##### Prepare your Service Account RSA Key  
Prepare your Service Account key for library by running the following command:  
 - openssl pkcs12 -in YOURPRIVATEKEY.p12 -nodes | openssl rsa | base64 > myfile.pem.b64  

If you are running Windows you will need to install openssl and base64.exe  
[base64.zip](https://drive.google.com/open?id=0B_j9_-NbJQQDQ2xNUEloMlV1b1U)  
[Openssl for windows](http://slproweb.com/products/Win32OpenSSL.html)  

##### Using the Library  
You can either either use the code from this repo or include the library MLMfbjxn4nA3IwygCAa7Pqsh00DPSBbB3  
  
    
    /*  
    * Constructor for the tokenBuilder Library. Use this to initialize a tokenBuilder object.  
    * @param {String} rsaKey Your private RSA key in PEM64  
    * @param {Array} Scopes An Array of scopes you want to authenticate    
    * @param {String} saEmail The service account Email  
    * @return {object} self for chaining  
    */  
    function tokenBuilder(string RSAKey, array Scopes, string ServiceAccountEmail)   
      
    /*  
    * Sets the url to the signing server if you don't wish to use the default  
    * @param {String} serverUrl Url of the server you want to use  
    * @@return {object} self for chaining  
    *\  
    function setSigningServer(string serverUrl)  
      
    /*  
    * Adds a user to the builder. Multiple users can be added for batch calls  
    * @param {String} userEmail The Email account of the user for whom you are requesting the token  
    * @return {object} self for chaining  
    *\  
    function addUser(string userEmail)   
      
    /*  
    * Generates a JWT Claim for each user you added with addUser()    
    * @return {object} self for chaining  
    *\  
    function generateJWT()    
      
    /*  
    * Requests an Oauth token for each JWT Claim generated by generateJWT(). You must call genereateJWT() before this function.  
    * @return {object} self for chaining  
    *\  
    function requestToken()   
      
    /*  
    * Gets the Oauth token for the specified user. You must call requestToken() before this function.  
    * @param {String} userEmail The email account of the user you want  
    * @return {object} {token,expire}  
    *\  
    function getToken(string userEmail)  
      
    /*  
    * Gets all the tokens generated by requestToken(). You must call requestToken() before this function.  
    * @return {object} {user:{token,expire} , user:{token:expire} , ... }   
    *\  
    function getTokens()  
  
  
