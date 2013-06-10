#Frog13 How to build a theme workshop

##Introduction
- I'm a Front End Interface Developer at Frog.
- Audience expectations (basic knowledge of CSS & HTML).
- This page contains the notes that accompany the presentation.

##Flexibility - Scrolling, images, expanding content
*Frogos has been built for an array of devices, so flexibility is key.*

###Scrolling
- Don’t make your theme fixed
- Test on different browser sizes
- Frog touch scrolling

#####Notes
* You can't account for the size of content that will need to go in a site, or the size of browser someone will be looking at it in.
* If you make your content 1000px high, it won't fit on an iPad screen, but if you make it 600px height then it’ll get lost on a hi-res display.
* Make sure you test on different browser sizes, Chrome has a tool you can use to change the aspect ratios of the browser for different devices.
* .frog-touch-scroll is a class that is added so that FrogOS works on touch devices, as this is where the markets going, it’s important that we support this technology.

###Images
- Background images need to repeat
- Large images can still break
- Be careful with fixed images overlapping content

#####Notes
* Some areas that have background images may need to expand to accommodate text/titles and content, you need to make sure that the bg images repeat and don't break.
* We’ve had situations where a header image wasn't long enough to accommodate a long title so as the title grew the text continued onto a white background.
* Fixed images can be used, but be careful of using z-index and positions as we’ve had images interfering with widgets within a site if not done well.

###Expanding content
- Content is predicted by the user
- Headers - long words
- Content - 300px 3 columns

#####Notes
* Content is added by the user, it could be one widget and a one line header, or it could be a whole website with content. So you must make sure that your design is flexible enough to accommodate both.
* We had some issues with long words not wrapping; there’s a simple CSS class you can add, word-wrap:break-word; this will make sure that headers won't break your layout.
* Content areas can have 1,2 or 3 columns or a mixture of all three, this means that keeping the content are to no smaller than 960px is necessary for the smallest column size to be 300px.

##Optimization - image sizes, using fonts, CSS gradients
*To help FrogOS run effectively, we need to be careful what we put in there.*

###Avoid large background images

- Slow load times
- Problems switching between themes
- Compression software, like <a href="http://kraken.io/">kraken</a>

#####Notes
* The larger the image,the longer it’ll take to load, especially on iPads
* as themes are dynamically loaded, we can’t preload images like we do in the rest of the platform
* Optimise your image as best you can to keep file sizes low, Kraken is a great example of an online image compression tool.

###File sizes

- Combined files 800kb or lower
- Need to be packaged up

#####Notes
* All files, including images, in a theme folder should not exceed 800kb,
* We can’t restrict how people will download a theme, so we may need to send these themes over wifi to mobile devices, so the smaller you can make a theme, the better.

###Embed custom fonts

- Font Squirrel generator
- Download and embed Google fonts
- Header base sizes

#####Notes
* Don't link to them from the web. Google fonts, or fonts you’ve bought can be turned into webfonts easily by using an online font generator
* Different browsers require different font types to render the text.
* Remember, fonts have different base sizes, which means you must check that the overall size of text that uses the font are legible.

###CSS over Images

- CSS box shadows, rounded corners & more css3generator.com
- CSS gradients Ultimate CSS Gradient Generator

#####Notes
* Use css gradients and box shadows instead of background images, CSS file sizes are vastly smaller than images and can achieve nicer results than using a low res image.
* These two websites are great to use to generate the CSS that is compatible across all browsers.

##Structure - .EJS, HTML, CSS, LESS, Navigation, Theme builder
*A Theme's directory is system generated and is stored in FrogOS/internal/theme/theme folder/. The Theme is then called using JavaScript within FrogOS. In a theme directory there is no support for subfolders so all images etc. need to be in the root folder - this will be changing soon.*

###.ejs = embedded javascript

- Combines data and a template to produce HTML
- This type of file is readable by FrogOS

