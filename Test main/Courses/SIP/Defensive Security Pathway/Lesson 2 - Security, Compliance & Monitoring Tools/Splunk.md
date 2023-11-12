# What is Splunk

![Screenshot 2022-08-05 at 15-24-25 Wix.com.png Thumbnail](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://cdn.fs.teachablecdn.com/ubAg5jWgQU2iWV5v4Kty)

Splunk is a software platform to search, analyze and visualize the machine-generated data gathered from the websites, applications, sensors, devices etc. which make up the IT infrastructure and business.

It is not only used for security; it's used for data analysis, DevOps, etc. But before speaking more on Splunk. let's see, what machine data is.

Machine data is the information automatically generated by a computer process, application, or any other mechanism without the active intervention of a human.

It takes any DATA from ANY source, like:

1. Computers
2. Network devices
3. Virtual machines
4. Internet devices
5. Communication devices
6. Sensors
7. Databases
8. Logs
9. Configurations
10. Messages
11. Call detail records
12. Scripts
13. Changes
14. Tickets
15. Email Servers
16. Security Appliances
17. Voice mail servers
18. Point of Sale servers

and many more custom data collection options from any environment is possible.

Splunk enables organizations to gain operational intelligence for IT, Security and business - delivering real-time insights and business value from machine data that is needed to drive digital transformation.

Assume a scenario, where you have to find a "Transaction Failure".

Now with the lack of operational intelligence it will lead to high time consumption and resource usage but with Splunk an operator can easily search and come up with the solution.

In cyber security context, you will be able to Automate threat detection using machine learning so you _can_ spend more time hunting with better alerts for quick resolution.

# Functions of Splunk

![Screenshot 2022-08-05 at 15-31-00 Wix.com.png Thumbnail](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://cdn.fs.teachablecdn.com/mZaBavSRGd9iAT1jSWJw)

**Index Data:**﻿

The Index collects data from virtually any resource. Basically the data generated by any machine is always in it's raw form. This function inspects the raw data collected from the whole infrastructure and then with finding a suitable match, it labels it as source type. Now as the data is indexed into the Splunk as a particular database, let's take a look at what you can do with it.

  
**Search & Investigate:**

By entering a query in Splunk search bar, you can find events that contain values across multiple data sources. It allows you to analyze and run statistics on the events using Splunk Search Language. So as you can Search & Investigate anything from the specified database, what if you can add notes.

  
**Add Knowledge:**

The Add Knowledge function in Splunk allows you to add classification and enrichment, to normalize the searched data and save notes to make use in later searches or while generating reports.

  
**Monitor & Alert:**

Splunk can monitor any organizations infrastructure in real-time. You will be able to identify issues, problems,and cyber attacks before they impact their customers and services. Also you can create alerts for specific conditions and also automate actions regarding them.

  
**Report & Analyze:**

It allows you to analyze all the information to a single dashboard, while making it easy to read for everyone in an organizational environment.

Next we will learn about how the Splunk Processing Components works.

# Deploying Splunk

![Screenshot 2022-08-05 at 15-37-35 Wix.com.png Thumbnail](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://cdn.fs.teachablecdn.com/czPpOAikT2mXqtJJQuh2)

_Note: You have to follow along, if you wish to complete this module._

1. Go to [splunk](http://splunk.com) and signup using a temp mail.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/fRAcqXB5TciTouQXKHwn)  

2. Click the Free Splunk button in the top right corner and click on "Access Free 14 Days Trail"

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/dMfdoheRwGg63Qwjgvbw)

3. Start the free trail and you will receive a new set of username and password to access the cloud architecture. Note them down for further use.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/O0MmBfvUTtuwnNuDeyMI)

4. Sign in to Splunk Cloud Dashboard using the new details. once done with process, you will see the dashboard.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/bwMwwapNTPCkAvYq5hKN)

  

  

# Splunk Processing Components

It has 3 main components:

1. Indexers
2. Search Head
3. Forwarders

## Indexers:

Indexers index data and creates a lot of directories based on age(time) and source type. When you search data by time Splunk will only need to search the data that meets the time frame of your search, making it more efficient.

##   
Search Head:

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/KamqifT2Tzu8pzhUcUrX)

  

