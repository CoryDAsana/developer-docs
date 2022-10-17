<hr class="full-line">
<section>

# Custom external data

<span class="description">
Custom external data allows a client application to add app-specific metadata to [tasks](/docs/tasks)
in the API. The custom data includes a string `gid` that can be used to retrieve objects and a data blob that can store
character strings.
</span>

The blob may store unicode-safe serialized data such as [JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON)
or [YAML](https://yaml.org/). The external `gid` is capped at 1,024 characters, while data blobs are capped at 32,768 characters. Each object supporting
external data can have one `gid` and one data blob stored with it. You can also use either or both of those fields.

The external `gid` field is a good choice to create a reference between a resource in Asana and another database, such as
cross-referencing an Asana task with a customer record in a CRM, or a bug in a dedicated bug tracker. Since it is just
a unicode string, this field can store numeric IDs as well as URIs. However, when using URIs, extra care must be taken
that the parameter is escaped correctly when forming queries . By assigning an external `gid`, you can use the notation
`external:custom_id` to reference your object anywhere that you may use the original object `gid`.

_Note: You will need to authenticate with [OAuth](/docs/oauth), as the `gid` and data are app-specific, and these fields are not_
_visible in the UI. This also means that external data set by one Oauth app will be invisible to all other Oauth apps._
_However, the data is visible to all users of the same app that can view the resource to which the data is attached,_
_so this should not be used for private user data._

| Parameter | Description |
|---|---|
| gid | `"contractor_name"` 	The external `gid`. Max size is 1024 characters. Can be a URI. |
| data | `"{ \"time_estimate\": 3600, \"time_spent\": 1482 }"` The external data blob. Max size is 32,786 characters. |

<div>
  <div class="docs-developer-satisfaction-content">
      <h4>Was this section helpful? <a class="positiveFeedback-DevSatisfaction" style="cursor:pointer;">Yes </a><a class="negativeFeedback-DevSatisfaction" style="cursor:pointer;">No</a></h4>
  </div>
</div>

</section>