#####Notes
* An .ejs file compiles the HTML and CSS that makes up a theme into a readable file for FrogOS. It's still easier to build in HTML & CSS so you can view your work, then add both to an ejs file later.

###Build in LESS for scoped CSS

- Use LESS if you can.
- Crunch is a great Less compiler
- CSS should always have a unique wrapper class

#####Notes
* Rather than constructing long selector names to specify inheritance, in Less you can simply nest selectors inside other selectors. This makes inheritance clear and style sheets shorter.
* It’s paramount that each theme has a unique class that wraps all the content like .ui-theme-frog13. Themes can be switched out for other themes, but browsers cache images and css, so if you have the same class name as another theme, the browser will render it with the previous css and images.

###Navigation

- Cheat!
- No unique classes
- Remember the + page tab

#####Notes
* This is the trickiest part of any theme. As navigation is much like content and is user generated, this means that each link has a unique ID generated by the system that we can’t predict in a theme. This means that you have to target levels of navigation by the UL class, data-menu-level="2" for example.
* You can also choose from two types of navigation, so you could have a nested navigation (where all the navigation is together), or you could choose to have 3 sets of individual navigation set out thorough the theme - there are no working examples of this in FrogOS as it will require a certain type of design, but this is the closest approximation we’d have to it being used.
* It’s useful to have the add page function in a different colour to normal navigation so it’s easy for a user to identify what it is.

###Theme builder

- Download
- Host
- Run

#####Notes
* This is a dynamic tool and will need to be hosted on a server for it to work, This is due to the nature of how all the components are dynamically brought together…it’s basically a copy of how FrogOS works.
You can try running a localhost, such as xampp <a href="http://www.apachefriends.org/en/xampp.html">apache</a>. This will create a folder on your system and treat it like a server.
* Download the Boilerplate on the themes guide <a href="http://designguide.frogtrade.com/themes.html">design guide</a>.

##Compatibility - colours, backgrounds graceful degradation
*Compatibility with widgets, FrogOS and the theme itself.*

###Text colours

- White text on white backgrounds
- Widget colours

#####Notes
* Keep in mind the content background colour when adding text styles there has been issues with white text on white backgrounds.
* Widgets have different coloured headers and can be overridden by accident, avoid using the !important selector in CSS.

###No javascript

- Frog OS is built with Javascript
- Conflicts
- Use classes not ids

#####Notes
* As FrogOS’s interface is built using JS, we can’t allow custom scripts as we won't know how this will interact with existing JS on the page.
* Use classes only, FrogOS’ Javascript is based on ids so we avoid them in themes so it doesn't conflict with the interface.

###Browser support

- No more IE7!
- All CSS2 & most CSS3 supported
- Graceful degradation
- Basically...avoid IE

#####Notes
* JS was unstable in ie7 and as such, we moved away from this.
* This also means that most CSS2 styles will work with the platform, there are issues with CSS3 in ie8, but we encourage graceful degradation, which means that we don't support rounded corners or box shadows in ie8.

--------------------------------------------










##Based on - reveal.js [![Build Status](https://travis-ci.org/hakimel/reveal.js.png?branch=master)](https://travis-ci.org/hakimel/reveal.js)

A framework for easily creating beautiful presentations using HTML. [Check out the live demo](http://lab.hakim.se/reveal-js/).

reveal.js comes with a broad range of features including [nested slides](https://github.com/hakimel/reveal.js#markup), [markdown contents](https://github.com/hakimel/reveal.js#markdown), [PDF export](https://github.com/hakimel/reveal.js#pdf-export), [speaker notes](https://github.com/hakimel/reveal.js#speaker-notes) and a [JavaScript API](https://github.com/hakimel/reveal.js#api). It's best viewed in a browser with support for CSS 3D transforms but [fallbacks](https://github.com/hakimel/reveal.js/wiki/Browser-Support) are available to make sure your presentation can still be viewed elsewhere.