The Search Head allows the users to use the Splunk Searching Language to search the index data. Search Head handles the search request.

  

Let's see it through an example:

Assume you are a Splunk operator and you are asked to find out the total number and details of successful purchases in a database. How this can be done?

Well, you have to provide this command to Splunk search bar:

> Source=database_name action=purchase status=200

So what happens, after you run the command?

1. Search Head goes to indexers(where all the databases exists) and looks for the database_name and within it searches for purchased items with a 200 HTTP request response.

2. The enriched data is sent back to Search Head.

3. And, it is presented to the User i.e. operator.

  
Search Heads also provides the user with the following:

1. Dashboard
2. Reports
3. Visualizations to assist the search experience.

  

## Forwarders:

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/DodTgwMeSZSER5zdFJya)

  

Organization instances that consume data, forwards it to indexers for processing. Splunk Forwarders has some benefits such as they require minimal resources, have little impact on the performance, resides on the machine from where the data is originated.

  
In the next step, we will learn **how to deploy** it. but before that you should know this:

There are two types of Splunk Instances:

1. **Single Instance** - Single Instance Deployment is perfect for 1) Proof of concept 2) Personal use 3) Learning 4) Might serve the needs of small organizations
2. **Fully distributed Instance** - In here, you can add more Indexers for better data processing and also cluster them for any use.

  

# Navigating Splunk

![Screenshot 2022-08-05 at 15-50-27 Wix.com.png Thumbnail](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://cdn.fs.teachablecdn.com/qnfW8ffSTYChtBH3xUbg)

When you access Splunk, you will see the default home screen identical to the screenshot below.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/sjB5TpuQRxmAsKGRBQjZ)

  

Let's look at each section, or panel, that makes up the home screen. The top panel is the **Splunk Bar** (below image).

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/MoROkJArS8iDjafGXvQC)

### **Splunk Bar:**

1) You can see system-level messages (**Messages**),

2) Configure the Splunk instance (**Settings**),

3) Review the progress of jobs (**Activity**),

4) Miscellaneous information such as tutorials (**Help**),

5) And a search feature (**Find**).

The ability to switch between installed Splunk apps instead of using the **Apps panel** can be achieved from the Splunk Bar, like in the image below.  

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/onOAJ4UWS2C9RPsBdTje)

### **Apps Panel:**

In this panel, you can see the apps installed for the Splunk instance. The default app for every Splunk installation is **Search & Reporting**.  

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/120jSCoNS7WlWbvKtCEq)

## **Explore Splunk:**

This panel contains quick links to add data to the Splunk instance, add new Splunk apps, and access the Splunk documentation.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/QecYbSiMTfKGekhkYLEH)

  

  

### **Home Dashboard:**

By default, no dashboards are displayed. You can choose from a range of dashboards readily available within your Splunk instance. You can select a dashboard from the dropdown menu or by visiting the **dashboards listing page**.

