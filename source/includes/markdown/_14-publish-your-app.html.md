<hr class="full-line">
<section class="full-section">
<section>

# Developer Sandbox

<span class="description">
An Asana developer sandbox consists of a temporary Asana domain with limited users. It is essentially a standard Asana account where you can test premium features during development.
</span>

#### Developer Sandboxes are intended for:
* Developers building or maintaining a 3rd-party integration with Asana (submit your completed integration to get listed on our apps page)
* Existing premium Asana customers that require a separate environment to perform risk-free testing on the API 

To request a developer sandbox, please fill out **[this form](https://form-beta.asana.com?hash=b9bca5d2a3ff59b9a7f82d29086e2d9bcd0df6fd306aa81bd96a63405d5948db&id=1113032351814260)**.

<div>
  <div class="docs-developer-satisfaction-content">
      <h4>Was this section helpful? <a class="positiveFeedback-DevSatisfaction" style="cursor:pointer;">Yes </a><a class="negativeFeedback-DevSatisfaction" style="cursor:pointer;">No</a></h4>
  </div>
</div>
</select>



<hr>
<section>
# API Explorer

<span class="description">
The Asana API Explorer is a tool to easily make API requests in your browser and quickly test various routes, fields, and parameters. 

The explorer is not meant to be an exhaustive tool with every endpoint in the API (try [Postman](/docs/using-postman) if you want a tool with complete coverage). Instead, the explorer is designed to be a simple tool to help developers quickly access the API and see examples of requests and responses fetching real Asana data.  
</span>

#### Follow these steps to get started:

1. Go to the API Explorer site: <a href="https://developers.asana.com/explorer" target="_blank">https://developers.asana.com/explorer</a>

2. Click the large button that says “Click to authorize API Explorer”. This will use your Asana credentials to provide cookie authentication for the requests you make in the explorer. Because the explorer is using your Asana account, it only allows read requests (i.e. `GET` only) to protect against unintentionally changing your Asana data.

3. Choose the resource you wish to query from the drop-down. 

4. In the next drop-down, choose your desired route for that resource. 

5. Under "Include Fields," You have the option to select only the fields you would like to include in the response (more about [I/O options](/docs/input-output-options)). 

6. The default response limit is 10. You can increase it up to 100.

7. Add the required “Attribute parameters”. Note that task and project gids are in URLs when viewing those resources in the Asana web product (e.g. when viewing a task in a project: https<nolink>://app.asana.com/0/'project-gid'/'task-gid'). 

8. In subsequent requests, you may have a pagination token (see the [pagination docs](/docs/pagination) for more on this) to paste into the “Offset” field.

9. You have the option to include additional parameters in your request.

10. Click “Submit” to send your request to the API. You will receive a JSON pretty-formatted response.   


<div>
  <div class="docs-developer-satisfaction-content">
      <h4>Was this section helpful? <a class="positiveFeedback-DevSatisfaction" style="cursor:pointer;">Yes </a><a class="negativeFeedback-DevSatisfaction" style="cursor:pointer;">No</a></h4>
  </div>
</div>
</section>


<hr>
<section>
# Submit your App

If you've built an application that you wish to share with the Asana community, you can visit the
[developer console](https://app.asana.com/0/my-apps) to begin the app submission process. 

By submitting an app for review, you'll have the opportunity to distribute your app publicly by listing
it in the [app directory](https://asana.com/apps) (as well as in the in-product [app gallery](/docs/installing-an-app)
for apps with [App Components](/docs/overview-of-app-components)).

### Submit for review

When managing your app in the [developer console](https://app.asana.com/0/my-apps), select **Submit for review**
in the sidebar to access the app submission form:

<img src="../images/submit-my-test-app.png" />

From there, you'll review an interactive "pre-flight" checklist of app features before submitting an app. This includes:

- Adding an app icon that uniquely represents your app
- Setting up [OAuth](/docs/oauth) by adding a redirect URL
- Adding app images that show what your app can do
- Adding a short description to summarize what your app can do at a glance
- Adding a longer description (at least 250 characters) to tell users about the features of your app
- Adding information about your company to build trust with users
- Adding a support page URL so that users can seek help
- Adding your app’s privacy policy URL

Along with building or providing the above features, you'll be able to submit additional app details through the submit form,
such as setup instructions, a screencast video link, and other listing details.

### App review process

Once your app has been submitted through the [developer console](https://app.asana.com/0/my-apps), the review process will
begin. At this point, the the app will no longer be open for further edits. Note that if your app uses
[App Components](/docs/overview-of-app-components), your submission will go through a security review and QA process
before it’s listed in the in-product [app gallery](/docs/installing-an-app).

You can track the status of your app submission on the same **Submit for review** page. If your app submission passes requirements,
you'll receive an email notification that your app is ready to publish. At this point, you can select the **Publish app** button in 
the developer console to share your app:

<img src="../images/approved-app.png" />

If your app submission doesn't meet requirements, you will receive communications regarding the next steps (i.e., any changes required)
to get your app ready for re-review.


<div>
  <div class="docs-developer-satisfaction-content">
      <h4>Was this section helpful? <a class="positiveFeedback-DevSatisfaction" style="cursor:pointer;">Yes </a><a class="negativeFeedback-DevSatisfaction" style="cursor:pointer;">No</a></h4>
  </div>
</div>
</section>

<hr>
<section>
# Managing your App

### Duplicating an app

You can quickly create a brand new app with the same configurations of an existing one by selecting **Duplicate app**
in the [developer console](https://app.asana.com/0/my-apps).

<img src="../images/duplicate-app.png" />

This feature can help streamline the creation and management of different versions (e.g., staging, beta, production, etc.)
of your application. As a result of this operation, the newly-generated app will retain the configurations of the original app,
including:

* Basic information (e.g., app name, descriptions, authentication URL, etc.)
* Configurations of App Components

Because the newly-generated app is its own unique app, the following _will not_ be carried over from the original app:

* App credentials (i.e., a new Client ID and Client Secret will be generated)
* Users who have completed OAuth
* Organizations in which the app is available
* Published listings in the [app directory](https://asana.com/apps) or [app gallery](/docs/installing-an-app)

<hr>

### Editing a published app

Developers have the ability to submit edits to a published app.

To begin the process, first [duplicate your app](/docs/duplicating-an-app):

<img src="../images/duplicate-app-modal.png" />

After duplicating the original app, provide any edits to any configurations as needed. 

When you are ready to [submit your app for review](/docs/submit-your-app), navigate to **Submit for review** in the
sidebar when managing your app. On the app submission page, select **I'm submitting changes to a published app** in
the **Submission type** dropdown:

<img src="../images/edit-published-app.png" />

Upon submission, your app will follow the standard review process. If the edits are accepted,
_the original (i.e., previous) app will reflect the new updates_, while the duplicate app can be used again for testing.

<hr>
# Custom Apps

#### What to consider when building a custom app


<span class="description">
Unlike 3rd-party apps and integrations used by many companies, custom apps are designed to only be used within a single domain. For example, an Asana customer may want to use the API to create a bot, integrate Asana with a homegrown tool, or generate custom reports. If you want to get inspired about what’s possible with custom apps, here are some [common use cases](/docs/common-usecases).
</span>

#### Authentication
Most custom apps use [Personal Access Tokens](/docs/personal-access-token) (PATs) for authentication. In general, PATs are best for projects that don’t require multiple users to log in. For example, it’s advisable to use PATs to auth scripts, bots, or anything else that doesn’t require taking action on behalf of multiple Asana users. While less common, if your custom app requires users to sign in to use it, then you should consider [using OAuth](/docs/oauth).  


#### API Explorer 
If you're unfamiliar with our API, it may be helpful to start by playing around with our [API explorer](/docs/api-explorer). It’s a quick and easy way to test endpoints and see how various parameters affect responses. You will also find guides and [code examples](/docs/examples) in our docs and client libraries that are helpful when getting started. 


#### Client Libraries
You should consider using one of our [API client libraries](/docs/official-client-libraries) for your custom app. They simplify some of the more technically challenging aspects of development such as authentication and pagination. There are code examples for each library to help you get started. The client libraries also help developers navigate [API deprecations](/docs/communicating-about-breaking-changes), which will help you avoid unexpected breaking changes and reduce the overall time required for maintenance. 

Note that client library functions are not documented. You need to check the `lib/resources/gen` folder of each library to see the built-in functions.  

#### API support 
If you get stuck or need help developing your custom app (or just want to meet other Asana developers), join our active [developer community](https://forum.asana.com/c/developersAPI/24). On the forum, you can find answers to many technical questions. If your question has not yet been answered, post it and you should get a reply within a day or so. In addition to community support, internal Asana engineers also help troubleshoot issues on the forum.
If you have found an API bug, you can either post it to the community or email the issue to api-support at Asana dot com.

#### Deployment 
Once you’ve created a custom app, you will likely want to host it somewhere. While you could run your script from the command line, doing so is tedious and time consuming.

The most basic, automated option is to use launchd to programmatically execute your app on your machine (launchd is like cron but better). Here’s a [tutorial to get you started with launchd](https://medium.com/@chetcorcos/a-simple-launchd-tutorial-9fecfcf2dbb3).

A more robust option would be to deploy your custom app to a hosted server. Here’s a guide exploring some of the [popular hosting providers](https://api.slack.com/docs/hosting). Hosting your app makes it more resilient and allows you to add more sophisticated features (e.g. use webhooks). 

Remember to [securely store your PAT](https://www.freecodecamp.org/news/how-to-securely-store-api-keys-4ff3ea19ebda/) and any other sensitive data (never expose a PAT in a public repository). 

#### Maintenance 
Make certain that the email address associated with your custom app is being actively monitored. We only email developers for critical issues such as API bans and [upcoming deprecations](/docs/communicating-about-breaking-changes) that our logs show will break your app. If you’re using a PAT to authenticate, you should confirm that the email address associated with the Asana account that generated the PAT is being actively monitored by one or more people. 

We also recommend all developers join the [Asana developer community](https://forum.asana.com/c/developersAPI/24). This is where we will communicate new API features as well as announce upcoming breaking changes. To ensure you don’t miss these announcements, we encourage you to turn on notifications for the [Platform News](https://forum.asana.com/c/forum-en/api/news) section of the community.

If your app is having issues, here are some steps to help you troubleshoot the issue:

1. Carefully read any error messages (here are the docs for Asana [error codes](/docs/errors)). 
2. Check the [status of the Asana API](https://status.asana.com/) to confirm it’s up and available.
3. Check for any issues with the server that is hosting your app.
4. Check the [Asana dev community](https://forum.asana.com/c/developersAPI/24) to see if others are having the same issue.
5. If you can't find an answer on the community, post your issue and someone will likely help. Please include all of the required information to reproduce the issue (e.g. verbose CURL request with full response). Never post a PAT to the forum (or share it anywhere else). 

<div>
  <div class="docs-developer-satisfaction-content">
      <h4>Was this section helpful? <a class="positiveFeedback-DevSatisfaction" style="cursor:pointer;">Yes </a><a class="negativeFeedback-DevSatisfaction" style="cursor:pointer;">No</a></h4>
  </div>
</div>
</section>
</section>

</section>
