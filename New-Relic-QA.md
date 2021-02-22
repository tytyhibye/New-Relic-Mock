## New Relic Mock Q & A

```
Customer opens ticket for assistance under New Relic Platforms’ Installation/Integration category
```
<br/><br/>
Hey there,<br/>
I see you’ve opened a ticket for assistance with installing and integrating the New Relic platform. First and foremost, welcome to New Relic! I’d love to help you get this set up, how can I be of assistance today?
  <br/><br/>


Optimistically, <br/>
Tyler Bates<br/>
<hr/><br/>
Hi Tyler,<br/>
Thanks for getting back to me. Here's the situation: I followed the guide for injecting the platform but am not seeing any data come through on my dashboard. The application is listed under the gcp section of the infrastructure tab but the graphs are all silent. I'm trying to monitor firebase hosting.<br/><br/>
Halp,<br/>
Jimmy Pesto
<br/>
<hr/>
<br/>
 

Hey Jimmy,<br/>
I'm sorry to hear about the trouble you're having, let's see what we can do together to get this working. Since you're looking to monitor firebase hosting let's go over your Google Cloud Project's [IAM permissions](https://console.cloud.google.com/iam-admin/iam "I believe in you!") first and look at a few things:<br/><br/>

* From following the steps to [add a GCP project](https://one.newrelic.com/launcher/infra.infra?platform[accountId]=3056649&platform[timeRange][duration]=3600000&pane=eyJuZXJkbGV0SWQiOiJpbmZyYS5ob3N0cyIsImZlYXR1cmUiOiJzeXN0ZW0ifQ "Just in case you need a refresher!") you should see a project member added with an email address ending with:
```
@newrelic-gcp.iam.gserviceaccount.com
```
* This member should be assigned two roles: ***Viewer*** and ***Service Usage Consumer***<br/><br/>
* Let's add a third role titled ***Firebase Hosting Viewer*** and click save.
<br/><br/>

Additionally, let's head over to Google Cloud Platform's [API's & Services](https://console.cloud.google.com/apis/dashboard "You got this!") page to ensure we've enabled the<br/><br/>
<img src="https://i.ibb.co/FW4jtVs/Stackdriver.png"><br/><br/>
This is a necessary component for New Relic to access your firebase hosting data, more info on the access requirements can be found [here](https://docs.newrelic.com/docs/integrations/google-cloud-platform-integrations/get-started/connect-google-cloud-platform-services-new-relic "You're doing great!").
<br/><br/>
Once these changes have been implemented it should only take a few minutes for the platform to begin displaying information from your application. I hope this helps and please don't hesitate to let me know if there's anything else I can help you with.
<br/><br/>

Encouragingly,<br/>
Tyler Bates
<hr/>
<br/><br/>
Tyler,<br/>
Thank you for the info. I added the additional role and enabled the API (don't know how I missed that one) but I'm still having trouble locating the displayed information. I'm not seeing it in the integrations or in any of the dashboard metrics.<br/><br/>

Thanks,<br/>
-Jimmy Pesto
 <hr/>
 <br/><br/>
 Hey Jimmy,<br/>
 It looks like your application is linked correctly and I'm happy to help you find some of the data coming in. Let's head over to the GCP section of the Infrastructure tab. Once you see your linked project you'll notice on the top right there are three links. What you're looking for is the center link labeled:<br/><br/>
 <img src="https://i.ibb.co/xLdnmNj/status.png"><br/><br/>
 Follow this link and you'll see that the Stackdriver Monitor API is indeed pulling down data from your hosted site (hooray!). Here's a screenshot of what I see for your application:
 <br/><br/>
 <img src="https://i.ibb.co/LgzPRfg/dashboard.png">
 <br/><br/>
The data fields attached to your application's hosting are dependent on the traffic and usage of the application itself. So even though there's not much to show now those numbers will gradually increase over time.

Here's some [additional documentation](https://docs.newrelic.com/docs/integrations/google-cloud-platform-integrations/gcp-integrations-list/google-cloud-firebase-hosting-monitoring-integration "You did a great job!")</a> to help get you more comfortable with querying the data coming in from Firebase.
<br/><br/>
Great job implementing the platform and thanks for using New Relic!
<br/><br/>
Fondly,<br/>
Tyler Bates