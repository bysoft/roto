What is Roto?
=============
Roto is a simple, flexible, touch-capable image spinner plugin for jQuery.
See a demo at http://www.pausebuttonedit.com/roto/demo.html

You may think another jQuery image spinner is the last thing the world needs. Well, none of the existing ones entirely met my reqirements -- so I wrote Roto.


What are these stringent and esoteric requirements?

1. I wanted it to work nicely with touch devices, and to be familiar to users of touch devices when working on a desktop browser. Roto does this by aping the iPhone's inertial scrolling when clicked and dragged; you can point your finger or your mouse pointer at it, swipe, and the images whirl by. Then you can point again to stop the whirl, or slowly drag to exactly the image you want to see. If you get to the end of the scroll travel, it lets you pull a bit and then does a nice bounce back.

2. I wanted it to have a simple button-based fallback for users more comfortable with that, and for the buttons to work in a sensible way. Roto doesn't advance or retreat image-by-image when you press the Previous or Next buttons: it advances by its entire width, so you see the next SET of images, not the next image in the queue. Much quicker.

3. I wanted it to be simple and flexible. You can pass Roto all sorts of options, or none at all. You can put the buttons anywhere you like, or nowhere at all. You can have vertical or horizontal rotos; rotos can contain anything you can put in an html listitem, not just images; you can stack up your images in a grid and it'll still work. You can have working links in the roto; you can use it with Fancybox. All done without major headaches.

4. I wanted it to be supplied with a minimum of styling. I'm a designer, so I'll do the styling, thanks. I don't need any funny-looking skins -- just the functionality.


How do I use it?
----------------
1. Create a div or other block-level element. Give it an id or a classname that you can use to identify it.
2. Put an unordered list inside it.
3. Put some listitems in your list, containing whatever you want to be rotoed (normally images, or images inside links, but whatever you like).
4. Optionally, add a couple of buttons with classnames 'prev' and 'next' inside the containing element.
5. Call roto on the containing element, e.g. $("#roto-div").roto().

See the demo for an example.


Are there dependencies?
-----------------------
The only dependency is my own Bez plugin (https://github.com/rdallasgray/bez), which is used to create jQuery-compatible easing functions from cubic-bezier co-ordinates. That's just for compatibility with browsers which don't support CSS transitions, so if you're only supporting newer browsers, you don't need it.


What else do I need to know?
----------------------------
Roto works best if you call it using $(window).load() rather than $(document).ready(). This is because Webkit-based browsers don't know the dimensions of images at $(document).ready() time, and Roto relies on those dimensions. Of course, if you're giving all your images explicit dimensions anyway, you can use $(document).ready().


What options do I have, and what are the defaults?
--------------------------------------------------
Lots of options. The ones you'll generally want to use are:

- btnPrev: the css selector for the 'Previous' button. Default is '.prev'.
- btnNext: the css selector for the 'Next' button. Default is '.next'.
- direction: 'h' for horizontal, 'v' for vertical. Default is 'h'.
- snap: whether to snap individual listitems. Default is true.

That's all. Power users have more options and should read the source and experiment.

The button defaults work when the buttons are INSIDE the overall containing element. If you want to put them outside (which can be useful), you need to give the containing element an id (say, 'roto'), and then id your buttons as '[id]-prev' and '[id]-next' ('roto-prev'/'roto-next'). Otherwise you can specify precisely how to identify them in the options.


How do I style Roto?
--------------------
Any way you like. I haven't supplied any examples, for reasons you can read above. You don't NEED to include any CSS for Roto to work -- the script sets the basic required styles for you. But it can certainly look (and sometimes work) better with a bit of design nous.

There are certain things that will break Roto, though:

1. The overall container must be set with overflow: hidden, position: relative.
2. The unordered list must be set with position: relative, white-space: nowrap, and padding and margin 0.
3. The listitems must be set with display: block, float: left, list-style: none.

You DON'T need to set these -- the script does it for you. But be aware that if you contradict them in your own stylesheets or scripts, you could run into problems.

Otherwise, you shouldn't need to treat Roto with kid gloves. It'll take most of what you throw at it.


What doesn't work?
------------------
It might not work in IE6. I haven't tested it. Life's too short.


Acknowledgements
----------------
I must acknowledge Ganeshji Marwaha's jCarouselLite (http://www.gmarwaha.com/jquery/jcarousellite), which I used somewhat before writing Roto. Some of the option names are lifted from jCarouselLite, because there was no point being awkward by changing them.