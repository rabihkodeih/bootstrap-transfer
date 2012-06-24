bootstrapTransfer
=================

Welcome to bootstrapTransfer. This is a two-column transfer multi-select widget. It is
inspired by Django admin module's similar widget. The look and feel is designed to blend with
twitter bootstrap (2.0+), jQuery 1.7+ is assumed.

Usage :

First, in your html create a div and give it some id:

    <div id="test"></div>

It is possible to set a width value whose bootstrapTransfer will use for the generated widget:

    <div id="test" style="width:500px;"></div>
	
Also you can add some bootstrap classes such as 'input-xlarge' in forms:
	
    <div id="test" class="input-xlarge"></div>
	
Now call bootstrapTransfer on the corresponding jquery object and add some values:

    $(function() {
        ...
        var t = $('#test').bootstrapTransfer();
        t.populate([
            {value:"1", content:"Apple"},
            {value:"2", content:"Orange"},
            {value:"3", content:"Banana"},
            {value:"4", content:"Peach"},
            {value:"5", content:"Grapes"}
        ]);
        ...
    });

You can get the selected values any time:

    console.log(t.get_values());

Setting new values is straightforward:

    t.set_values(["2", "4"]);
	
Alternatively, you can access the plugin object directly from the selector:

	$('#test').data().bootstrapTransfer.get_values()
	$('#test').data().bootstrapTransfer.set_values(["2", "4"])

Note that the order of the items at population time is allways preserved in both get_values and set_values.

Options are:

    target_id : the id of the internal select element, useful for wiring events and such
	height : the height of the select columns, default value is '10em'
	hilite_selection: if true will hilite the moved items between the columns, default value is true
	
Example:	

    $('#test').bootstrapTransfer(
        {'target_id': 'multi-select-input'
         'height': '15em',
         'hilite_selection': false});

I hope you find this widget useful.