# Introduction 
This Mule example application demonstrates interface created with APIkit, Anypoint Studio's tooling for building REST APIs with RAML interfaces. 
The application takes a RAML file and maps it to an implementation of an API. This example implementation routes the request according the method which was used (GET, POST, PUT, DELETE) and generates a dummy message.

# How it works
Application is focused on implementing an API definition, which is based on the RAML API specification that you can find in the src/main/resources/api folder of the project.
It uses the APIKit Router component to route requests to the proper flows. There are five different flows, one for GET, PUT, and DELETE requests with an uri parameter and POST, GET requests without uri parameter. The flow then generates a dummy return message.

# Build and Test
Follow the procedure below to create, then run the application in Mule ESB.
Open the Example project in Anypoint Studio. In the Package Explorer panel in Studio, right-click the project name, then select Run As > Mule Application.

Get loan offers for multiple customers:  
Open http://localhost:8081/customerprofile in your browser to get a response from the application. 
Sample reply is returned, including:
- customer name
- ssn
- loan amount
- loan currency
- term
- payments
- bank
- request date

Create customer loan profile:
Send sample HTTP POST request to http://localhost:8081/customerprofile:  
{  
	"name": "John FLetcher",  
	"ssn": "123456789",  
	"amount": 10000,  
	"currency": "EUR",  
	"term": 10,  
	"bank": "1",  
	"requestedDate": "2018-12-12"  
}  

Get loan offers for a single customer:
Open http://localhost:8081/customerprofile/1234 in your browser to get a response from the application. 
Sample reply is returned, containing same type of data as in the case of GET request for multiple customers.

Replace customer loan profile:
Send sample HTTP PUT request to http://localhost:8081/customerprofile/{SSN}:   
{  
	"name": "John FLetcher",  
	"ssn": "123456789",  
	"amount": 10000,  
	"currency": "EUR",  
	"term": 10,  
	"bank": "1",  
	"requestedDate": "2018-12-12"  
}  

Delete customer loan profile:
Send HTTP DELETE request to http://localhost:8081/customerprofile/{SSN}

# Encrypted properties
Sensitive configuration data, like passwords are encrypted using MuleSoft Secure Properties module. 
