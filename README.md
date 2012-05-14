jquery-dawdle
=============

jQuery plugin for lazy loading images.

Based on jQuery lightweight boilerplate pattern: https://github.com/addyosmani/jquery-plugin-patterns/blob/master/patterns/jquery.basic.plugin-boilerplate.js

<!--! Basic. -->
<div class="dawdle" data-dawdle='{ "sizes":{ "original":"img/image1.jpg" }}'></div>
<img class="dawdle" data-dawdle='{ "sizes":{ "original":"img/image1.jpg" }}' height="120" src="img/some-transparent-image.gif" width="200"></div>

<!--! Multiple resolutions: define the width as the key name in the data object. -->
<div class="dawdle" data-dawdle='{ "sizes":{ "original":"img/image1.jpg", "640":"img/image-640.jpg" }}'></div>

// Basic.
$('.dawdle').dawdle();

// Multiple resolutions: must supply resolutions during setup for markup references to be picked up.
$('.dawdle').dawdle({
  sizes : [640]
});

// Resize functionality: this will allow multiple resolutions to be switched on the fly when resizing the browser.
// @resize - true|false; default=true; Enable/disable resize functionality.
// @resizeThrottle - (millisecond); default=100; Throttle functionality will control how frequently the window resize event is fired.  Higher number = less frequent.
$('.dawdle').dawdle({
	resize : true
	, resizeThrottle : 100
});

// Animation: there are two handlers - 'beforeLoad' and 'onLoad'.
$('.dawdle').dawdle({
	animate : {
		beforeLoad : function(el) {
			el.css({ opacity:0 });
		}
		, onLoad : function(el) {
			el.animate({ opacity:1 }, 1000);
		}
	}
});