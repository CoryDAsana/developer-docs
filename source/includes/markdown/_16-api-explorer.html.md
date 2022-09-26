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

<hr class="full-line">