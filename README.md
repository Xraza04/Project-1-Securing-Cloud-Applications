# Project-1-Securing-Cloud-Applications

URL of web application that was created: https://drazabytes.azurewebsites.net/

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/eb6e9817-5b6f-4bd2-8850-a6b6a030c7df)

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/b41a4d07-cabe-4486-aa85-d31900992c3c)

Part 1: Create an Azure Web App
In Part 1 of this activity, you will create your own Azure web application. You will name your application instance and select your back-end code and service plan. To do so, complete the following steps:


> Begin by logging in to the Azure portal: https://portal.azure.com.
    
> Select "App Services" from the Azure search field at the top of the page

> Select "+ Create" to create your application

Under the "Basics" tab, make the following selections:


> Subscription/Resource Group: Select the same subscription nd resource group that you used during Cloud week.


> Name: Name your instance as you see fit; note that this will be the name of the Azure app.

 
> Publish: Select "Code."

> Runtime Stack: Select "PHP 7.4." (There isn't 7.4 so Eli (TA) recommended trying 8.2)

>Operating System: Select "Linux."

>Region: Select the same region that you used during Cloud week.

The following image shows the completed "Basics" tab:

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/1dd478ac-0f71-4bd8-ae38-48ece01e98d8)


For the App Service Plan, complete the following steps:


> Under "Linux Plan," select "Create New" and then enter "project1plan."

> Under "Sku and size (AKA pricing tab)," select "Change size." 

> Select "Dev/Test" and "Plan B1", and then click "Apply," .

> Select "Create" at the bottom of the screen to create your web app.

> Once your app has been created, either select "Go to Resource" or find the app that you just created by selecting "App Services" from the Azure search field at the top of the page.

> Select your app from this page

> After selecting your app, a menu of available options should appear on the left-hand side of your app. Select "Custom domains," as the following image shows:

 ![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/8d8710bb-9c87-45b4-892e-1a3ce607a2db)


Once this new page opens, note that your unique IP has been created, as the following image shows:

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/faa1289e-1e37-43fb-a358-a7c6051d38cc)


**Note that upon creation of this app, Azure provides you with a free domain.**

> It begins with the name that you selected and ends with ".azurewebsites.net".

> Take note of this domain, as this will be your website for the remainder of Project 1.
If the domain doesn't appear, refresh your page.


**Part 2: Deploy a Container on the Web App**

In Part 2, you will use the Azure Cloud Shell to deploy a Docker container on your web application. This container contains the framework for your cyber blog webpage.


For your web application, you will use a Docker container that has been added to Docker Hub. 


Note that the Docker container image name is cyberxsecurity/project1-apachewebserver


Next, you will use the Azure Cloud Shell to deploy this container to your web application.

> Azure Cloud Shell takes user input from a command line to manage Azure's cloud resources.

> While we will use Bash, you can also use Powershell to administer your commands.

> To open Azure Cloud Shell, click the shell logo in the tool bar at the top of the screen, as indicated by the red arrow in the following image:

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/fc40b492-95dc-49b2-a9f3-20a80ab4927e)


Once you've clicked this icon, the Cloud Shell will be accessible at the bottom of your page.


When using Shell, you may receive the following prompts:

> Select which shell to use (Bash or Powershell): Select "Bash."

> Create Storage: If a window appears, select "Create Storage."


Next, from the command line, you'll enter a command to configure your container.


There are three types of commands that manage your web app container settings:


> (1) az webapp config container delete - This will delete your web app container's settings.

> (2) az webapp config container set - This will set your web app container's settings.

> (3) az webapp config container show - This will display the current details of your web app container's settings.


To configure your web app with your provided container, run the following: az webapp config container set --name <name of your webapp> --resource-group <name of your resource group> --docker-custom-image-name <container-name> --enable-app-service-storage -t


After pressing enter, an output similar to the image below should appear:

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/6925025d-9574-48d0-9ce9-90c0f69f9086)


To verify that the container has been added correctly, run the following command to show the container for your web app: az webapp config container show --name <name of webapp> --resource-group <name of your resource group>


**Part 3: Design Your Custom Web Application**


The container that you just loaded onto your web application is a framework for a cyber-blog page that you can customize.

You will now customize the following elements of the webpage:

> Your name

> Your email

> Your LinkedIn profile link

> Your introduction

> Your picture

> Two custom blog posts on topics of your choice


Once you have access, change directories to the location where the HTML files are located by running cd /var/www/html, as the following image shows:

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/6610ace5-ff7a-44fb-a7c3-c7a1f06cdab4)

> This directory contains the index.html file that makes up your webpage. To customize your webpage, complete the following steps:


**Day 2 Activity File: Secure Your Web Application with SSL Certificates (Azure Free Domain Version)**


Part 1: Create a Key Vault
In this first part, you will create an Azure key vault.

> Select "+ Create" from the Key Vault page to create your key vault

> On the "Create key vault" tab, make the following selections:

> Subscription/Resource Group: Select the same subscription and resource groups that you selected on Day 1.

> Key Vault Name: Choose a key vault name, such as drazabytes-KeyVault. (Note: This name must be globally unique, so you will be prompted to choose a different name if the one you enter has been used before.)

> Region: Select the same region that you selected on Day 1.


After your key vault has been created, select your new resource to view your new key vault.

 **Part 2: Create a Self-Signed Certificate**

