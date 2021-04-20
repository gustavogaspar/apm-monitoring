# Application Performance Monitoring 
This is a self-study repo about Oracle Cloud Infrastructure Application Performance Monitoring platform.

## To follow the samples present on this repository you have to first configure your APM environment. Here is a quick guide on how to do it.
_Please notice that this guide may be outdated, always use the documentation to have access to the latest configuration_

1. Login to your OCI account. https://www.oracle.com/br/cloud/sign-in.html
2. On the top search bar type: "Application Performance"
3. Under Services menu, select Administration
4. Create a new APM Domain
_An APM domain is an Oracle Cloud Infrastructure resource, which contains the systems being monitored by Application Performance Monitoring._
	- Set a Name for your Domain
	- Select the compartment that your APM Domain must be created
	- APM is a service that has a free tier option, enable it if you find fit for your use case.
5. The two most important information will be your key pair and also your Data Upload Endpoint, which you can easly find in the Domain page.
