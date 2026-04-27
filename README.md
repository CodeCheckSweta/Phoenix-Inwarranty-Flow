# Postman API Automation Integration with GitHub Actions #

This repository is a demonstration for a POC for integrating Postman tests with GitHub Actions. The Tests are written in Postman and executed on the VM using newman and newman-reporter-htmlextra. GitHub Actions will trigger the project execution on every push to the main branch. You can also execute the project manually using workflow_dispatch. The project runs on a scheduled time with the help of the cron job.

The HTML report is archived in the artifacts section for the team to download. Along with that, they can view the report directly from the GitHub page: https://codechecksweta.github.io/Phoenix-Inwarranty-Flow/. The latest report is mailed to the team members using GMAIL SMTP.
## About Me ##
Hi My Name is Sweta Singh. I have 9 years of experience in Automation Testing and DevOps. My Skillset Includes UI Automation with Selenium Webdriver, Playwright and for API Testing I use Rest Assured and Postman. You can connect with me over: (https://www.linkedin.com/in/swetasingh22/)

## Testing Coverage ##
1. Happy Flow Testing
2. Neagtive Testing and Edge Case Testing
3. Token Testing
4. Data Driven Testing with CSV
5. Schema Validation
6. Secrets Management with Github Secrets

## Tech Stack ##
1. Postman
2. NodeJS 22v
3. Newman
4. Newman-Reporter-Htmlextra
5. GitHub Actions
6. Gmail SMTP
7. GitHub Pages
8. CSV for data-driven testing
9. AWS-EC2 Instance for self-hosted GitHub runner

## GitHub Pages ##
You can directly view the latest test report of the Postman Test at the GitHub page link: https://codechecksweta.github.io/Phoenix-Inwarranty-Flow/

## HTML Report ##
The report will be created in the newman folder
![Postman report](https://github.com/CodeCheckSweta/Phoenix-Inwarranty-Flow/blob/static-content/newman-report.png)

## Project Structure ##

```
Phoenix Inwarranty Flow
├─ Inwaranty-flow Collection.postman_collection.json    # Collection File
├─ QA.postman_environment.json    # environment File
└─ testdata.csv    # TestData File

```   

## How to run the project? ##
You can run the project on your local system for that:
1. Clone the Project on Local System: https://github.com/CodeCheckSweta/Phoenix-Inwarranty-Flow.git
2. Install Nodejs and NPM from https://nodejs.org/en
3. Install Newman using ``` npm install -g newman ```  
4. Install Newman-reporter-htmlextra ``` npm install -g newman-reporter-htmlextra ```  
5. Run the Newman Command:
```
      newman run 'Inwarranty-flow Collection.postman_collection.json' \  
      -e QA.postman_environment.json \
      -d testdata.csv \
      -r cli,htmlextra \
      --reporter-htmlextra-export ./newman/index.html
```   
