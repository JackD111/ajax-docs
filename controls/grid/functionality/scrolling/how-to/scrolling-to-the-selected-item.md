---
title: Scrolling to the Selected Item
page_title: Scrolling to the Selected Item | UI for ASP.NET AJAX Documentation
description: Scrolling to the Selected Item
slug: grid/functionality/scrolling/how-to/scrolling-to-the-selected-item
tags: scrolling,to,the,selected,item
published: True
position: 0
---

# Scrolling to the Selected Item



## 

If you have an initially selected item (row) in a scrollable grid, you may want to bring the focus to this item when the page first loads. The following steps describe how to accomplish this:

1. Set one of the items in the control as selected. (The following example selects a row in the same function that moves to the selected row. However, after that, it shows how to move to the selected row even if it were selected in some other way).

1. Provide a handler for the client-side __GridCreated__ event.

1. In the event handler, locate the selected row using the __GridTableView__ object's __get_selectedItems()__ method.

1. Use the __RadGrid__ object's __GridDataDiv__ property to access the DOM element for the scrollable region of the grid.

1. Use the DOM element for the row to check if it is visible in the scrollable region. If it is not, set the __scrollTop__ property of the scrollable region to scroll the grid so that the selected row is showing.

The following example demonstrates this technique:

````JavaScript
	    <script type="text/javascript">
	        function GridCreated(sender, eventArgs) {
	            //gets the main table scrollArea HTLM element  
	            var scrollArea = document.getElementById(sender.get_element().id + "_GridData");
	            var row = sender.get_masterTableView().get_selectedItems()[0];
	
	            //if the position of the selected row is below the viewable grid area  
	            if (row) {
	                if ((row.get_element().offsetTop - scrollArea.scrollTop) + row.get_element().offsetHeight + 20 > scrollArea.offsetHeight) {
	                    //scroll down to selected row  
	                    scrollArea.scrollTop = scrollArea.scrollTop + ((row.get_element().offsetTop - scrollArea.scrollTop) +
	                    row.get_element().offsetHeight - scrollArea.offsetHeight) + row.get_element().offsetHeight;
	                }
	                //if the position of the the selected row is above the viewable grid area  
	                else if ((row.get_element().offsetTop - scrollArea.scrollTop) < 0) {
	                    //scroll the selected row to the top  
	                    scrollArea.scrollTop = row.get_element().offsetTop;
	                }
	            }
	        }
	    </script>
````



````ASPNET
	    <telerik:RadGrid ID="RadGrid1" runat="server" DataSourceID="SqlDataSource1" AllowPaging="true"
	        PageSize="25" Skin="Web20" Width="95%">
	        <mastertableview width="100%" />
	        <clientsettings>
	      <Scrolling AllowScroll="true" UseStaticHeaders="true" SaveScrollPosition="true" />
	      <ClientEvents OnGridCreated="GridCreated" />
	      <Selecting AllowRowSelect="true" />
	    </clientsettings>
	        <pagerstyle mode="NumericPages" />
	    </telerik:RadGrid>
	    <asp:SqlDataSource ID="SqlDataSource1" runat="server" ConnectionString="<%$ ConnectionStrings:NorthwindConnectionString %>"
	        SelectCommand="SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, PostalCode FROM [Customers]">
	    </asp:SqlDataSource>
````

