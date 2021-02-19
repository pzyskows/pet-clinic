# Spring PetClinic Application

This repository is a fork of the [spring-petclinic/spring-framework-petclinic](https://github.com/spring-petclinic/spring-framework-petclinic).

This application is used by [Online DevOps Dojo](https://github.com/dxc-technology/online-devops-dojo) to illustrate the DevOps practices.
Customization and vulnerabilities have been added for training purpose. If you wish to use the PetClinic application, please fork the [original repository](https://github.com/spring-projects/spring-petclinic).

<img width="1042" alt="petclinic-screenshot" src="https://cloud.githubusercontent.com/assets/838318/19727082/2aee6d6c-9b8e-11e6-81fe-e889a5ddfded.png">

# Introduction 
This Mule example application demonstrates the use of content-based routing and for each data processing.
The application provides information about possible loans from banks.
It is possible to send customer loan profile creation/replacement and deletion requests, via mocked banks API.

# How it works
The application exposes a service that can be used to ask for possible loan offers from banks. Secondary mocked API (GET/customerprofile endpoint) is queried for the loan propositions and then the final answer is composed, containing:
- name of the customer
- loan amount
- SNN
- loan term

Responses from banks are randomized, including 1, 2 or 3 answers.

Customer loan profile creation/replacement and deletion requests result in a success message from the mocked API, stating that request was processed.

# Build and Test
Follow the procedure below to create, then run the application in Mule ESB.
Open the Example project in Anypoint Studio. In the Package Explorer panel in Studio, right-click the project name, then select Run As > Mule Application.

Get loan offers for a customer:
Open http://localhost:8081/?name=Muley&amount=20000&term=48&ssn=1234 in your browser to get a response from the application. 
In your browser's address bar, replace query parameters and press enter for a new response from the application. 

Create customer loan profile:
Send sample HTTP POST request to http://localhost:8081/:
{
    "name": "John FLetcher",
    "ssn": "123456789",
    "amount": "10000",
    "term": "10",
    "banks": [1],
    "requestedDate": "2018-12-12"
}

Replace customer loan profile:
Send sample HTTP PUT request to http://localhost:8081/{SSN}:
{
    "name": "John FLetcher",
    "ssn": "123456789",
    "amount": "10000",
    "term": "10",
    "banks": [1],
    "requestedDate": "2018-12-12"
}

Delete customer loan profile:
Send HTTP DELETE request to http://localhost:8081/{SSN}

# Choice Router and Foreach references
- For more information on routing messages, see [Choice Router](https://docs.mulesoft.com/mule4-user-guide/v/4.1/choice-router-concept).
- For more information on iterative processing, see [Foreach Scope](https://docs.mulesoft.com/mule4-user-guide/v/4.1/for-each-scope-concept).
