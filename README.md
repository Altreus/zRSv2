zRS - Responsive Slider - v2.2
===

2.2 Update:
---

Added additional options to support image swapping on smaller viewports, this can be invoked by using the following structure:

	$('.slider').zRS({

		procedural: true,
		sizes: {

			mobile : 480,
			tablet : 768

		}

	});

The labels 'mobile' and 'tablet' are just examples you can use any label and any sizes. The number in the option refers to which data attribute will be read if the screensize is SMALLER than the number; data-src will be used if it's larger than the highest value.

Here's a markup example for the above example.

	<img src="_blank.gif" alt="example" data-src="highres.jpg" data-tablet="midres.jpg" data-mobile="smallres.jpg" />

If the slide itself isn't an image then it will search the slide for the images!

Basic Implementation:
---

Use the following HTML structure when implementing the slider to your webpage.

	<div class="slider"> <!-- The element the slider needs to be called on -->
		<div class="inner-slider"> <!-- Inner slider is necessary to make the plugin function correctly, make sure this is 100% width if you want it responsive! -->
			<img src="img/trans/1.jpg" alt="Tester" />
			<img src="img/trans/2.jpg" alt="Tester" />
			<img src="img/trans/3.jpg" alt="Tester" />
			<img src="img/trans/4.jpg" alt="Tester" />
			<img src="img/trans/5.jpg" alt="Tester" />
			<img src="img/trans/6.jpg" alt="Tester" />
			<img src="img/trans/7.jpg" alt="Tester" />
			<img src="img/trans/8.jpg" alt="Tester" />
		</div>
	</div>

Use the following JS structure when implementing the slider to your webpage.

	$(document).ready(function() {

		$('.slider').zRS();		// Uses default options below
		$('.slider').zRS({		// Set your own options!

			speed: 500,
			delay: 7000,
			transition: 'fade'

		});

		$('.slider').zRS('transition', 'forward'); 	// Firing a method, full list below!

	});

Some options aren't compatable with one another, make sure you check the console if things aren't working correctly, you will get an error message that gives you more insight.

Options:
---

Here's a list of options with all their defualt values:

	delay: 5000, 				// The amount of time before the slide transitions automatically, set to 0 to turn off automatic transition.
	speed : 1000, 				// The speed of the animation.
	transition : 'slide', 		// Transition type, currently 'slide' and 'fade' are the only ones.
	procedural : false, 		// Proceedural image loading, more info below.
	pager : false, 				// A selector for pagination e.g. $('.pager').
	pauseOnHover : false, 		// Explains itself!
	visibleSlides : 1, 			// The number of slides visible at anytime, not comatable with fade.
	slideSpacing : 0,			// The spacing in pixels between each slide.
	pre_trans_callback : null,	// A callback just before the slide transitions.
	trans_callback : null, 		// A callback for when the slide has finished it's transition.
	load_callback : null,		// A callback for when the slide has finished loading.
	sizes: null 				// An object full of sizes to swap out for smaller images on mobile devices.

Callbacks:
---

Each callback has a few values you can access to help you do what you need to do, listed below are all the properties you can access.

###### Pre Transition Callback
	
	pre_trans_callback: function(e) {

		this 		// The this keyword refers to the slide that you are transitioning to.
		e.target 	// The slide number you are going to.

	}

###### Transition Callback

	trans_callback: function(e) {

		this 		// The this keyword refers to the slide you're currently on.
		e.slide 	// The slide number you're currently on.

	}

###### Load Callback

	load_callback: function(e) {

		this 		// The this keyword refers to the main slider container.
 
	}

Methods:
---

zRS has a few methods that you can call in order to manipulate the plugin once it's up and running, they are as follows:

	$('.slider').zRS('transition', 'forward');	// Transitions forward 1 slide
	$('.slider').zRS('transition', 'back');		// Transition back 1 slide
	$('.slider').zRS('goTo', 0);				// Go to the specified slide! 0 is the first slide.

	$('.slider').zRS('pause');					// This will pause the slider
	$('.slider').zRS('play');					// This will resume the slider

	$('.slider').zRS('setVisibleSlides', 2);	// This will set the current number of visible slides

	$('.slider').zRS('widthAdjustments');		// Update the width calculations for the slides


Bind them to whatever events you need to!

Procedural Loading Implementation:
---

This version supports dynamic loading in of images as the slider transitions, saving a lot of time on page load, especially for sliders with large images.

First thing first set the procedural option to be true in the settings. e.g.

	$('.slider').zRS({

		procedural : true

	});

Once you've set that up you will need to follow the following HTML structure with your images either inside your slides or as the slides themselves.

	<img src="_blank.gif" alt="Example" data-src="image.jpg" />

It's as simple as that! "_blank.gif" is optional, you may leave the src attribute empty.

###### Image swapping

With 2.2 you can now use the sizes option to swap images out depending on viewport size it is implemented as follows:

	$('.slider').zRS({

		procedural: true,
		sizes: {

			mobile : 480,
			tablet : 768

		}

	});

The labels 'mobile' and 'tablet' are just examples you can use any label and any sizes. The number in the option refers to which data attribute will be read if the screensize is SMALLER than the number; data-src will be used if it's larger than the highest value.

Here's a markup example for the above example.

	<img src="_blank.gif" alt="example" data-src="highres.jpg" data-tablet="midres.jpg" data-mobile="smallres.jpg" />

If the slide itself isn't an image then it will search the slide for the images!