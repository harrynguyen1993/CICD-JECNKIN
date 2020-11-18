#Trigger Jenkins Job Remotely using Jenkins API

```
1. Create new pipele line with name is "helloword"
2. Create an authentication token for a job
3. Configure a job to trigger from remote
4. Trigger the job form remote resource
  - With parameters 
  - Not parameters

```
#Create new pipele line with name is helloword

#Create an authentication token for a job
##1. Goto Configure
##2. At API token 
    - Find the “Add new Token” button and click on it.
    - Find the “Generate” and save the ${token}

#Configure a job to trigger from remote
##1. Goto job helloword
##2. Enable Trigger builds remotely and inout token
    - input Authentication Token ${token}
    
#Trigger the job form remote resource

##1. Not parameters 
  - Open post man and create a new POST request 
   ```
   curl --location --request POST 'http://192.168.1.55:8080/job/helloword/build' \
--header 'Authorization: Basic bHVhbm50OjExYWEyZDFjMGQxOGQxMDg5OWQ1ZGY0ZDFkNTU0YjlkYTQ=' \
--header 'Cookie: JSESSIONID.16061c2f=node01hlrmb54k0lbjvayhm17nertb2.node0' \
   ```
   - url:http://192.168.1.55:8080/job/helloword/build
   - authorization: 
      - Username: luannt
      - Password: 11aa2d1c0d18d10899d5df4d1d554b9da4.  #  ${token} 
      
##2. With parameters 
  - Open post man and create a new POST request 
   ```
   curl --location --request POST 'http://192.168.1.55:8080/job/helloword/buildWithParameters' \
--header 'Authorization: Basic bHVhbm50OjExYWEyZDFjMGQxOGQxMDg5OWQ1ZGY0ZDFkNTU0YjlkYTQ=' \
--header 'Cookie: JSESSIONID.16061c2f=node01hlrmb54k0lbjvayhm17nertb2.node0' \
--form 'debug=flase'
   ```
   - url:http://192.168.1.55:8080/job/helloword/buildWithParameters
   - authorization: 
      - Username: luannt
      - Password: 11aa2d1c0d18d10899d5df4d1d554b9da4.  #  ${token} 
      -  body:  form
          debug= true
          
      
      