In this second part, you will return to the command line to create a self-signed certificate using OpenSSL. 

From your Azure portal, access the same Cloud Shell that you accessed on Day 1 to load the Docker container, as the following image shows:

 ![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/e04ed5d6-db45-4260-aaa1-75cb0c093a4a)


From this command line, you will now use the open source cryptography and SSL/TLS "toolkit" OpenSSL (it is preinstalled).


Next, you will use OpenSSL to generate a self-signed certificate.

> The following image shows this step:

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/748413a6-084e-4c3b-86bd-6207c10cbd0b)


We added the following options:

> -x509: Indicates for OpenSSL to create an SSL certificate.

> -sha256: Uses the sha256 hashing algorithm.

> -nodes

> -days 365: States the certificate will be valid for one year.

> -newkey rsa:2048: Uses a 2048-bit RSA key.

> -keyout project1-key.key: The outputted name of the private key.

> -out project1-cert.crt: The outputted name of the certificate.

> -addext "extendedKeyUsage=serverAuth": Indicates how a public key can be used.


After pressing Enter, you will be asked several questions about your certificate.

> The following image shows this step:

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/5e5ecdf5-0fcd-4261-b6dd-3fcbd47c0bd3)

 
Now, view your newly created key (.key) and certificate (.crt) by running ls, as the following image shows:

 ![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/71076ad4-9d16-48a0-b3c6-41ae95bf2336)


The PFX format is the server certificate and the private key combined into a single encrypted file.

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/2407f0b3-25d3-48bb-92d9-3eff3f111fd7)

I added the following options:

> pkcs12: Indicates for OpenSSL to create a PFX certificate.

> -export -out project1-cert.pfx: States what to name the PFX file.

> -inkey project1-key.key: This is the current private key that you are importing.

> -in project1-cert.crt: This is the current certificate that you are importing.

After pressing Enter, you will be prompted for a password to encrypt your PFX key.


View your new PFX certificate by running ls, as the following image shows:

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/4e9bfb41-0379-4d28-9b6b-098ba7907429)


**Part 3: Analyze a Self-Signed Certificate**

In this part, you will use Azure to import and analyze self-signed certificates. To do so, complete the following steps:
From the Azure Portal, select "Key Vaults."


Select the key vault that you created in Part 1.

From your key vault, select "Certificates" and then "+ Generate/Import," as the following image shows:

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/ccd949c2-3785-4c40-a62c-61c84509fc15)


Select "Create" to upload your certificate.


The following success message should appear to confirm that your PFX certificate has been uploaded to your key vault:

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/b23e7de7-18ab-4857-94e0-ef53d34a07e6)



Let's examine this webpage's certificate. Click "Not secure" in the search bar if you are in Chrome, or a similar message depending on your browser, as shown in the following image:

 ![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/cdfae71c-d80d-420c-a181-e30f72d23330)

> Note the reason for the error based on the message on the certificate. This is due to the fact that the certificate was not created by a trusted CA—it would have been created by you.



**Day 3 Activity File: Protect Your Web Application with Azure's Security Features**

**Part 1: Create a Front Door Instance**

In this first part, you will create an Azure Front Door instance.

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/8a4ce05c-2fa6-4f5f-853c-bfcc91b2e2e2)

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/95b16f26-ff3d-45f3-b793-0b52c667689c)

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/013284cc-8d5c-425d-a1ca-460aa0b8d8d8)



**Part 2: Analyze WAF Rule Sets**

In this second part, you will view the features that are provided by your web application firewall. 

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/68884955-e325-45a7-9c98-28bfd99da402)


**Part 3: Configure Custom WAF Rules**

In this part, you will configure a custom WAF rule to protect against a potential security attack.
Let's assume for this project that you have been experiencing a variety of attacks from international IP addresses, and you need to only accept traffic from the locations where your business partners reside: the United States, Canada, and Australia.


Now, you'll learn how to create a custom rule on your web application to protect against these attacks.


![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/a2f277da-37dd-44d7-af31-b26394a3d045)


Your custom rule should now display on the page, as the following image shows:

 ![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/3b3fdabc-51ae-4ed7-80b6-9d561392f6bb)



**Part 4: Analyze and Fix a Defender for Cloud Recommendation**

Microsoft Defender for Cloud is a management system that provides best practices and recommendations to enhance the security of your cloud resources.

While Azure provides tools to protect your cloud resources, it is up to you to apply the correct configurations and best practices to protect your web application.


In this part, you will learn how to use Microsoft Defender for Cloud to analyze and fix a recommendation from the dashboard.

To access Defender for Cloud, from your web app, select "Microsoft Defender for Cloud" from the toolbar, as the following image shows:

 ![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/5db2859e-6432-4407-b732-ea49ca0863a5)


> When the Security page opens, it should display counts for both recommendations and alerts (note that your counts may vary).

![image](https://github.com/Xraza04/Project-1-Securing-Cloud-Applications/assets/107894378/41efcc89-a30e-439f-b33c-22fd91fa2fc5)


Review the recommendations, and note that Azure describes the recommendations in this way: "Defender for Cloud continuously monitors the configuration of your app services to identify potential security vulnerabilities and recommends actions to mitigate them."

⚠️ Important: Your security recommendations may vary, or may not show up at all. If there are no security recommendations, skip ahead to Part 5, and return in a few hours to complete this section. If you have any, most security recommendations will appear within 24 hours.
