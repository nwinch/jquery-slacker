Slacker
=============

jQuery plugin for lazy loading images.

Why?
----
There are many great lazy load plugins out there, but none seemed to capture everything that I wanted to achieve for a project at the time.  So I 
created my own - with the specific aim that it would load different size/quality images on the fly and only when required.

HTML
----
### Basic

`<div class="slacker" data-slacker='{ "sizes":{ "original":"img/image1.jpg" }}'></div>`
`<img class="slacker" data-slacker='{ "sizes":{ "original":"img/image1.jpg" }}' height="120" src="img/some-transparent-image.gif" width="200"></div>`

### Multiple resolutions

`<div class="slacker" data-slacker='{ "sizes":{ "original":"img/image1.jpg", "640":"img/image-640.jpg" }}'></div>`

### High quality images
You can split any resolution check into high and low quality image options.  Slacker will detect if you are using a high pixel density 
ratio (current check is for > 1).
`<div class="slacker" data-slacker='{ "sizes":{ "original":"img/image1.jpg", "640":{ "reshigh":"img/image-640-high.jpg", "reslow":"img/image-640-low.jpg" }}}'></div>`

JavaScript
----------

### Basic

`$('.slacker').slacker();`

### Multiple resolutions

`$('.slacker').slacker({
  sizes : [640]
});`

### Resize functionality

This will allow multiple resolutions to be switched on the fly when resizing the browser.

@resize - true|false; default=true; Enable/disable resize functionality.<br />
@resizeThrottle - (millisecond); default=100; Throttle functionality will control how frequently the window resize event is fired.  Higher number is less frequent.

`$('.slacker').slacker({
	resize : true
	, resizeThrottle : 100
});`

### Animation

There are two handlers - 'beforeLoad' and 'onLoad'.
`$('.slacker').slacker({
	animate : {
		beforeLoad : function(el) {
			el.css({ opacity:0 });
		}
		, onLoad : function(el) {
			el.animate({ opacity:1 }, 1000);
		}
	}
});`