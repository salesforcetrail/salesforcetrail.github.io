---
title:  "Salesforce Lightning Timeline Component"
excerpt: See related records of any object as a timeline (similar to to the standard activity timeline)
date:   2020-12-02 00:00:00 +0100
categories: blog
toc: true
toc_label: On this pages
toc_sticky: true

header:
  teaser: assets/images/2020/blog/salesforce-lightning-timeline-component/timelinecomponent-header.jpg
  overlay_image: assets/images/2020/blog/salesforce-lightning-timeline-component/timelinecomponent-header.jpg
---

## Intro

This Salesforce Lab lightning component allos you to see related records of any object as a timeline (similar to to the standard activity timeline).

## Component Highlights

- Timeline view for any object: Standard component only shows tasks/events and emails. This component can display any related object to an object.
- Clicks / No code: Driven through custom objects and a Flow to guide you through the configuration options.
- Customize icons, what fields to use for title, date and fields to display.

## Installation

The first thing is to install the component from the AppExchange.

Find in AppExchange the Lightning Timeline Component. You can find it [here](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3A00000G0yN3UAJ){:target="_blank"}
![AppExchange Lightning Timeline Component](/assets/images/2020/blog/salesforce-lightning-timeline-component/salesforce-lightning-timeline-component-appexchange.png)
Click on "Get it Now" and Install, login and select your Salesforce account:
![Select Your Salesforce Account](/assets/images/2020/blog/salesforce-lightning-timeline-component/salesforce-lightning-timeline-component-login.png)
In the following screen click on "Confirm and Install"
Agree the license terms and proceed with the installation.
Validate again in your org, and the installation screen will be shown. Select the installation type, in our case for all the users, and click on install.
![Timeline Component Install Screen](/assets/images/2020/blog/salesforce-lightning-timeline-component/salesforce-lightning-timeline-component-install.png)
Verify in > Setup > Installed Packages that the component is installed:
![Component Install Verification](/assets/images/2020/blog/salesforce-lightning-timeline-component/salesforce-lightning-timeline-component-verify.png.png)
Now we have the component installed in our org. Let's go to configure and use it!!
## Playing with the Timeline Component
In your application find the Timeline object. And go to Timeline Configurations Screen:
![Timeline Configurations Screen](/assets/images/2020/blog/salesforce-lightning-timeline-component/salesforce-lightning-timeline-component-timelineconfig.png)
Create a new one, specifying the object and save:
time![](/assets/images/2020/blog/salesforce-lightning-timeline-component-selectobject.png)
Here we start with the configuration flow, it is showing up that the timeline configuration is for the Account object, click on "Next"
![](/assets/images/2020/blog/salesforce-lightning-timeline-component/2020-12-03-07-18-50.png)
Select the related object type, we selected Case, go to "Next", and after that take the Title field, for Case it makes sense to get the Subject field:
![](/assets/images/2020/blog/salesforce-lightning-timeline-component/2020-12-03-07-22-09.png)
This component order the records in a reverse way based on a date field, here you have to select the field for this object type:
![](/assets/images/2020/blog/salesforce-lightning-timeline-component/2020-12-03-07-22-53.png)
In the component several fields will be shown, here you have to select the fields to show:
![](/assets/images/2020/blog/salesforce-lightning-timeline-component/2020-12-03-07-24-01.png)
Choose the icon to apply for the cases:
![](/assets/images/2020/blog/salesforce-lightning-timeline-component/2020-12-03-07-25-09.png)
Apply a filter criteria, if you want
![](/assets/images/2020/blog/salesforce-lightning-timeline-component/2020-12-03-07-25-57.png)
Review your configuration and confirm
![](/assets/images/2020/blog/salesforce-lightning-timeline-component/2020-12-03-07-26-29.png)
Click on Finish
![](/assets/images/2020/blog/salesforce-lightning-timeline-component/2020-12-03-07-26-56.png)
Now you have your TimelineConfiguration record for use

I added another related object (Opportunity) to show several types of records mixed in the component:
![](/assets/images/2020/blog/salesforce-lightning-timeline-component/2020-12-03-09-48-17.png)

Now we can add this component to the Account flexipage. Go to one of the accounts and edit the page. Find the Custom-Managed component "Activity Timeline". 

Provide the information to configure the component:
- Record Id or Name of the Timeline configuration to use: Here provide the automatic name genrated in the configuration.
- Check to display header: Mark if you want, and provide a header title.
- Header Icon: Based on SLDS Icons
- Magin styling, you can find the link with the reference in the config help for the field.

Here is our configuration:
![](/assets/images/2020/blog/salesforce-lightning-timeline-component/2020-12-03-10-03-53.png)

After that, we can see our component mixing Cases and Opportunities in the same view in a timeline basis. As you can see in the following image, it is possible to perform filters by date and object type:
![](/assets/images/2020/blog/salesforce-lightning-timeline-component/2020-12-03-10-06-24.png)

The display fields selected in the configuration for each object type are displayed when you expand the left arrow next to the icon:
![](/assets/images/2020/blog/salesforce-lightning-timeline-component/2020-12-03-10-14-52.png)

And that's all, is a good component with many configuration options if we have to mix several types of related records in a timeline basis.
