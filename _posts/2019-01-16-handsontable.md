---
title: handsontable
description: handsontable
categories:
tags:
---

#### handsontable ####
   
**helpdoc**:
    https://handsontable.com/docs/6.2.2/tutorial-using-callbacks.html

    <html>
	<script src="https://cdn.jsdelivr.net/npm/handsontable@6.2.2/dist/handsontable.full.min.js"></script><link href="https://cdn.jsdelivr.net/npm/handsontable@6.2.2/dist/handsontable.full.min.css" rel="stylesheet" media="screen">
	<body>
	<div id="example"></div>

	<script>
	var data = [
  	["", "Ford", "Tesla", "Toyota", "Honda"],
 	["2017", 10, 11],
  	["2018", 20, 11],
  	["2019", 30, 15]
	];

	var container = document.getElementById('example');
	var hot = new Handsontable(container, {
  		data: data,
 	 	rowHeaders: true,
  		colHeaders: true,
  		filters: true,
 		dropdownMenu: true,
  		colWidths: [50, 400, 600],
  		columns: [
   		{readOnly: true},
    	{
      	editor: 'select',
      	selectOptions: ['10', '20', '30']
	  
    	},
    	{}
  		]
	});

	</script>
	</body>
	</html>