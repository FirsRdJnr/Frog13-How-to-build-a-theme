#Frog13 How to build a theme workshop

##Introduction
- I'm a Front End Interface Developer at Frog.
- Audience expectations (basic knowledge of CSS & HTML).
- This page contains the notes that accompany the presentation.

##Flexibility - Scrolling, images, expanding content

###Scrolling
- Don’t make your theme fixed
- Test on different browser sizes
- Frog touch scrolling

####Notes
```HTML
* You can't account for the size of content that will need to go in a site, or the size of browser someone will be looking at it in.
* If you make your content 1000px high, it won't fit on an iPad screen, but if you make it 600px height then it’ll get lost on a hi-res display.
* Make sure you test on different browser sizes, Chrome has a tool you can use to change the aspect ratios of the browser for different devices.
* Frog touch scrolling is a class that is added so that FrogOS works on touch devices, as this is where the markets going, it’s important that we support this technology.
```

###Images
- Background images need to repeat
- Large images can still break
- Be careful with fixed images overlapping content

####Notes
```HTML
* Some areas that have background images may need to expand to accommodate text/titles and content, you need to make sure that the bg images repeat and don't break
* We’ve had situations where a header image wasn't long enough to accommodate a long title so as the title grew the text continued onto a white background
* Fixed images can be used, but be careful of using z-index and positions as we’ve had images interfering with widgets within a site if not done well.
```

###Expanding content
- Content is predicted by the user
- Headers - long words
- Content - 300px 3 columns

####Notes
```HTML
The content and header areas can be small or large, depending on how people use a site, so make sure you test for both.
```





##Based on - reveal.js [![Build Status](https://travis-ci.org/hakimel/reveal.js.png?branch=master)](https://travis-ci.org/hakimel/reveal.js)

A framework for easily creating beautiful presentations using HTML. [Check out the live demo](http://lab.hakim.se/reveal-js/).

reveal.js comes with a broad range of features including [nested slides](https://github.com/hakimel/reveal.js#markup), [markdown contents](https://github.com/hakimel/reveal.js#markdown), [PDF export](https://github.com/hakimel/reveal.js#pdf-export), [speaker notes](https://github.com/hakimel/reveal.js#speaker-notes) and a [JavaScript API](https://github.com/hakimel/reveal.js#api). It's best viewed in a browser with support for CSS 3D transforms but [fallbacks](https://github.com/hakimel/reveal.js/wiki/Browser-Support) are available to make sure your presentation can still be viewed elsewhere.
