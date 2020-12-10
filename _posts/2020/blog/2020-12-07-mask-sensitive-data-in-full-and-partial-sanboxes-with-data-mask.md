---
title:  "Mask sensitive data in full and partial sandboxes with Data Mask"
excerpt: Use Data Mask, a Salesforce platform-native obfuscation to mask sensitive data in any full or partial sandboxes.
date:   2020-12-07 00:00:00 +0100
categories: blog
toc: true
toc_label: On this pages
toc_sticky: true

header:
  teaser: assets/images/2020/blog/mask-sensitive-data-in-full-and-partial-sanboxes-with-data-mask/mask-sensitive-data-in-full-and-partial-sanboxes-with-data-mask-header.jpg
  overlay_image: assets/images/2020/blog/mask-sensitive-data-in-full-and-partial-sanboxes-with-data-mask/mask-sensitive-data-in-full-and-partial-sanboxes-with-data-mask-header.jpg
---

## Intro

Data mask is a Salesforce feature that uses platform-native obfuscation to mask sensitive data in full and partial Sanboxes. Bellow we are going to configure in a Sandbox and do a basic configuration.

## Install the Data Mask managed package
We are going to do the configuration in production, then everytime we create or refresh a full or partial Sandbox, the package and the configurations will be in the Sandbox.
The first step is to install the managed package that is going to provide the tools to perform the data masking. Go to the following link and install the managed package:
[Data Mask managed package link](https://sfdc.co/datamask-install){:target="_blank"} 

After you install the package, Salesforce will upgrade the package with future versions.

Set the following permissions to the user:
- System Administrator profile (Modify All Data and API Enabled user permission)
- Assign Data Mask permission set license
- Assign Data Mask permission set

**Note:** If you want to use an existing Sandbox, you have to replicate this configuration there
{: .notice--info}

## Data Mask Configuration app
Now you will have available the DataMask configuration app to administer your mask configs
![Data Mask App](/assets/images/2020/blog/mask-sensitive-data-in-full-and-partial-sanboxes-with-data-mask/2020-12-10-11-34-14.png)
When we create or edit a mask configuration we can see two sections:
- **Settings**: where we can **Anonymize Case Comments**, **Delete All Email** and **Delete All Chatter**
- **Objects & Fields**: List of objects where we can apply masking rules
![New mask configuration](/assets/images/2020/blog/mask-sensitive-data-in-full-and-partial-sanboxes-with-data-mask/2020-12-10-11-38-46.png)

For Account object, for instance, we can do several things:
- Run in Serial Mode: To avoid lock problems with object relationships (UNABLE_TO_LOCK_ROW or "unable to obtain exclusive access")
- Data Filter: It is possible to configure a filter where the masking configuration will apply
- Quick Find box: To easily locate the fields to configure.
- Fields: Depending on the field we have several options

## Actions for different field Types

### Number

The actions are Replace with a Random Value or Delete. You can specify the min and max value for the random values

![Number field](/assets/images/2020/blog/mask-sensitive-data-in-full-and-partial-sanboxes-with-data-mask/2020-12-10-12-00-12.png)

### Date/Datetime

The actions are are Replace with a Random Value or Delete. You can specify the Earliest Date and Latest Date values for the random value
![Date field](/assets/images/2020/blog/mask-sensitive-data-in-full-and-partial-sanboxes-with-data-mask/2020-12-10-12-02-45.png)

### Text

You can select if the field have to be Unique. The actions are:

- Replace with Random Characters
- Replace from Library: We can select a library with random values: Name, Fullname, Street, City, Postal Code...
- Replace using pattern: We can use a pattern expression using the following rules:
  - Max Generated Data Length 20 characters 
  - Use '%c' for a random lower case letter
  - Use '%C' for a random upper case letter
  - Use '%%' for a '%'
  - Use '%d' for a random digit
  - Use '%nd', '%nc, or '%nC' for n random letters or digits.
  - Any other character will be included as is
- Delete
![Text field](/assets/images/2020/blog/mask-sensitive-data-in-full-and-partial-sanboxes-with-data-mask/2020-12-10-12-07-48.png)

Once we have our mask configuration ready, we can run our mask job.

## Run Data Mask Job

From the configuration list we can click on the down arrow and then Run. Our job will be scheduled. We can verify the process in the Data Mask configuration list:
![Data Mask Status](/assets/images/2020/blog/mask-sensitive-data-in-full-and-partial-sanboxes-with-data-mask/2020-12-10-12-37-46.png)
You can see in Apex Jobs many jobs related with the Data Mask, once your job is running it will perform in an asynchronous way, you can stop from the down arrow when you want. Depends on your data size the job can take several hours.

Data Mask **disables the following automations** during execution:

- Triggers
- Workflow Rules
- Validation Rules
- Flows
- Field History Tracking
- Feed Tracking

## Verify the Job Execution

Once the job is finished. We can view in the job list the Last Ran date time in the status field.
![Data Mask Status Finished](/assets/images/2020/blog/mask-sensitive-data-in-full-and-partial-sanboxes-with-data-mask/2020-12-10-13-24-26.png)
In the "Run Logs" tab under the Data Mask app we can verify all the steps of the process.
