#WaltzerJS

[WaltzerJS](http://www.waltzer-js.co.uk) is a lightweight, easy to skin carousel plugin for jQuery. It includes a range of configurable options making it suitable for a variety purposes. Features include the ability to:

* Choose scrolling orientation (horizontal or vertical).
* Specify a transition speed.
* Specify the amount of items scrolled during each transition.
* Choose automatic or manual scrolling.
* Choose circular or linear scrolling.
* Generate navigation buttons.
* Generate a navigation pager.
* Add additional (third party) easing effects.
* Further customise the plugin, through the provided method and event API.
* Internet Explorer 7, 8, 9 compatible.

##Documentation

WaltzerJS has a range of configurable options to define how the plugin will function when initialised. In addition there is also a number of methods and events that can be used to develop the plugin (and its functionality) further. Further documentation and examples can be found at [www.waltzer-js.co.uk](http://www.waltzer-js.co.uk).
 
###Usage

    $('#carousel').waltzer();

**Markup & Styling**

Markup structure is relatively straight forward. Carousel items need to be nested inside the targeted container. WaltzerJS will create any navigation or pagers elements after the plugin call.

	<div id="carousel">
		<div class="item">1</div>
		<div class="item">2</div>
		<div class="item">3</div>
		<div class="item">4</div>
	</div>

Keep in mind WaltzerJS core styling may be affected by any custom CSS included. Refer to the examples if you encounter any styling based functionality issues.

###Options
**speed** *(integer)*

Time to complete each transition.

Default: *300*

**scroll** *(integer)*

Number of items to scroll during each transition.

Default: *1*

**auto** *(boolean)*

Turn on auto scrolling. Carousel will transition automatically.

Default: *false*

**autoPause** *(integer)*

Pause time between each automatic transition, when auto scrolling is enabled.

Default: *1000*

**easing** *(string)*

Easing effect to be applied during carousel transitions. By default jQuery only has two options built in "swing" and "linear". Further options are available through use of easing plugins such as [jQuery Easing](http://gsgd.co.uk/sandbox/jquery/easing/) or [jQueryUI](http://jqueryui.com/effect/).

Default: *"swing"*

**offset** *(integer)*

Item to start on, items will be reordered positioning the specified item first. 0 based indexing e.g first item is equal to 0.

Default: *0*

**vertical** *(boolean)*

Transition top to bottom, instead of left to right.

Default: *false*

**circular** *(boolean)*

Behavior of the carousel when the last item is reached. *circular* will behave as though items are in a continuous loop e.g. last item appears as the previous item to the first. *non-circular* will behave like a linear row, with the carousel having to transition back to the start along the path it came.

Default: *true*

**navBtns** *(boolean)*

Whether or not to create navigation buttons.

Default: *true*

**leftNavBtn** *(string)*

Class name for the 'previous' button to be created.

Default: *'leftNav'*

**rightNavBtn** *(string)*

Class name for the 'next' button to be created.

Default: *'rightNav'*

**pager** *(boolean)*

Whether or not to create a navigation pager.

Default: *false*

**onCreate** *(function)*

Callback on carousel creation.

Default: *null*

**onComplete** *(function)*

Callback on transition complete.

Default: *null*

**onForwardComplete** *(function)*

Callback on forward transition complete.

Default: *null*

**onBackwardComplete** *(function)*

Callback on backward transition complete.

Default: *null*

**developerMode** *(boolean)*

Logs the WaltzerJS instance as an object to the developer console. Contains various configuration information about a specified carousel.

Default: *false*

###Methods

WaltzerJS has a number of methods that can be used to control the behavior of a carousel after the instance has been created.

**start()**

Turn on auto scrolling.

	$('#carousel').waltzer('start');

**stop()**

Turn off auto scrolling.

	$('#carousel').waltzer('stop');

**forward()**

Move carousel forward.

	$('#carousel').waltzer('forward');

**backward()**

Move the carousel backward.

	$('#carousel').waltzer('backward');

**destroy()**

Removes all carousel functionality, returns the element back to its pre-waltzer state. 

	$('#carousel').waltzer('destroy');

###Events

In addition to providing the ability to pass event callbacks, WaltzerJS also triggers a number of events during and after certain carousel actions. Event listeners can be set up to target these using jQuery's [on() function](http://api.jquery.com/on/).

**forward**

This event is triggered as the carousel moves forward.

**backward**

This event is triggered as the carousel moves backward.

**forwardComplete**

This event is triggered after the carousel moves forward.

**backwardComplete**

This event is triggered after the carousel moves backward.

**move**

This event is triggered as the carousel moves (in either direction).

**moved**

This event is triggered after the carousel moves (in either direction).

##Examples

Below is a collection of examples demonstrating basic and advanced usage of WaltzerJS. For further reference, consult the demo files that come bundled with the plugin download.

###Demo 1

Scroll 1. [View Demo](http://www.carmichaelize.co.uk/examples/waltzerjs/examples/demo_1.html)

    $('#carousel').waltzer();

###Demo 2

Auto scroll 5, start at item 3. [View Demo](http://www.carmichaelize.co.uk/examples/waltzerjs/examples/demo_2.html)

    $('#carousel').waltzer({
	    auto:true,
	    scroll:5,
	    offset:2
    });

###Demo 3

Scroll 4, non-circular. [View Demo](http://www.carmichaelize.co.uk/examples/waltzerjs/examples/demo_3.html)

    $('#carousel').waltzer({
	    scroll:4,
	    circular:false
    });

###Demo 4

Scroll 4 with pager. [View Demo](http://www.carmichaelize.co.uk/examples/waltzerjs/examples/demo_4.html)

    $('#carousel').waltzer({
	    scroll:4,
	    pager:true,
	    navBtns:false
    });

###Demo 5

Scroll 1, vertical, non-circular. [View Demo](http://www.carmichaelize.co.uk/examples/waltzerjs/examples/demo_5.html)

    $('#carousel').waltzer({
	    vertical:true,
	    circular:false,
	    speed:500
    });

###Demo 6

Scroll 2, vertical, specified navigation buttons. [View Demo](http://www.carmichaelize.co.uk/examples/waltzerjs/examples/demo_6.html)

    $('#carousel').waltzer({
	    scroll:2,
	    vertical:true,
	    speed:500,
	    left_nav_btn:'topNav',
	    right_nav_btn:'botNav'
    });

###Demo 7

Auto scroll 5 with custom page counter. [View Demo](http://www.carmichaelize.co.uk/examples/waltzerjs/examples/demo_7.html)

    var counter = function(){
	    var currentPage = this.pageCount,
	        itemCount = this.itemCount,
	    scroll= this.options.scroll;
	    $('#counter').html(currentPage+' / '+(itemCount / scroll));
    }
     
    $('#carousel').waltzer({
	    scroll:5,
	    auto: true,
	    autoPause: 10000,
	    onCreate: counter,
	    onComplete: counter
    });

###Demo 8

Auto scroll 4 with custom stop / start button. [View Demo](http://www.carmichaelize.co.uk/examples/waltzerjs/examples/demo_8.html)

    $('#carousel').waltzer({
	    scroll:4,
	    auto: true,
	    autoPause: 8000
    });
     
    $('#control_btn').on('click', function(){
	    if($(this).text() == 'Start') {
	    	$(this).text('Stop');
	    	$('#carousel').waltzer('stop');
	    } else if($(this).text() == 'Stop') {
	    	$(this).text('Start');
	    	$('#carousel').waltzer('start');
	    }	
    });

##Licence

(Dual) [GPL](http://www.gnu.org/licenses/gpl.html) & [MIT](http://opensource.org/licenses/MIT)