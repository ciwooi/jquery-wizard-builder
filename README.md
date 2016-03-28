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
    <div data-step="1">
        ...Content
    </div>
    <div data-step="2">
        ...Content
    </div>
</div>

<!-- Just before end of page before </body> run the Javascript -->
<script type="text/javascript">

    // $("#my_wizard").wizardBuilder(); // Simple initiation with JS having no options passed in

    // Javascript manual init with a couple options passed in
    $("#my_wizard").wizardBuilder({
        topButtons: false,                  // Hide the top next/prev bottoms
        onCompleted: function(element) {    // Add a callback function when the final step "Complete" is pushed
            console.log(element);
        },
    });

</script>
```



### Original Author
jQuery / jqLite Wizard Plugin  
https://github.com/bygiro/jQuery-Wizard-Plugin  
version: 0.0.4  
Author: Girolamo Tomaselli http://bygiro.com  
Copyright (c) 2013 G. Tomaselli  
Licensed under the MIT license.  
