# APM Browser Agent

This agent will collect information about your web page using Javascript this informations can be: Response Times, Script Errors, Ajax calls, and also will generate Tracing information, like calls that you do to your backend and etc.

To be able to see that in action, I will use a simple setup to build this lab:

1. Create a Compute Instance with Oracle Linux Developer Image (The shape is not important, you can use a Free Tier if you like);
2. Enable the apache server by executing: _sudo systemctl enable httpd_ 
3. Open the http port (80) by executing: 
sudo firewall-cmd --zone=public --permanent --add-port=80/tcp
sudo firewall-cmd --reload
4. After the configuration is done, you can check if the server is up by accessing it's public/private IP in your Browser. It will show you an error of Page not Found which basically means that the server doesn't have an index.html in this context.

Ok so now we can start creating a simple scenario where you can configure your webpage to send data to Oracle Cloud

1. Go to the directory  /var/www/html. _cd /var/www/html_
2. Create a new index.html file. _touch index.html_
3. Edit the file and create a simple HTML page. _vim index.html_

I'll use the code bellow:

<html>
<head>
<title>Hello APM</title>
</head>
<body>Hello APM</body>
</html>

4. After the configuration of your index page, refresh your browser to see if you are able to see your web page.

Now let's configure our page to be able to send data to APM service:

1. Inside the <head></head> tag we will create two scripts tag to import the agent to our code, this tags can be found at: https://docs.oracle.com/en-us/iaas/application-performance-monitoring/doc/deploy-browser-agent-your-application.html

<script>
window.apmrum = (window.apmrum || {}); 
window.apmrum.serviceName='<APM Browser>';
window.apmrum.webApplication='<Webapp1, Webapp2, Webapp3, WebappN>';
window.apmrum.ociDataUploadEndpoint='<ociDataUploadEndpoint>';
window.apmrum.OracleAPMPublicDataKey='<APM_Public_Datakey>';
</script>
<script async crossorigin="anonymous" src="<ociDataUploadEndpoint>/static/jslib/apmrum.min.js"></script>

We will update the fields with the information about our environment:
	- '<APM Browser>': he service name value that you specify for your APM Browser agent. If you don't set a value, the default service name APM Browser is assigned;
	- '<Webapp1, Webapp2, Webapp3, WebappN>': is the web application value(s). Multiple values can be separated by a comma.
	- '<ociDataUploadEndpoint>':  is the Data Upload Endpoint value. It can be obtained from the APM Administration page. 
	- '<APM_Public_Datakey>':is the APM Public Datakey value that can be obtained from the Administration menu in the APM main page.

2. Save and refresh your browser
3. APM now must be collecting metrics from the web page that you created, refresh the page again, try accessing it from another browser to generate more events on the APM page.

Now we can go back to APM service to see the data that was generated.