![](https://www.filepicker.io/api/file/GZrKRJXaStqjKFzRffK7)

  

You can also create dashboards and add them to the Home Dashboard. The dashboards you create can be viewed isolated from the other dashboards by clicking on the **Yours** tab.

You can read more here about [Navigating Splunk](https://docs.splunk.com/Documentation/Splunk/8.1.2/SearchTutorial/NavigatingSplunk).

# Getting Data In

The Splunk platform can **index** any kind of data. In particular, the Splunk platform can index any and all IT streaming, machine, and historical data, such as Microsoft Windows event logs, web server logs, live application logs, network feeds, **metrics**, change monitoring, message queues, archive files, and so on.

  

## Types of data sources in Splunk Cloud Platform

Splunk Cloud Platform provides tools to configure many kinds of data inputs, including those that are specific to particular application needs.

Splunk Cloud Platform also provides the tools to configure any arbitrary data input types. In general, you can categorize Splunk Cloud Platform inputs as follows:

- Files and directories
- Network events
- Windows sources
- HTTP Event Collector (HEC)
- Metrics

  

## Let's add some data for practice

To add data to the Splunk platform, access the Add Data page in Splunk Web by following these steps:

1. Log into Splunk Web, the Home page appears.
2. Click **Add Data** to access the Add Data page.
3. After you access the Add Data page, choose one of three options for getting data into your Splunk platform deployment with Splunk Web:

- Upload
- Monitor
- Forward

  

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/BGrXP4NTj20LWp2JiE5b)

  

## Upload

The Upload option lets you upload a file or archive of files for indexing. When you choose Upload option, Splunk Web opens the upload process page. For more details, see [Upload data](http://docs.splunk.com/Documentation/Splunk/8.2.3/Data/Uploaddata).

## Monitor

For Splunk Cloud Platform deployments, you can monitor files and directories with the HTTP Event Collector.

For Splunk Enterprise installations, the Monitor option lets you monitor one or more files, directories, network streams, scripts, Event Logs (on Windows hosts only), performance metrics, or any other type of machine data that the Splunk Enterprise instance has access to.

When you choose the Monitor option, Splunk Web loads a page that starts the monitoring process. See [Monitor data](http://docs.splunk.com/Documentation/Splunk/8.2.3/Data/Monitordata).

## Forward

If you have a Splunk Cloud Platform environment, using a forwarder is the most common method for getting data in. The Forward option lets you receive data from **forwarders** into your Splunk Cloud Platform deployment.

When you choose the Forward option, Splunk Web takes you to a page that starts the data collection process from forwarders. See [Forward data](http://docs.splunk.com/Documentation/Splunk/8.2.3/Data/Forwarddata).

##   
For our use case, we gonna use **Upload:**

We will be ingesting static data sources that cover 30 days.

*For this demo you will not see real-time data.

## Steps

Let's take a Scenario: You have recently joined the team at SaferInternetProject as a Splunk Administrator. And You have been asked to ingest data into your Splunk Enterprise instance for searching.

### Task 1: Download log files from the repository.

1. Open a new browser window and direct it to [http://splk.it/f1data](http://splk.it/f1data)
2. The file Splunk_f1_Data.zipwill be downloaded to your system.
3. Use an archive tool to unarchive the file.
4. Once unarchived, you will see a folder labeled tmp.
5. Inside the folder you will see three files.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/o1kTvEWiTkGb14NtAsSz)

  

Return to the browser window for your instance of Splunk Web or open a new one.

## Task 2:Ingest web application data into Splunk Enterprise.

7. Go to the Homeapp by clicking the SplunkEnterpriselogo in the upper left hand of the interface.

8. Click settings button from Splunk Nav bar

9. Click Add data

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/PoUxq47CSAKTOEMK8LcD)

10. From the Add Data page, click the upload button.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/PqZ2PUPRyONdsiL7iBYL)

  

11. You will be taken to the Select Source step. Click the Select File button and choose the **access_30Day.log** file that you downloaded and make sure you have already unarchived the zip folder.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/aCkAXFS8SlWHUPJeRDAy)

  

12. Once the file is uploaded, click the Nextbutton.

13. On the Set Source Type step, you will see that Splunk automatically set the source type correctly as **access_combined_wcookie**. Click the Next button.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/oxGYz1EHRsajVdN3lmnd)

  

14. From the Input Settings step, enter **web_application** as the Host field value and click the Review button.

15. You will be taken to the Review step. Make sure your settings match what is shown below and click the Submit button.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/HTVey1QWSOvhIqhmGwN6)

16. Splunk will process the file.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/yp3dLN1eRWveKiZURusg)

17. When completed, a dialog will appear telling you the file has been successfully uploaded.

  
  

Follow along the below lab from Splunk to get a hands on experience using the product!

![[SplunkFundamentals1_module5.pdf]]