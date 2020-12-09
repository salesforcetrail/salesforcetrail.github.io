---
title:  "Enable Source Tracking in Sandboxes"
excerpt: Dev and DevPro Sandboxes can automatically track changes between the org and the local development workspace (Beta)
date:   2020-12-02 00:00:00 +0100
categories: blog
toc: true
toc_label: On this pages
toc_sticky: true

header:
  teaser: assets/images/2020/blog/enable-source-tracking-in-sandboxes/enable-source-tracking-in-sandboxes-header.jpg
  overlay_image: assets/images/2020/blog/enable-source-tracking-in-sandboxes/enable-source-tracking-in-sandboxes-header.jpg
---

## Intro

Now, as a Beta feature, you can enable source tracking in Sandboxes: Dev and DevPro versions. This will allow you to track the configuration changes easily. This feature is in Beta, then use this feature at your sole discretion, the termns and restrictions are available [here](https://help.salesforce.com/articleView?id=sfdx_setup_enable_source_tracking_sandboxes.htm&type=5){:target="_blank"}

## How to Enable the Source Tracking for Dev and DevPro Sandboxes

In your production org go to > Setup > Dev Hub, then select "Enable Source Tracking in Developer and Developer Pro Sandboxes"
![Enable Source Tracking](/assets/images/2020/blog/enable-source-tracking-in-sandboxes/2020-12-09-10-34-47.png)

After enabling it, new created or refreshed Developer and Developer Pro Sandboxes will have activated the Source Tracking.

**Note:** If you clone a Sandbox without the Source Tracking activated, it won't be available in the cloned org, only for new orgs or cloned from orgs with the feature enabled.
{: .notice--info}

## Work with Source Tracking in a Sandbox

### Check the alignment between Sandbox and Working directory

First, make several configuration changes in your Sandbox. To check what changes are in place

```bash
cd MyProject
sfdx force:source:status -u sbxalias

You see that a list of changes posted to output:

STATE                     FULL NAME      TYPE         PROJECT PATH
─────────────             ─────────      ─────────     ───────────────────────────────────────────────────
Local  Deleted            Class1 .      ApexClass    /Class1.cls-meta.xml
Local  Deleted            Class1 .      ApexClass    /Class1.cls
Remote Deleted            Class2        ApexClass    /Class2.cls-meta.xml
Remote Deleted            Class2        ApexClass    /Class2.cls
Remote Changed (Conflict) Class3        ApexClass    /Class3.cls-meta.xml
Remote Changed (Conflict) Class3        ApexClass    /Class3.cls
```

### Pull changes from the Sandbox to your working directory

With the pull you place in your local directory only the files that changed:
```bash
sfdx force:source:pull -u sbxalias
```

### Push changes from your working directory to the Sandbox

With push you place in the Sandbox the changes made locally
```bash
sfdx force:source:push -u sbxalias 
```

**Note:** You can continue to use force:source:retrieve and force:source:deploy to synchronize your Sandbox with your working directory, but with Source Tracking enabled it will manage it automatically for you.
{: .notice--info}