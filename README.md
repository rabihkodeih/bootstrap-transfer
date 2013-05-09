bootstrapTransfer
=================

Welcome to bootstrapTransfer. This is a two-column transfer multi-select widget. It is
inspired by Django admin module's similar widget. The look and feel is designed to blend with
twitter bootstrap (2.0+), jQuery 1.7+ is assumed.

###Usage

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
            {value:'1', content:'Apple'},
            {value:'2', content:'Orange'},
            {value:'3', content:'Banana'},
            {value:'4', content:'Peach'},
            {value:'5', content:'Grapes'}
        ]);
        ...
    });

You can get the selected values any time:

    console.log(t.get_values());

Setting new values is straightforward:

    t.set_values(['2', '4']);
	
Alternatively, you can access the plugin object directly from the selector:

	$('#test').data().bootstrapTransfer.get_values()
	$('#test').data().bootstrapTransfer.set_values(['2', '4'])

Note that the order of the items at population time is always preserved in both get_values and set_values.

###Options

<table>
    <tr>
        <th style="text-align:left; vertical-align:top;">target_id</th>
        <td style="text-align:left;">The "id" attribute of the internal select element, useful for wiring events and such.</td>
    </tr>
    <tr>
        <th style="text-align:left; vertical-align:top;">height</th>
        <td style="text-align:left;">The height of the select columns, default value is '10em'.</td>
    </tr>
    <tr>
        <th style="text-align:left; vertical-align:top;">hilite_selection</th>
        <td style="text-align:left; vertical-align:top;">If true will hilite the moved items between the columns. Defaults to true.</td>
    </tr>
    <tr>
        <th style="text-align:left; vertical-align:top;">remaining_select_id</th>
        <td style="text-align:left; vertical-align:top;">The "id" attribute of the remaining choices select element (on left). Defaults to "remaining_select".</td>
    </tr>
    <tr>
        <th style="text-align:left; vertical-align:top;">remaining_select_name</th>
        <td style="text-align:left; vertical-align:top;">The "name" attribute of the remaining choices select element. Defaults to "remaining_select".</td>
    </tr>
    <tr>
        <th style="text-align:left; vertical-align:top;">target_select_id</th>
        <td style="text-align:left; vertical-align:top;">The "id" attribute of the target choices select element (on left). Defaults to "target_select".</td>
    </tr>
    <tr>
        <th style="text-align:left; vertical-align:top;">target_select_name</th>
        <td style="text-align:left; vertical-align:top;">The "name" attribute of the target choices select element. Defaults to "target_select".</td>
    </tr>
</table>
	
###Example:	

    $('#test').bootstrapTransfer(
    {
        'target_id': 'multi-select-input'
        'height': '15em',
        'hilite_selection': false
    });

I hope you find this widget useful.
