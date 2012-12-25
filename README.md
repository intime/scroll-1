Scroll
======

Custom adaptive scrolling

## Supported in browsers and devices:

- iPhone and iPad
- Firefox 3.6
- Opera 10+
- Chrome and Safari
- Internet Explorer 7+

## Installation

Include tag link for styles:

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

####Html inner drag-tag [example](http://csscode.ru/test/scroll#drag-old):

    new Scroll({
        drag_old: '<div class="drag-top"></div><div class="drag-body"></div><div class="drag-bottom"></div>' // default - false
    });

####Custom class name for node:

    new Scroll( '.scroll-myclass-name' ,{ // name main wrapper
        cls: ['scroll-wrap', 'scroll-pane', 'scroll-track', 'scroll-drag'] // strict sequence
    });

####Run all scrolling right off and set step (speed):

    new Scroll({
        start: true, // default - false
        step : 5 // step (speed), default - 5
    });

## Events

**Delegate events to track the behavior and to get debug information.**

####Events list:

    // example
    $('body').on('eventname', '.scroll', function(event, data){
        console.dir(data);

        // data.config.cls      - array current clasess
        // data.config.drag_old - if is html inner drag-tag then this html else false
        // data.config.horizontal - if is horizontal then true
        // start: false - start?
        // step: 5 - step

        // data.node == div.scroll
        // data.tracking.scrollHeight - height scrolling box
        // paneHeight - height wrap contents
        // dragHeight - height slider
        // dragTop - The distance from slider top border to the top dead dott wrapper
        // dragBot - The distance from slider bottom border to the bottom dead dott wrapper
    });

####The event name
- **scrolling.load**       - start init scripts
- **scrolling.create**     - create node
- **scrolling.loaded**     - script loaded

- **scrolling.mouseenter** - The event mouse enter for class name .scroll node
- **scrolling.mouseleave** - The event mouse leave
- **scrolling.mouseover**  - The event mouse over
- **scrolling.mouseout**   - The event mouse out
- **scrolling.mousedown**  - The event mouse down
- **scrolling.mousemove**  - The event mouse move
- **scrolling.mouseup**    - The event mouse up

- **scrolling.left**       - The event occurs when the slider to the left dead dott
- **scrolling.right**      - The event occurs when the slider to the right dead dott
- **scrolling.top**        - The event occurs when the slider to the top dead dott
- **scrolling.bottom**     - The event occurs when the slider to the bottom dead dott
- **scrolling.scroll**     - The event scrolling

## Set position:

    $('#set-pos').click(function(e){
        var event = jQuery.Event("scrolling.set"); // create event
        event.scrollY = 100; // custom position by Y
        event.scrollX = 100; // custom position by X if horizontal scrolling
        event.duration = duration; // duration animate
        event.easing   = 'linear'; // default 'swing'
        $(".scroll").trigger(event); // call start
        return false; // stop default event
    });
