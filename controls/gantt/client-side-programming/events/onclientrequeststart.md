---
title: OnClientRequestStart
page_title: OnClientRequestStart | RadGantt for ASP.NET AJAX Documentation
description: OnClientRequestStart
slug: gantt/client-side-programming/events/onclientrequeststart
tags: onclientrequeststart
published: True
position: 1
---

# OnClientRequestStart

## 

The **OnClientRequestStart** occurs when a request to the Web Service is about to be sent. The event is raised only when the Gantt is bound to a Web Service and is raised for every request sent to the service, including all CRUD operations on tasks, dependencies, resources and assignments.

The event handler receives two parameters:

1. The instance of the Gantt control firing the event.

1. An **eventArgs** parameter containing the following methods:

* **get_type** returns the type of the request.

* **get_context** returns a context object (implements IDictionary) that is passed to the Web Service method that handles the request.

* **set_cancel** lets you cancel the event and stop the request.

````ASP.NET
<telerik:RadGantt runat="server" id="RadGantt1" OnClientRequestStart="OnClientRequestStart">
</telerik:RadGantt>
````

````JavaScript
function OnClientRequestStart(sender, eventArgs) {
    args.set_cancel(true);
}
````

# See Also

 * [Client-Side Basics]({%slug gantt/client-side-programming/overview%})

 * [Client-Side Events]({%slug gantt/client-side-programming/events/overview%})