bootstrap-transfer
==================

Welcome to bootstrapTransfer. This is a two-column transfer multi-select widget. It is
inspired by Django's admin multi-select widget. The look and feel is designed to blend with
twitter bootstrap (2.0+) and the widget is compatible with jQuery 1.7+.
Usage is very simple.

First, in your html create a div and give it some id:

    <div id="test"></div>

Now call bootstrapTransfer on the corresponding jquery object and add some options:

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

This is useful for setting events and such. I hope you find this widget useful.