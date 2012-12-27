Scroll
======

Custom adaptive scrolling

## Supported in browsers and devices:

- iPhone/iPod and iPad
- Firefox 3.6+
- Opera 10+
- Chrome and Safari
- Internet Explorer 7+

## Installation

Include tag <link> for styles:

    <link rel="stylesheet" type="text/css" href="/path/to/scroll.css" media="all" />

Include script **after** the jQuery library:

    <script src="/path/to/jquery.scroll.js"></script>

## Usage:

Simply start! [base example](http://csscode.ru/test/scroll/)

    new Scroll();

## Configuration

**All configuration is optional**

####Horizontal scrolling [example](http://csscode.ru/test/scroll#horizontal):

    new Scroll({
        horizontal:true // default - false
    });

####Your html code in the slider [example](http://csscode.ru/test/scroll#drag-old):

    new Scroll({
        drag_old: '<div class="drag-top"></div><div class="drag-body"></div><div class="drag-bottom"></div>' // default - false
    });

####Custom classes for the node:

    new Scroll('.scroll-myclass-name', { // name main wrapper
        cls: ['scroll-wrap', 'scroll-pane', 'scroll-track', 'scroll-drag'] // strict sequence
    });

####Run all scrolling right off, set step (speed) and support Apple device:

    new Scroll({
        start: true, // default - false
        step : 5, // step (speed), default - 5
        iDeviceSupport: false // off support Apple device, default - true
    });

## Events

**Delegate events to track the behavior and to get debug information.**

####Events list:

    // example
    $('body').on('eventname', '.scroll', function(event, data){
        console.dir(data);

        // data.config.cls      - array current clasess
        // data.config.drag_old - if is html inner slider then this html else false
        // data.config.horizontal - if is horizontal then true default false
        // data.config.start: false - is start?
        // data.config.step: 5 - step

        // data.node == div.scroll
        // data.tracking.scrollHeight - height scrolling box
        // data.tracking.paneHeight - height wrap contents
        // data.tracking.dragHeight - height slider
        // data.tracking.dragTop - The distance from slider top border to the top dead point wrapper
        // data.tracking.dragBot - The distance from slider bottom border to the bottom dead point wrapper
    });

####The event name
- **scrolling.init**       - start init scripts
- **scrolling.create**     - create node
- **scrolling.inited**     - script loaded

- **scrolling.mouseenter** - The event mouse enter for class name .scroll node
- **scrolling.mouseleave** - The event mouse leave
- **scrolling.mouseover**  - The event mouse over
- **scrolling.mouseout**   - The event mouse out
- **scrolling.mousedown**  - The event mouse down
- **scrolling.mousemove**  - The event mouse move
- **scrolling.mouseup**    - The event mouse up

- **scrolling.left**       - The event occurs when the slider to the left dead point
- **scrolling.right**      - The event occurs when the slider to the right dead point
- **scrolling.top**        - The event occurs when the slider to the top dead point
- **scrolling.bottom**     - The event occurs when the slider to the bottom dead point
- **scrolling.scroll**     - The event scrolling

## Set position:

    $('#set-pos').click(function(e){
        var event = jQuery.Event("scrolling.set"); // create event
        event.scrollY = 100; // custom position by Y, optional '+number' or '-number', example '+54'
        event.scrollX = 100; // custom position by X if horizontal scrolling, optional '+number' or '-number', example '-76'
        event.duration = duration; // duration animate
        event.easing   = 'linear'; // default 'swing'
        $(".scroll").trigger(event); // call start
        return false; // stop default event
    });

*Button Up or Down [example](http://csscode.ru/test/scroll#up-and-down-button):*

    $('.scroll-up').click(function(e){
        var event = jQuery.Event("scrolling.set");
        event.scrollY = '-20';
        event.duration = 300;
        $(".scroll").trigger(event);
        return true;
    });
