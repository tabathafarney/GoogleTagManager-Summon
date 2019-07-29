# GoogleTagManager-Summon

# Implementing Summon Google Tag Manager (GTM) Container

## Purpose
To provide a base GTM container for libraries using the Summon \(v2\) discovery service. There are two versions of a Summon GTM container:
* **GTM\-Summon\-Standard\.json**: Adds pageview tracking and several click based events (user actions) for a Google Analytics account\. Here is an [Example GTM Summon Standard Report in Google Data Studio](https://datastudio.google.com/open/11XG44s5N_F4JbOXl6Zh_h5n_BqIateMW) so you can preview some data this container provides. **NOTE:** GDS doesn't work well in Internet Explorer or Edge. 
* **GTM\-Summon\-Advance\.json**: All the tags in Standard(v1) container with the addition of custom dimensions being pushed in several event tags. To fully use this container, you will need to set up custom dimensions in your Google Analytics account\. Here is an [Example GTM Summon Advance Report in Google Data Studio](https://datastudio.google.com/open/1zMM4vJQ05U-F0AB3cZkFQRIRun4FmG92) so you can see the use of the custom dimensions. **NOTE:** GDS doesn't work well in Internet Explorer or Edge. 

See the [GTM-definitions spreadsheet](https://docs.google.com/spreadsheets/d/17hoq4iaxnwX5p5o5KX5_BD_EKqfNW7mc8puCeZhlpF0/edit?usp=sharing) for all the events being tracked\.

You can add your own tags to these containers to further customize it to your library's data needs. 

## Importing and Configuring GTM for Summon
1. Down the either the GTM-Summon-Standard.json or GTM-Summon-Advance.json file.
2. Create a new GTM account. Anyone with a Google Account can do this at https://tagmanager.google.com
If you are new to GTM, you need to first create a GTM account and then create a GTM container within that GTM account. Select the Web option when you create the container.
3. Go to the Admin area of your GTM container. Click on Import Container.
4. Click on the Choose Container File option and select the GTM Summon JSON file on your computer.
5. Select Existing workspace and select Default workspace.
6. Select the Overwrite import option since you are using a new GTM container that contains no tags.
7. Click the Confirm button.
8. To continue to customize the GTM container for your Summon installation, go to the Variable section in your GTM container and click on the **Google Analytics Variable - UPDATE ME** in the User-Defined Variables section.
9. Remove the default Google Analytics tracking id number (UA-xxxxxx-x) and add your library’s Summon Google Analytics tracking id number and save the tag.
   * **Recommendation:** If you are testing this GTM container, it is recommended to create a new Google Analytics property (UA-xxxxx-xx) that is different from the current GA property used to track Summon usage. This allows you to compare your current GA configuration with this GTM configured GA set up. You can have two different GA properties on one website. 
10. Scroll up to the Built-in Variables section and click the Configure button. Check mark the following built-in variables to enable them:
    * Click Element
    * Click Classes
    * Click ID
    * Click URL
    * Click Text
    * New History Fragment
    * Old History Fragment
    * New History State
    * Old History State
    * History Source
11. Click the Submit button to publish your changes in your GTM container.

## Enabling Custom Dimensions in Google Analytics (GTM-Summon-Advance.json option only)

A custom dimension is any data point you want to send to Google Analytics so you can associate that data with pageviews, user, or even event data. A good example of a custom dimension would be content type or item title.

**You must be an admin for the Google Analytics property to create custom dimensions.**

The GTM-Summon-Advance.json uses three custom dimensions:


Google Analytics Index Number | Custom Dimension Name | GTM User Defined Variable
----------------------------- | --------------------- | -------------------------
1                             | content type          | Content Type - Item Title - Variable ; Content Type - Secondary Links - Variable
2                             | result position       | Result Position Variable
3                             | item title            | Item Title Variable ; Item Title - News Results - Variable ; Item Title - News Results Brief - Variable

Google Analytics assigns the Index Number sequentially as you create them. If you haven’t created a custom dimension in Google Analytics, the first one you create will have the Index Number of 1.

To create a custom dimension within Google Analytics:
1. Login into Google Analytics and go to the Admin area of your Google Analytics property
2. Expand the custom definitions option under the Property column.
3. Select Custom Dimensions
4. Click + New Custom Dimension button.
5. Name the custom dimension. For example: content type
6. Keep the scope to Hit and keep the Active checkmarked.
7. Click the Create button.
8. Google Analytics will assign a number to that custom dimension.
9. Repeat this process to create custom dimensions for result position and item title.

If you already have custom dimensions or don’t use the exact numbering used in the GTM-Summon-Advance.json, you can create your custom dimensions in Google Analytics and then modify the following GTM tags with your correct Index Numbers:
* Export Citation Tag
* Item Interaction Tag
* Link Click Tag
* Resource Outbound Link Tag
* Resource Outbound Link 2 Tag
* Resource Outbound Link - News Results - Tag
* Resource Outbound Link - News Available Results - Tag

## Installing GTM on Summon
Currently GTM is not a default feature in the Summon Admin console, but you can load it via a javascript file using the Summon 2.0 External Script option.

There’s a sample JavaScript file (add-gtm-summon.js). You will need to edit the script to add your GTM container tracking id number (GTM-xxxxxx).

Once the script is installed, you should be able to login into GTM container and click the Preview button. Refresh your Summon website and you should see the the GTM preview window pop up at the bottom of your browser.
