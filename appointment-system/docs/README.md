# Appointment Booking System / Software

## Installation Guide
This document will guide you through the installation and configuration of application.

## Introduction
This is a web appointment scheduler that can be installed and run in web servers. Users will be able to reach the application through their web browsers by using an active internet connection, just like visiting a normal website. The installation process is very similar to other popular web systems like WordPress and Joomla, so it is very likely that you will be familiar with the next steps. Follow this article strictly in order to complete the installation with no problems. After that, read the "Configuration" section for adjusting the system to fit your needs.

## Installation
There are 6 steps you must follow during the installation process.

Make sure that your server has at least the following applications/tools installed: Apache(v2.4), PHP(v5.6) and MySQL(v5.7). This app needs these programs to run. Most of the web hosting companies provide these tools within their Linux hosting plans. If you want to install app on your local server use one of the pre-made bundles available on the web (XAMPP, MAMP, WAMP ...), all of which are free to use. If you plan to use the Google Calendar synchronization you will need the php_curl extension installed and enabled as well.
Create a new database (or use an existing one). The database is necessary for storing the system data. Therefore your hosting plan must include at least one MySQL database. You must also get the database administration credentials because they will be needed later on.
Upload the app source files to your server. You can place the files into a directory with named  "appointments" or "book" etc. Make sure that you mark the App folder URL because it will be needed in the following step. For example if the system files are placed in the this directory ".../httpdocs/appointment/" then the URL to this folder will be "http://your-domain.com/appointments". This URL will be needed in the following steps.
Ensure that the "storage" directory is writable. Session information, logs and any other kind of files will land into the "storage" directory so make sure that it has the correct permissions and that is writable.
Edit the "config.php" file and set your server properties. Like other web systems, This app needs to know how to connect to the database and the base URL of the installation. You can also provide the Google Calendar API keys in this file, if you want to use the Google Calendar Sync feature. NOTE that you will need to create an API key before that in the Google Cloud Console.
Open a web browser and head to the App installation folder URL. The first time you open this page an installation guide will be shown. Fill in the administrator user and company settings and press the "Install" button. That's it! You can now use the application at your own will.
Configuration
When you finish the installation, Appointment will only contain an administrator user, a test service, a test provider and some default settings. You will need configure the system with your own business logic, but before that you can try adding a test appointment before proceeding with the following steps.

Head to backend section by entering the App URL http://installation-url/index.php/backend in your browser. When logged in, click on the "Settings" menu item on top of the page. Click on the "Business Logic" tab and apply the working plan of your company. Press the "Save" button when you are finished. This will be the default working plan for all new providers (not the existing ones).
Next you will need to add the services that your customers will book appointments for. You can optionally organize these services by using custom categories. Add some records and make sure you fill the required fields.
Once you are ready with the services you will need to add the service providers of your company. By doing so, customers will be able to select the employee they want to provide their preferred service, during the booking procedure. Hit the "Users" menu item and then the "Providers" tab. Add a new provider user and set his working plan and services. If you wish to assign the appointments without using app just create a single general provider user named with your company name. It is not necessary for the provider to know the login credentials, but if he does, he will be able to view his appointment plan and sync it with his Google Calendar account.
If you have a secretary handling all the appointments for your company, hit the "Secretaries" tab and add a new user. Select the providers that she can manage and save the record. The secretary user will be able to manage the appointments only for the providers she is responsible.
That's it! Click on the "Go To Booking Page" link on the footer of the page and create a new appointment. The new appointment will be now be visible at the "Calendar" page of the backend section. The customer's data have also been saved and can be found in the "Customers" page.
Finally just add a link in your website that points to your App installation with a caption similar to "Book Appointment". Whenever a customer clicks on that link he will be redirected the booking page.





## Localization  / Translation

App supports the addition of custom translations in order to display the user interface into many languages and therefore be more user friendly. This page will guide you through the addition of a new translation and the configuration of the application. You can also modify the available translations or even set the default one for the application.

Details
App is based upon CodeIgniter (PHP Framework) and it uses its build-in libraries in order to translate the content into many languages. Version 1.1 of the application comes with English, German, Greek, Hungarian, Portuguese, Spanish, Italian, Japanese, Dutch, French, Simplified Chinese, Polish, Danish, Luxembourgish, Slovak, Finnish, Russian, Romanian, Turkish, Hindi,Marathi and Bulgarian already included, but there is also the ability to add you own translation and change the user interface strings and captions. To add a new translation you must do the following:

CREATE A TRANSLATION FOLDER INSIDE "/APPLICATION/LANGUAGE/" DIRECTORY. If you want for example to translate the application into French then you will need to create a new folder named "french" inside the /application/language/ directory and copy the contents of the "english" folder. You must also copy the "migration_lang.php" file from another translation directory (e.g. "german") because CodeIgniter requires it when the version migration algorithm is executed.
TRANSLATE EACH STRING WITHIN YOUR "TRANSLATION_LANG.PHP" FILE INTO YOUR LANGUAGE. You will just have to replace the English strings with your translation. Example >> $lang['page_title'] = 'Write your translation here!';
TELL App THAT YOU HAVE ADDED A NEW TRANSLATION. When you are finished with the translation you will need to make some changes into the core config file of App located at "/application/config/config.php" in order to tell the application that there is a new translation available. Find line 90 and add your language to the array. Example >> $config['available_languages'] = array('english', 'german', 'greek', 'hungarian', 'portuguese', 'french');. Then change the default language, though this is optional (e.g.$config['language'] = 'english';).
Follow these steps in order to add or adjust your translations and modify the message of the user interface of App. 


