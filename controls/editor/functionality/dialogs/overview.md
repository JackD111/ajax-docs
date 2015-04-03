---
title: Dialogs Overview
page_title: Overview | UI for ASP.NET AJAX Documentation
description: Overview
slug: editor/functionality/dialogs/overview
tags: overview
published: True
position: 0
---

# Dialogs Overview



## 

RadEditor offers FileBrowser dialogs such as

* Image Manager

* Flash Manager

* Silverlight Manager

* Document Manager

* HyperlinkManager

* Media Manager

* Template Manager

The RadEditor FileBrowser dialogs are mainly used to insert objects in the content area. These are the Image Manager, Flash Manager, Document Manager, Media Manager and Template Manager dialogs. The FileBrowser dialogs also provide the ability to upload and delete files and directories. You can find more information about the File Browser dialogs in the following article: [File Browser Dialogs]({%slug editor/functionality/dialogs/file-browser-dialogs/overview%}).

These dialogs are enabled by default. Dialog visibility can be toggled using the [ToolsFile.xml]({%slug editor/functionality/toolbars/using-toolsfile.xml%}) or by populating the RadEditor Tools collection.

RadEditor offers FileBrowser dialogs such as ImageManager, FlashManager and DocumentManager as well as others such as the HyperlinkManager, the About and Help dialogs.

To enable dialogs, use the Smart Tag __Enable RadEditor Dialogs__ option.
>caption 

![](images/editor-ataglance001.png)

Running the Smart Tag option will add the following web.config HttpHandler entry:

````XML
	    <httpHandlers>  
	        ...  
	        <add path="Telerik.Web.UI.DialogHandler.aspx" verb="*" type="Telerik.Web.UI.DialogHandler" validate="false" />
	    </httpHandlers>
	    ...
	    <system.webServer>    
	        <handlers>      
	            ...      
	            <add name="Telerik_Web_UI_DialogHandler_aspx" verb="*" preCondition="integratedMode" path="Telerik.Web.UI.DialogHandler.aspx" type="Telerik.Web.UI.DialogHandler" />    
	        </handlers>  
	    </system.webServer>
````

