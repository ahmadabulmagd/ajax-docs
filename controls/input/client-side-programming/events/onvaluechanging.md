---
title: OnValueChanging
page_title: OnValueChanging | UI for ASP.NET AJAX Documentation
description: OnValueChanging
slug: input/client-side-programming/events/onvaluechanging
tags: onvaluechanging
published: True
position: 16
---

# OnValueChanging



## 

The __OnValueChanging__ client-side event handler is called when the user changes the value of the input control. The event occurs immediately after the control loses focus, but before its value has been updated.

>note The __OnValueChanging__ event is supported by: __RadNumericTextBox__ , __RadDateInput__ , and __RadTextBox__ . On __RadNumericTextBox__ , __OnValueChanging__ does not occur if the user enters a non-numeric value.
>


Two parameters are passed to the event handler:

* __sender__ is the input control.

* __eventArgs__ has the following methods:

* __set_cancel()__ lets you permit or block the change to the value of the control. Calling __set_cancel(true)__ prevents the change.

* __get_oldValue()__ returns the string value of the input control before the user made any changes.

* __get_newValue()__ returns the string value that is about to be assigned to the input control.

* __set_newValue()__ lets you change the value that is about to be assigned to the input control.

The following example uses the __OnValueChanging__ event to force the value of a text box to be one of a limited number of possible values:

````ASPNET
	    <telerik:RadTextBox ID="RadTextBox1" runat="server">
	        <ClientEvents OnValueChanging="LimitOptions" />
	    </telerik:RadTextBox>
````



````JavaScript
	    <script type="text/javascript">
	        function LimitOptions(sender, eventArgs)
	        {
	            if (eventArgs.get_newValue() == "t" || eventArgs.get_newValue() == "T" || eventArgs.get_newValue() == "true")
	                eventArgs.set_newValue("True");
	            else if (eventArgs.get_newValue() == "f" || eventArgs.get_newValue() == "F" || eventArgs.get_newValue() == "false")
	                eventArgs.set_newValue("False");
	            if (eventArgs.get_newValue() != "True" && eventArgs.get_newValue() != "False")
	                eventArgs.set_cancel(true);
	        }
	    </script>
````



# See Also

 * [OnValueChanged]({%slug input/client-side-programming/events/onvaluechanged%})

 * [TextChanged Event]({%slug input/server-side-programming/textchanged-event%})

 * [OnKeyPress]({%slug input/client-side-programming/events/onkeypress%})