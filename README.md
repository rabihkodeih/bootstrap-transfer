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
	template : the actual html code with the selectors and buttons 

Example:	

    $('#test').bootstrapTransfer(
        {'target_id': 'multi-select-input'
         'height': '15em',
         'hilite_selection': false});

Localization:

If needed, specify the labels for the widget. In this example the labels are set to spanish:

    $.fn.bootstrapTransfer.locale = {
	    available_title: 'Disponible',
	    selected_title: 'Seleccionados',
	    help_text: 'Agregue presionando',
	    add_button: 'Agregar',
	    remove_button: 'Remover',
	    add_all_button: 'Agregar todos',
	    remove_all_button: 'Remover todos'
    };

Templating :

You can specify the html where the bootstrap-transfer widget will be 

    var t = $('#test').bootstrapTransfer({
		'target_id' : 'multi-select-input',
		'height' : '15em',
		'hilite_selection' : true,
		'template':
			'<div class="input-prepend"><span class="add-on"><i class="icon-search"></i></span> '+
				'<input type="text" class="span2 filter-input"></div>'+
			'<table width="100%" cellpadding="0" cellspacing="0">' +
				"<tbody>" + 
					"<tr>"+
						'<td width="50%">'+
							'<h4>{%=available_title%}</h4>' + 
							'<select class="filtered remaining span12" id="available" multiple="multiple" name="available[]" size="10"></select>'+
						'</td>'+
						'<td style="padding: 2px;">'+
							'<div class="btn-group btn-group-vertical" style="display: inline-block;">'+
								'<button type="button" class="btn btn-small selector-chooseall" title="{%=add_all_button%}">'+ 
									'<i class="icon-forward"></i></button>'+
								'<button type="button"  class="btn btn-small selector-add" title="{%=add_button%}" >'+ 
									'<i class="icon-chevron-right"></i> </button>'+
								'<button type="button" class="btn btn-small selector-remove" title="{%=remove_button%}" >'+ 
									'<i class="icon-chevron-left"></i></button>'+
								'<button type="button" class="btn btn-small selector-clearall" title="{%=remove_all_button%}" >'+ 
									'<i class="icon-backward"></i></button>'+
							'</div>'+
						'</td>'+
						'<td width="50%">'+
							'<h4>{%=selected_title%}</h4>' + 
							'<select class="filtered target span12" id="selected" multiple="multiple" name="selected[]" size="10">'+
							'</select>'+
						'</td>'+
					'</tr>'+
				'</tbody>'+
			'</table>'
    });
In the templates, tokens can be used to specify where to use the localizations labels. The syntax is {%=label_name%}, where 'label_name' should be present in the locale hash. 

I hope you find this widget useful.