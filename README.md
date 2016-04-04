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
            <td>btnText</td>
            <td>
                {
                    next : 'Next',
                    previous: 'Previous',
                    complete: 'Complete'
                }
            </td>
            <td>An object with at least ONE of the 3 properties set in the default to override</td>
            <td>
            You can change the default button text for one or more of the button types. Value must be an object with properies
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
			<th>Return</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
	    <tr>
	        <td>onCompleted</td>
	        <td>(self)</td>
	        <td>Null</td>
	        <td>
	            Triggered when the final submission button is pressed.<br/>
	            Receives an instance of its WizardBuilder object as the self parameter.<br/>
	            This does not require a return value<br/>
	            <italic>If this event is hooked up, the option for autoSubmit is ignored.</italic>
	        </td>
	    </tr>
	    <tr>
            <td>onStepLoadBefore</td>
            <td>(self, direction, event)</td>
            <td>Boolean</td>
            <td>
                Triggered whenever a step is about to be loaded<br/>
                Receives an instance of its WizardBuilder object as the self parameter.<br/>
                Receives a boolean parameter (direction); true if its an attempt to move forward a step, false if backward<br/>
                Receives the original browser event as 3rd parameter<br/>
                Return a BOOLEAN true if you want it to proceed or a false to stop it from changing steps<br/>
                <italic>This is the old checkStep method renamed and will be rewritten very soon as a bunch of new methods are added for events</italic>
            </td>
        </tr>
	</tbody>
</table>

Methods
-------
Methods that can be called on the wizard object directly

```javascript
$("#my_wizard").wizardBuilder('methodNameBelow', { // methodNameBelow is referenced below
    param_1: 'param_value_1',
    param_2: 'param_value_2' // etc. Params are listed in docs below as NAME: DATA TYPE (with descriptions on right)
});
```
<table class="table table-bordered table-striped">
	<thead>
		<tr>
			<th>Method Name</th>
			<th>Parameters</th>
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
	    <tr>
	        <td>setErrorCount</td>
	        <td>step:int, errors:int</td>
	        <td>
	            Sets the Error Count in the step headings for a specific step<br/>
	            An integer is expected for the two parameters<br/>
	            Step must be a valid step number 1 to X (number of steps in your wizard)<br/>
	            If errors is set to 0, the error label will disappear
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