## Google Calendar 


Customers will be able to sync their appointments with their Google Calendars but beforehand you will need an API key. Click again on the Create credentials button while being in the Credentials overview page and select API Key. A modal dialog will be shown asking you the type of key to create. Select the Browser Key option and fill the following form with your installation data.

App Syncing Feature
To enable the synchronization edit your root config.php file and update the Google Calendar Sync section with your API credentials.

GOOGLE_SYNC_FEATURE needs to be set to TRUE.
GOOGLE_PRODUCT_NAME needs to have the same name as the Google Cloud Console project.
GOOGLE_CLIENT_ID needs the client ID from the OAuth2 credentials.
GOOGLE_CLIENT_SECRET needs the client secret from the OAuth2 credentials.
GOOGLE_API_KEY needs the API key created in the previous section.
Link Google Calendar and App: Go to backend/calendar page, select a provider and click on the "Enable Sync" button. A new window will pop up asking you to grant concern. Enter the user's credentials and the sync will be activated!
Note that ...
Currently synchronization can only be triggered from the App backend or whenever there are changes in the appointment plan.

Every provider user can be synced with only one Google Calendar account.

Recursive events are not supported yet.


Useful Link ...
Google Developers – https://developers.google.com/google-apps/calendar




#### FAQ


How do I check that my server has Apache, Php and MySQL already installed?
App is a php application and needs an apache server with php and mysql installed. Apart from that, the php "curl" extension and the apache module "mod_rewrite" need to be enabled. To check if your server fullfils the needed prerequisites you will need to either contact the web hosting company or create a php file on your web root directory with the content <?php phpinfo(); ?> and then access it from the web (eg "phpinfo.php" >> "http://domain-name.com/phpinfo.php"). This url will display all the server details.

How do I create a Google Calendar API key?
Google needs to authorize the usage of her services, so you need to create an API key for your App installation. In order to do that you will need a google account. When logged in, go to the Google Developers Console and create a new project. Enable the Calendar API service and then head to the "APIs & Auth >> Credentials" menu item. There, you will need to create a new OAuth client id. The last step is to enter a valid redirect url for the authrorization process. This is very important because if the redirect url is wrong, you will not be able to use the google synchronization feature on your E!A installation. For your redirect url enter the following value: "http://domain-name/folder-to-ea-installation/google/oauth_callback" (replace the domain name and the path to the App installation folder with your server values). For example if E!A is installed on the "ea" folder on the web root directory the valid redirect url would be "http://my-domain/ea/google/callback".

Installation Page Is Not Working
Various users have reported on the support group that they cannot complete the installation successfully. This is primarily because of two reasons (a) either the configuration.php file was set incorrectly, or the server settings won't allow AJAX calls to be completed successfully and thus let the installation finish. For the first situation you will have to check that you have properly set the $base_url parameter to "http://url-to-ea-folder/" (last slash is necessary!),  Then ensure that your database connection credentials is correct. In the second situation the things are more complex. Users have stated that in some web hosts you need to change the .htaccess file in order for the application to work (htacces snippet provided below). If this doesn't work then check the apache error log and open the browser javascript console after you press the "Install E!A" button. There you will find information about what is going wrong with your installation. Contact your hosting company and ask them to resolve these issues.

```.htaccess```

```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php?/$1 [L]
```

## Booking Wizard Won't Display Any Hours

This issue comes when the customer is on the appointment book wizard but he is not seeing any available appointment hours and he cannot continue either. If your installation has this problem check the apache error log and open the browser's javascript console to find any issues. This is definetely a server issue and can only fixed by contacting your hosting company. It has to do with your server settings not letting App run correctly. Normally you or the web hosting company will be able to find what needs to be changed in order to solve the issue.

Booking Wizard Displays "There are no available appointment hours for the selected date. Please choose another date." ... Even though there are available time periods in my plan.

This is not actually an issue but it happened to a user and it was indeed confusing to resolve. A clean installation of E!A has some default settings such as the default working plan that contains some breaks too during the working days. This was set this way in order for you to see how can a working plan be like and set. So if you add a service that lasts for several hours (eg. 3~4 hours) then because of the default breaks new appointments will not fit in any empty time period of your calendar and thus the customer will not be able to book appointments with you. So if your services last for long you will need to change the working plan of your providers too so new appointments will fit into their schedule.

## Installing E!A on Subdomain Won't Load Appointment Hours

If you want to install App on a subdomain you will have to use the subdomain URL in your "configuration.php" file and not the initial URL directory. For example if you have the subdomain "http://book.mysite.com" where E!A resides and this subdomain is mapping on "http://mysite.com/book", you will have to set $base_url = 'http://book.mysite.com' in your "configuration.php" file, otherwise you will get a No 'Access-Control-Allow-Origin' error and you won't get any available appointment hours on frontend.

## Change the gap of the available hours of the booking wizard to 60 minutes (or similar).

The following link points to a common question that many users ask. The default gap between the available appointment hours is 15 minutes. In the following thread there is a file attached which will change this gap to 60 minutes.


DateTime::__construct(): It is not safe to rely on the system's timezone settings...
You get this warning because PHP is not configured with a timezone setting. This is a very important setting especially for App, cause otherwise you might get into trouble with the appointment hours. After installing the application, make sure that the php.ini "date.timezone" setting has the correct value depending your location. You can find a list of the available timezone setting on php.net. If you cannot modify your php.ini file try to add the following command at the top of index.php.

date_default_timezone_set('America/Los_Angeles'); // Use your own timezone string.




We hope the documentation will work for you. If you find any difficulties. Please contact us.

Thank You :)