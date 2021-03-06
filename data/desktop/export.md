Export to PDF and PNG
==================================
dhtmlxGantt provides an online export service that will allow you to export the Gantt chart into the [PDF](desktop/export.md#exporttopdf) or 
[PNG](desktop/export.md#exporttopng) format.

{{note
The service is free but if you don't have the commercial license with the valid support period the output PDF/PNG file will contain the library's watermark.
}}

Using Export Services
-----------------------

There are several export services available. You can install them on your computer and export Gantt chart to PDF or PNG locally.

Note that export services are not included into the Gantt package, 
read the [corresponding article](http://dhtmlx.com/docs/products/dhtmlxGantt/export.shtml) to learn the terms of using each of them.

Export to PDF
-----------------------------
To export Gantt chart as a PDF document, do the following steps:

<ol>
	<li>Include the <b>"http://export.dhtmlx.com/gantt/api.js"</b> file on the page to enable the online export service:
~~~html
<script src="codebase/dhtmlxgantt.js"></script>
<script src="http://export.dhtmlx.com/gantt/api.js"></script>  /*!*/
<link rel="stylesheet" href="codebase/dhtmlxgantt.css" type="text/css">
~~~
</li>
	<li>Call the <a href="desktop/export.md#parametersoftheexportmethods">exportToPDF</a> method to export the Gantt chart: 
~~~html
<input value="Export to PDF" type="button" onclick='gantt.exportToPDF()'>/*!*/

<script>
	gantt.init("gantt_here");
	gantt.parse(demo_tasks);
</script>
~~~

</li>
</ol>
{{sample
08_api/06_export.html
}}

Export to  PNG
-----------------------------
To export Gantt chart as a PNG image, do the following steps:

<ol>
	<li>Include the <b>"http://export.dhtmlx.com/gantt/api.js"</b> file on the page to enable the online export service:
~~~html
<script src="codebase/dhtmlxgantt.js"></script>
<script src="http://export.dhtmlx.com/gantt/api.js"></script>  /*!*/
<link rel="stylesheet" href="codebase/dhtmlxgantt.css" type="text/css">
~~~
</li>
	<li>Call the <a href="desktop/export.md#parametersoftheexportmethods">exportToPNG</a> method to export the Gantt chart: 
~~~html
<input value="Export to PNG" type="button" onclick='gantt.exportToPNG()'>/*!*/

<script>
	gantt.init("gantt_here");
	gantt.parse(demo_tasks);
</script>
~~~

</li>
</ol>
{{sample
08_api/06_export.html
}}

Parameters of the export methods
----------------------------------------------------------

The **exportToPDF()** and **exportToPNG()** methods take as a parameter the same object with a number of properties (all of the properties are optional):

<table class="webixdoc_links">
	<tbody>
    	<tr>
			<td class="webixdoc_links0"><b>name</b></td>
			<td>(<i>string</i>) the name of the output file</td>
		</tr>
       <tr>
			<td class="webixdoc_links0"><b>skin</b></td>
			<td>(<i>'terrace', 'skyblue', 'meadow', 'broadway'</i>) the skin of the output Gantt chart</td>
		</tr>
        <tr>
			<td class="webixdoc_links0"><b>locale</b></td>
			<td>(<i>string</i>) sets the language that will be used in the output Gantt chart</td>
		</tr>        
        <tr>
			<td class="webixdoc_links0"><b>start</b></td>
			<td>(<i>string</i>) sets the start date of the data range that will be presented in the output Gantt chart. The date format is defined by the api/gantt_api_date_config.md config</td>
		</tr>
        <tr>
			<td class="webixdoc_links0"><b>end</b></td>
			<td>(<i>string</i>) sets the end date of the data range that will be presented in the output Gantt chart. The date format is defined by the api/gantt_api_date_config.md config</td>
		</tr>
        <tr>
			<td class="webixdoc_links0"><b>data</b></td>
			<td>(<i>object</i>) sets a custom data source that will be presented in the output Gantt chart </td>
		</tr>
        <tr>
			<td class="webixdoc_links0"><b>header</b></td>
			<td>(<i>string</i>) specifies the header that will be added to the output PDF image. Note, you can use any HTML here</td>
		</tr>
        <tr>
			<td class="webixdoc_links0"><b>footer</b></td>
			<td>(<i>string</i>) specifies the footer that will be added to the output PDF image. Note, you can use any HTML here</td>
		</tr>
        <tr>
			<td class="webixdoc_links0"><b>server</b></td>
			<td>(<i>string</i>) sets the API endpoint for the request. Can be used with the local install of the export service. The default value is <strong>https://export.dhtmlx.com/gantt</strong></td>
		</tr>
        <tr>
			<td class="webixdoc_links0"><b>raw</b></td>
			<td>(<i>boolean</i>) defines that all Gantt markup will be exported as it is, with all custom elements. <em>false</em> by default. <a href="desktop/export.md#exportingcustommarkupandstyles">Read the details below</a> </td>
		</tr>
    </tbody>
</table>
<br>
{{snippet
Calling export methods with optional properties
}}
~~~js
gantt.exportToPDF({
	name:"mygantt.pdf",
	header:"<h1>My company</h1>",
	footer:"<h4>Bottom line</h4>",
	locale:"en",
	start:"01-04-2013",
	end:"11-04-2013",
	skin:'terrace',
	data:{ },
    server:"https://myapp.com/myexport/gantt",
    raw:true
});
gantt.exportToPNG({
	name:"mygantt.png",
	header:"<h1>My company</h1>",
	footer:"<h4>Bottom line</h4>",
	locale:"en",
	start:"01-04-2013",
	end:"11-04-2013",
	skin:'terrace',
	data:{ },
    server:"https://myapp.com/myexport/gantt",
    raw:true
});
~~~


##Name of the output file

To set a custom name for the output file, use the **name** property in the parameter of the [exportToPDF/exportToPNG](desktop/export.md#parametersoftheexportmethods) methods:

~~~js
gantt.exportToPDF({
	name:"my_beautiful_gantt.pdf"/*!*/
});
~~~

##Language of the output file

By default, the Gantt chart will be exported in the same language as it is shown on the page.

To set a custom language for the output file, use the **locale** property in the parameter of the [exportToPDF/exportToPNG](desktop/export.md#parametersoftheexportmethods) methods:

~~~js
gantt.exportToPDF({
	name:"mygantt.pdf",
	locale:"de" /*!*/
});
~~~


##Data to export

To set the tasks that should be presented in the output PDF or PNG file, use one of the following ways:

1. <a href="#daterange">Specify the date range of the output data.</a>
2. <a href="#customdata">Specify a custom data source for output.</a>

<a id="daterange"></a>

###Specifying the date range of the output tasks

To set the range of tasks that will be presented in the output document, use the **start**, **end** properties in the parameter of the [exportToPDF/exportToPNG](desktop/export.md#parametersoftheexportmethods) methods:

~~~js
gantt.exportToPDF({
	name:"mygantt.pdf",
	start:"01-04-2013",/*!*/
	end:"11-04-2013"/*!*/
});
~~~

{{note
Note, the date format is defined by the api/gantt_api_date_config.md config
}}

<a id="customdata"></a>

###Setting a custom data source to export

To export the Gantt chart with a custom data set (i.e. not with the data presented in the initial Gantt chart), use the **data** property in the parameter of the 
[exportToPDF/exportToPNG](desktop/export.md#parametersoftheexportmethods) methods:

~~~js
gantt.exportToPDF({
	data:{/*!*/
		data:[
			{id:1, text:"Project #1", start_date:"01-04-2013", duration:18},
			{id:2, text:"Task #1", start_date:"02-04-2013",duration:8, parent:1},
			{id:3, text:"Task #2", start_date:"11-04-2013",duration:8, parent:1}
		],
		links:[
			{id:1, source:1, target:2, type:"1"},
			{id:2, source:2, target:3, type:"0"},
			{id:3, source:3, target:4, type:"0"},
			{id:4, source:2, target:5, type:"2"}
		]
	}
});
~~~

{{note
Note, you cannot specify some URL as the value of the **data** parameter, just a data object.
}}

##Skin of the output Gantt chart

By default, the Gantt chart will be exported with the same skin as it is shown on the page.

To set a custom skin for the output PNG or PDF file, use the **skin** property in the parameter of the [exportToPDF/exportToPNG](desktop/export.md#parametersoftheexportmethods) methods:

~~~js
gantt.exportToPDF({
	name:"mygantt.pdf",
	skin:"broadway"/*!*/ // or "skyblue", "meadow", "terrace"
});
~~~

##Header/footer of the output file

To add a header/footer to the output PNG or PDF file, use the **header**/**footer** properties in the parameter of the [exportToPDF/exportToPNG](desktop/export.md#parametersoftheexportmethods) methods:

{{note
Note, you can use any HTML while specifying the parameters. While specifying images, remember that you need to set global paths as values of the "src" attribute
}}

~~~js
gantt.exportToPDF({
	name:"mygantt.pdf",
	header:"<h1>My company</h1>",/*!*/
	footer:"<h4>Bottom line</h4>"/*!*/
});
~~~


##Custom style for the output file

To apply a custom style for the gantt, provide the stylesheet with your custom CSS classes:

- through a link:

~~~js
gantt.exportToPDF({
    name:"calendar.pdf",
    header:'<link rel="stylesheet" href="http://mysite.com/custom.css">' /*!*/
});
~~~

- or through the 'style' tag:

~~~js
gantt.exportToPDF({
    name:"calendar.pdf",
    header:'<style>... custom css classes here ...</style>' /*!*/
});
~~~


Note, the aforementioned solution works for the global HTTP reference. If you have CSS classes specified in an Intranet/local environment, you can embed all styles as in:

~~~js
gantt.exportToPDF({
	header:"<style>.tier1{background: red; color:white;}</style>"
});
~~~


##Exporting custom markup and styles

By default the Gantt chart is exported based on the specified configuration and loaded data, while [custom elements](desktop/baselines.md) and some templates are not exported.
To export the whole gantt markup as it is, with all custom elements, you can set the **raw:true** property in the parameter of the [exportToPDF/exportToPNG](desktop/export.md#parametersoftheexportmethods) methods.

~~~js
gantt.exportToPDF({
	raw:true
});
~~~

Note that custom elements will require providing [custom styles](desktop/export.md#customstylefortheoutputfile) in order to be displayed correctly.

Pay attention that the use of this mode increases the size of the API request. Large charts can exceed limit of the online export of 4MB and may not be exported that way.
In such a case you need to have an export service installed locally and increase the request size.



