# jQuery Wizard Builder : Plugin

A simple plugin to convert content into a step-by-step wizard. This package utilizes jQuery and Bootstrap. It was built with jQuery 2.x+ and Bootstrap 3.x+

### Installation

```html
Checkout the respository with git

<!--Jquery from your library or the copies in demo folder-->
<script src="js/jquery-2.2.2.min.js"></script>

<!--Bootstrap from your library or the copies in demo folder-->
<script src="js/bootstrap-3.3.6.min.js"></script>
<link href="css/bootstrap-3.3.6.min.css" rel="stylesheet" media="screen">

<!--Wizard Builder from the /dist folder (use .min versions in production-->
<script src="../dist/jquery.wizard-builder.min.js"></script>
<link href="../dist/jquery.wizard-builder.min.css" rel="stylesheet">

```

### Instructions
Simple Example. See /demo/index.html for more complex scenarios

```html
<!-- Load the libraries, css, and js as shown above into your <head> or combination <head> and bottom of <body> -->

<div id="my_wizard">
    <ul class="steps">
        <li data-step="1">Step 1</li>
        <li data-step="2">Step 2</li>
    </ul>
    <div class="steps-content">
        <div data-step="1">
            ...Content
        </div>
        <div data-step="2">
            ...Content
        </div>
    </div>
</div>

<!-- Just before end of page before </body> run the Javascript -->
<script type="text/javascript">

    // $("#my_wizard").wizardBuilder(); // Simple initiation with JS having no options passed in

    // Javascript manual init with a couple options passed in
    $("#my_wizard").wizardBuilder({
        actionBar: false,                  // Hide the embedded next/prev buttons
        onCompleted: function(element) {    // Add a callback function when the final step "Complete" is pushed
            console.log(element);
        },
    });

</script>
```
### Reference Documentation

Options
-------
Initialization options that can be passed in during initial build of the wizard
```javascript
$("#my_wizard").wizardBuilder({
    actionBar: false    // OPTION: Hide the embedded next/prev buttons
});
```
<table class="table table-bordered table-striped">
	<thead>
		<tr>
			<th>Option</th>
			<th>Default</th>
			<th>Allowed</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
	    <tr>
	        <td>actionBar</td>
	        <td>true</td>
	        <td>true / false</td>
	        <td>
	        Add the button action bar inline with the step elements.
	        Options are boolean true or false to show or hide the buttons in the upper step bar</td>
	    </tr>
	    <tr>
            <td>bottomButtons</td>
            <td>true</td>
            <td>true / false</td>
            <td>
            Add the next/prev buttons below the content container.
            Options are boolean true or false to show or hide the buttons at the bottom of the wizard</td>
        </tr>
        <tr>
            <td>autoSubmit</td>
            <td>false</td>
            <td>true / false</td>
            <td>
            If set to true and the whole wizard is contained within a &ltform&gt tag,
            the final "Complete" step will simply submit the form to its action. If you have
            added an onCompleted method call, this option is ignored</td>
        </tr>
        <tr>
            <td>stepCounterType</td>
            <td>'numbers'</td>
            <td>'numbers', 'letters', 'none'</td>
            <td>
            The types of prefix for the step boxes. Defaults to using 'numbers' starting at 1.
            'letters' will start steps with "A", 'none' will show no step label prefix
            </td>
        </tr>
        <tr>
            <td>nextClass</td>
            <td>'btn btn-default btn-mini btn-xs'</td>
            <td>Any CSS Classes</td>
            <td>
            The CSS class(es) to apply to the NEXT buttons (these are also applied to Complete button with finalClass option combined)</td>
        </tr>
        <tr>
            <td>prevClass</td>
            <td>'btn btn-default btn-mini btn-xs'</td>
            <td>Any CSS Classes</td>
            <td>
            The CSS class(es) to apply to the PREVIOUS buttons</td>
        </tr>
        <tr>
            <td>completeClass</td>
            <td>'btn-success'</td>
            <td>Any CSS Classes</td>
            <td>
            The CSS class(es) to apply to the FINAL button (includes the nextClass option before this is appended)</td>
        </tr>
	</tbody>
</table>

Events
-------
Initialization of event callbacks that get triggered. They pass in just like options during setup

```javascript
$("#my_wizard").wizardBuilder({
    onCompleted: function(element) {    // Add a callback function when the final step "Complete" is pushed
        console.log(element);
    },
});
```
<table class="table table-bordered table-striped">
	<thead>
		<tr>
			<th>Event</th>
			<th>Parameters</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
	    <tr>
	        <td>onCompleted</td>
	        <td>(self)</td>
	        <td>
	            Triggered when the final submission button is pressed.<br/>
	            Receives an instance of its WizardBuilder object as a parameter.<br/>
	            <italic>If this event is hooked up, the option for autoSubmit is ignored.</italic>
	        </td>
	    </tr>
	</tbody>
</table>


License
===============
The MIT License (MIT)

Copyright (c) 2016 - Joel Colombo

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

### Original Author & License
jQuery / jqLite Wizard Plugin  
https://github.com/bygiro/jQuery-Wizard-Plugin  
version: 0.0.4  
Author: Girolamo Tomaselli http://bygiro.com  
Copyright (c) 2013 G. Tomaselli  
Licensed under the MIT license.  
