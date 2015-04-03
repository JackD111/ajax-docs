---
title: OnClientItemClicking
page_title: OnClientItemClicking | UI for ASP.NET AJAX Documentation
description: OnClientItemClicking
slug: menu/client-side-programming/events/onclientitemclicking
tags: onclientitemclicking
published: True
position: 3
---

# OnClientItemClicking



## 

The __OnClientItemClicking__ client-side event occurs when the user clicks on a menu item, before the menu responds to the mouse click.

The event handler receives two parameters:

1. The instance of the menu firing the event.

1. An eventArgs parameter containing the following methods:

* __get_item__ returns a reference to the __RadMenuItem__ that was clicked.

* __set_cancel__ lets you prevent the menu from responding to the mouse click.

* __get_cancel__ returns a boolean value indicating whether the mouse click was cancelled.

* __get_targetElement__ (__RadContextMenu__ only) returns a reference to the target element attached to the context menu that is responsible for the context menu showing.

* __get_domEvent__ returns a reference to the DOM event that caused the clicking.

You can use this event to pre-process an item click or to cancel the default response:

````ASPNET
	
	    <script type="text/javascript">
	    function onClicking(sender, eventArgs) {
	        var item = eventArgs.get_item();
	        var navigateUrl = item.get_navigateUrl();
	        if (navigateUrl && navigateUrl != "#") {
	            var proceed = confirm("Navigate to " + navigateUrl + " ?");
	            if (!proceed) {
	                eventArgs.set_cancel(true);
	            }
	            else {
	                eventArgs.set_cancel(false);
	            }
	        }
	    }
	    </script>
	
	    <telerik:RadMenu ID="RadMenu1" runat="server" OnClientItemClicking="onClicking">
	        ...
	    </telerik:RadMenu>
````





# See Also

 * [OnClientItemClicked]({%slug menu/client-side-programming/events/onclientitemclicked%})

 * [Overview]({%slug menu/client-side-programming/overview%})

 * [RadMenuItem Object]({%slug menu/client-side-programming/objects/radmenuitem-object%})

 * [ItemClick]({%slug menu/server-side-programming/itemclick%})

 * [RadContextMenu Object]({%slug menu/context-menus/radcontextmenu-object%})