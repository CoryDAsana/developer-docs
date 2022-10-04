<hr class="full-line">
<section class="full-section">
<section>

# How to use the API

> Request

```
https://app.asana.com/api/1.0/users/me
```

_If you are familiar with building against APIs, you make skip this section and review our code [examples](/docs/examples)._

<span class="description">
If you are new to developing on APIs, you may begin here. In this guide, you'll learn how to make a simple Asana API request: getting your user information. 
</span>

To get started:

1. Be [logged into Asana](https://app.asana.com).
2. Go to this URL: <a href="https://app.asana.com/api/1.0/users/me?opt_pretty&opt_client_name=hello_world_browser" target="_blank">https://app.asana.com/api/1.0/users/me</a>

`me` is a user identifier that refers to the logged-in user. A user identifier can be either `me`, an email_address, or the GID of the user.

> Response

```json
{
  "data": {
    "gid": "12e345a67b8910c11",
    "email": "jonsnow@example.com",
    "name": "Jon Snow",
    "photo": {
      "image_21x21": "https://s3.amazonaws.com/profile_photos/121110987654321.hJGlskahcKA5hdslf4FS_21x21.png",
      "image_27x27": "https://s3.amazonaws.com/profile_photos/121110987654321.hJGlskahcKA5hdslf4FS_27x27.png",
      "image_36x36": "https://s3.amazonaws.com/profile_photos/121110987654321.hJGlskahcKA5hdslf4FS_36x36.png",
      "image_60x60": "https://s3.amazonaws.com/profile_photos/121110987654321.hJGlskahcKA5hdslf4FS_60x60.png",
      "image_128x128": "https://s3.amazonaws.com/profile_photos/121110987654321.hJGlskahcKA5hdslf4FS_128x128.png"
    },
    "resource_type": "user"
  }
}
```

Congratulations! You’ve just made your first Asana API request (for which you've received a response). Let’s explore what just happened.

#### Making a request

The base URL for all requests to the Asana API is `https://app.asana.com/api/1.0`. We want information about users, so we go down a level to the `https://app.asana.com/api/1.0/users` resource. Then, within the set of all users in Asana, we’re specifically looking to get information about our own account. We do so by adding `/me` to get `https://app.asana.com/api/1.0/users/me`. The `/me` part would ordinarily be an identifier (i.e., a long number) or email address of the user, but we've created this shorthand for getting the current user of Asana's API, whomever that may be. With everything put together, the result is the URL to get your user information from Asana: `https://app.asana.com/api/1.0/users/me`.

Since every API request you make will start with the same base URL (`https://app.asana.com/api/1.0`), in this documentation we'll generally refer to the URL by its resoruce or relative path. For instance, when we say `/users/me`, we are using this as a shorthand for the entire URL: `https://app.asana.com/api/1.0/users/me`.

#### Receiving a response

After requesting information from the API, you will receive a response in [JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON) format, which can be read and understood by both humans and computers. The response is structured in a particular way so programs can rely on a consistent format for the data.

Our API is documented for what resources are available and what sort of return data to expect. For example, here is the [documentation for the `/users` endpoint](/docs/get-a-user), which we just called (i.e., requested) earlier. This is where you can discover what is possible with our API.

Now, let’s make the same call to `/users/me` more like software would. Before we do so, we’ll need to get access outside of your web browser to the API.

<div>
  <div class="docs-developer-satisfaction-content">
      <h4>Was this section helpful? <a class="positiveFeedback-DevSatisfaction" style="cursor:pointer;">Yes </a><a class="negativeFeedback-DevSatisfaction" style="cursor:pointer;">No</a></h4>
  </div>
</div>

</section>
<hr>
<section>

## Authenticating
<a id="authentication-quick-start"></a>

<span class="description">
Similar to entering your username/password into a website or logging into Asana with Google, when you access your Asana data via the API, you need to authenticate. In the above example, you were already logged into Asana in your browser, so you were able to authenticate to the API with credentials stored by your browser.
</span >

If you want to write a script that interacts with the Asana API, a quick method is to first get a [personal access token](/docs/personal-access-token) (PAT), which you can think of as your unique password for accessing the API.

### App or PAT?

If your app needs to perform actions on behalf of users, you should use [OAuth](/docs/oauth).

**Getting a personal access token (PAT)**

> Example PAT

```
0/68a9e79b868c6789e79a124c30b0
```

1. Open the [developer console](https://app.asana.com/-/developer_console) (also accessible by clicking on your profile photo in the Asana app, then selecting **"My Settings"** > **Apps** > **"Manage Developer Apps"**).

2. Select **+ Create new token**.

3. Enter a description (i.e., you’ll use the personal access token for).

4. Click **Create token**.

5. Copy your token and store it securely. You will only see this token displayed one time, but you can always create another PAT later.

_Note: Treat your PAT like you would a password. Do not share it and do not display it online_.

<div>
  <div class="docs-developer-satisfaction-content">
      <h4>Was this section helpful? <a class="positiveFeedback-DevSatisfaction" style="cursor:pointer;">Yes </a><a class="negativeFeedback-DevSatisfaction" style="cursor:pointer;">No</a></h4>
  </div>
</div>

</section>
<hr>
<section>

## Using cURL

<a id="accessing-the-api-in-the-terminal"></a>

> cURL request

```
curl https://app.asana.com/api/1.0/users/me \
  -H "Authorization: Bearer 0/123456789abcdef"
```

<span class="description">
You may use cURL, a command line program to make HTTP requests. MacOS and many Linux distributions have cURL pre-installed, and it is also [available for download](https://curl.haxx.se/dlwiz/?type=bin) on Windows and many other operating systems. For more information about the tool, you visit cURL's [documentation](https://curl.se/docs/manpage.html). 
</span>

To begin:

> Response

```json
{
  data: {
    gid: "<your gid>",
    email: "<your email>"
    name: "<your name>",
    ...
  }
}
```

1. Open a terminal (instructions for [Mac](https://support.apple.com/guide/terminal/open-or-quit-terminal-apd5265185d-f365-44cb-8b09-71a064a42125/mac) and [Windows](https://www.wikihow.com/Open-the-Command-Prompt-in-Windows)).

2. Copy/paste the cURL request on the right (make sure to enter your personal access token instead of the placeholder after the word "Bearer", otherwise you will see a "Not Authorized" message):

3. Press Enter/Return on your keyboard.

You should see the response in your terminal! In our API documentation, we will often write examples as cURL commands, since it is a "middle-of-the-road" approach to accessing our API -- more flexible than using a browser, but user-friendly enough to be functional right out-of-the-box.

At this point, you are ready to begin development against the API! Asana has [client libraries](/docs/client-libraries) in several popular coding languages. Using these libraries has several advantages (e.g., managing authorization, retrying errors, etc.) that make them a good place to go from here. In the [examples](/docs/examples) section, feel free to see how you can make the same `/users/me` request in Python, JavaScript, and Ruby.

<div>
  <div class="docs-developer-satisfaction-content">
      <h4>Was this section helpful? <a class="positiveFeedback-DevSatisfaction" style="cursor:pointer;">Yes </a><a class="negativeFeedback-DevSatisfaction" style="cursor:pointer;">No</a></h4>
  </div>
</div>

</section>
<hr>
<section>

## Using Postman

<a id="accessing-the-api-with-postman"></a>

<blockquote>
<div class="postman-run-button"
data-postman-action="collection/import"
data-postman-var-1="c7a5949aed49ec7851c5"></div>
<script type="text/javascript">
  (function (p,o,s,t,m,a,n) {
    !p[s] && (p[s] = function () { (p[t] || (p[t] = [])).push(arguments); });
    !o.getElementById(s+t) && o.getElementsByTagName("head")[0].appendChild((
      (n = o.createElement("script")),
      (n.id = s+t), (n.async = 1), (n.src = m), n
    ));
  }(window, document, "_pm", "PostmanRunObject", "https://run.pstmn.io/button.js"));
</script>
</blockquote>

<span class="description">
You can quickly get started on Asana's API with the [API explorer](/docs/api-explorer). However, if you want a more comprehensive experience making API requests, we recommend using [Postman](https://learning.postman.com/docs/getting-started/introduction/). You can get started with the 'Run in Postman' button!
</span>

Once you have the collection, you should [create an environment](https://learning.postman.com/docs/sending-requests/managing-environments/).

You should then set:

1. An `authentication_token` to a personal access token (PAT). If you don't have one yet, visit [personal access token](/docs/personal-access-token) for details.
2. A `workspace` to your workspace's gid. You can find this value via a logged-in browser by going to [https://app.asana.com/api/1.0/users/me/workspaces](https://app.asana.com/api/1.0/users/me/workspaces), or you can make a request to that endpoint using your PAT.
3. Any other GIDs you want to easily access. For example, you can set `task` to the GID of a task that you regularly test with, `project` to the gid of a private sandbox project, and `user` to the string 'me'.

There is no need to edit your environment for requests on different objects. You may simply navigate to the endpoint you want to use, then change the `{{object}}` to any gid you want.

_Note: Importing this collection gives you a snapshot of the API at this time. To stay up to date with API changes, you'll have to re-import the collection by selecting the 'Run in Postman' button, and choosing to override your existing collection. As such, if you want to save custom requests, you should do so in a different collection._

<div>
  <div class="docs-developer-satisfaction-content">
      <h4>Was this section helpful? <a class="positiveFeedback-DevSatisfaction" style="cursor:pointer;">Yes </a><a class="negativeFeedback-DevSatisfaction" style="cursor:pointer;">No</a></h4>
  </div>
</div>

</section>
</section>
