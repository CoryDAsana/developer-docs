# Custom apps

#### What to consider when building a custom app


<span class="description">
Unlike third-party apps and integrations used by many companies, custom apps are designed to only be used within a single domain. For example, an Asana customer may want to use the API to create a bot, integrate Asana with a homegrown tool, or generate custom reports. For more ideas on what you can accomplish through custom apps, here are some [common use cases](/docs/common-usecases).
</span>

#### API explorer 
If you are unfamiliar with our API, it may be helpful to start by playing around with our [API explorer](/docs/api-explorer). The API explorer is a quick and easy way to test various _read_ endpoints and see how various parameters affect responses. You will also find guides and [code examples](/docs/examples) in our documentation and as well as [client libraries](/docs/official-client-libraries) that are helpful when getting started.

To make API requests against a more comprehensive collection of endpoints, you may wish to use our [Postman Collection](/docs/using-postman).

#### Authentication
Most custom apps use [persona access token](/docs/personal-access-token) (PATs) for authentication. In general, PATs are best for projects that don't require multiple users to log in. For example, it is advisable to use PATs to auth scripts, bots, or anything else that doesn’t require taking action on behalf of multiple Asana users. If your custom app requires users to sign in to use it, then you should consider [using OAuth](/docs/oauth).  

#### Client libraries
You should consider using one of our [API client libraries](/docs/official-client-libraries) for your custom app. They simplify some of the more technically challenging aspects of development such as authentication and pagination. There are code examples for each library to help you get started. The client libraries also help developers navigate [API deprecations](/docs/communicating-about-breaking-changes), which will help you avoid unexpected breaking changes and reduce the overall time required for maintenance. 

Note that client library functions are not documented. You need to check the **lib/resources/gen** folder of each library to see the built-in functions.  

#### API support 
If have questions about the API, need help developing your custom app, or just want to meet other Asana developers, you may join our active [developer community](https://forum.asana.com/c/api/24). On the forum, you can find answers to many technical questions. In addition to community support, internal Asana engineers also help troubleshoot issues on the forum. If you have found an API bug, you can either post it to the community or email the issue to api-support at Asana dot com.

#### Deployment 
Once you’ve created a custom app, you will likely want to host it somewhere. While you could run your script from the command line, doing so is tedious and time consuming.

A simple, automated option is to use launchd to programmatically execute your app on your machine (launchd is like cron but better). Here’s a [tutorial to get you started with launchd](https://medium.com/@chetcorcos/a-simple-launchd-tutorial-9fecfcf2dbb3).

A more robust option would be to deploy your custom app to a hosted server. Here’s a guide exploring some of the [popular hosting providers](/docs/hosting). Hosting your app makes it more resilient and allows you to add more sophisticated features (e.g., [webhooks](/docs/overview-of-webhooks) and [app components](/docs/overview-of-app-components)). 

Remember to [securely store your PAT](https://www.freecodecamp.org/news/how-to-securely-store-api-keys-4ff3ea19ebda/) and any other sensitive data. _Never expose a PAT in a public repository_. 

#### Maintenance 
Be sure that the email address associated with your custom app is being actively monitored. We only email developers for critical issues (e.g., API bans). If you are using a PAT to authenticate, you should confirm that the email address associated with the Asana account that generated the PAT is being actively monitored by one or more people. 

We also recommend all developers join the [Asana developer forum](https://forum.asana.com/c/api/24). This is where we will communicate new API features as well as announce upcoming breaking changes. To ensure you don’t miss these announcements, we encourage you to turn on notifications for the [Platform News](https://forum.asana.com/c/api/news/97) section of the community.

If your app is having issues, here are some steps to help you troubleshoot the issue:

1. Carefully read any error messages (see [error codes](/docs/errors) for more details). 
2. Check the [status of the Asana API](https://status.asana.com/) to confirm any potential disruptions.
3. Check for any issues with the server that is hosting your app.
4. Check the [developer forum](https://forum.asana.com/c/api/24) to see if others are having the same issue.
5. If you can't find an answer in the community, post your issue and someone will likely help. Please include all of the required information to reproduce the issue (e.g. verbose cURL request with full response). Never post a PAT to the forum (or share it anywhere else). 

<div>
  <div class="docs-developer-satisfaction-content">
      <h4>Was this section helpful? <a class="positiveFeedback-DevSatisfaction" style="cursor:pointer;">Yes </a><a class="negativeFeedback-DevSatisfaction" style="cursor:pointer;">No</a></h4>
  </div>
</div>