![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

<!--1:30 5 minutes -->

# Responsive Design

<!--Hook: Raise your hand if you've ever opened a webpage on your phone, and it looks ugly?  Buttons all over the place, text falling off the screen?  You are not alone.  The purpose of Responsive Design is to solve this problem, so whether you are looking at one of your projects on a laptop, desktop, tablet, or smartphone, it is always readable and user-friendly. -->

## Objectives

* **Define** responsive design
* **Understand** the purposes and benefits of responsive design
* **Explain** the purpose of the viewport meta tag in context of responsive design
* **Utilize** media queries to change a web page's layout

<!--1:35 5 minutes -->

## What is responsive design?

> "Responsive Design" is the strategy of making a site that "responds" to the browser and device that it is being shown on... by looking awesome no matter what.

Or, the dryer Wikipedia definition:

> Responsive web design (RWD) is a web design approach aimed at crafting sites to provide an optimal viewing experience—easy reading and navigation with a minimum of resizing, panning, and scrolling—across a wide range of devices (from mobile phones to desktop computer monitors).

### More devices

Not that long ago building a successful online presence meant just ensuring that your website worked correctly in all the major desktop browsers. 

Fast forward to today (2017) and the desktop computer is dying, and more than 71% of the US population owns a smartphone.

* **195 million** tablet devices were sold in 2013.
* The number of active mobile devices and human beings crossed over somewhere around the [7.19 billion mark](http://www.independent.co.uk/life-style/gadgets-and-tech/news/there-are-officially-more-mobile-devices-than-people-in-the-world-9780518.html).
* New devices like iWatches are going to (try to) change the game as well.

<!--1:40 10 minutes -->

## Mobile is the ~~future~~ now!

> "Having a mobile friendly website is no longer just important, it’s critical." 

[Forbes Ecommerce Marketing Checklist for 2013](http://www.forbes.com/sites/brentgleeson/2013/03/14/ecommerce-marketing-checklist-for-2013/), four years ago


### Examples of responsive sites:

<!--Show these, shrink screen to demo responsiveness -->

- [Boston Globe](http://www.bostonglobe.com/)  
- [GA](https://generalassemb.ly/)

#### Non-responsive sites

You'll be hard-pressed to find a major website that doesn't deal with mobile devices somehow. For example, [Dave's EMS Website](http://www.davesems.com/).

<!-- CFU: Think-pair-share -->

<!--1:50 5 minutes -->

## The Web has always been responsive

From the beginning, the web has been meant to be shown on a variety of different screens. Text wraps, floats automatically position themselves based on screen size, and we've had percentage sizing in CSS basically forever.

If we go to this simple example, we see that floats reflow, depending on screen width:

http://codepen.io/jsera/pen/MaobYW

Likewise, the paragraphs remain at 50% of screen width, no matter what the screen width is.
Why is Dave's EMS site not responsive, then?

<!--1:55 5 minutes -->

## The Viewport

Default responsive design works to a degree, but we'd really like a few more tools for changing layout based on screen size.

Everyone's used Pinch to zoom on their phone. The portion of the page you see while panning is called the viewport. Open up Dave's EMS site, open your Chrome Developer Tools, and click the phone icon next to that. What a horrible way to browse!

When designing sites for mobile, we can make viewport match the page width on load by using the viewport tag:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Great! But still completly useless to a site with no media queries in it. 

<!--2:00 5 minutes -->

## Media Queries

Media queries are simply a way to conditionally apply styles based on the device the page is being displayed on.

We already know that if we do something like this:

```css
p {
  color: red;
}

p.blue_text {
  color: blue;
}
```

By default, all `p` tags will have red text, unless they have the class `blue_text`, in which case, the text will be blue. We can do a similar thing with media queries:

```css
p {
  color: blue;
}

@media (min-width: 600px) {
  p {
    color: red;
  }
}
```

Now, all `p` tags will be red, until the screen size reaches 600px, at which point they will turn blue.

A potentially more useful example would be to list all items inline until a certain screen size, then revert the list items to block, causing them to stack.

```css
li {
  display: block;
  color: blue;
}

@media (min-width: 600px) {
  li {
    display: inline-block;
    color: red;
  }
}
```

## Mobile First

You notice how the above looks slightly backwards? We're declaring media queries that affect the page based on it's minimum size. That's because we're using a mobile-first strategy. If you design for large screens first, you put yourself in a position where you must consolidate lots of information into a smaller screen, causing you to either smush or remove sections of content. If, instead, you design your smallest experience first, you can add more design to your larger screen like frosting on the cake (or don't - whitespace is nice too)! That way, even if we don't have time to implement everything, everyone gets a good experience.

That's the reason we're using the min-width query instead of the max-width query. This means the styles aren't applied unless, at minimum, the screen is X pixels wide.

> Note: Looking to apply a hyper-specific media query? You can add more arguments to your query, such as `@media (min-device-width: 768px) and (max-device-width: 1024px)`, which would target the size of a landscape-oriented iPad.

<!--2:05 30-40 minutes -->

## Independent Practice

Create a responsive page for our class.

Here's an example of the mobile view from a previous class:

<!-- Replace with our class -->

![mobile page design](https://github.com/den-wdi-1/css-responsive-design-and-flexbox/blob/master/images/mobile_view.png)

And this is the desktop view:
![desktop page design](https://github.com/den-wdi-1/css-responsive-design-and-flexbox/blob/master/images/desktop_view.png) 

### Create a mobile view
Add the following elements to an HTML page:

1. The team image (the JPG in the top folder of this repo) below the h1 tag
2. A course summary 
  1. A h2 tag containing ``WDI Denver, Da Best``
  2. An unordered list with the following bullets:
    1. ``Learn Full Stack programming``
    2. ``Explore MEAN Stack, Express, and more``
    3. ``Create a developer portfolio``
  3. The background should be blue for the course summary 
  4. The text color for the course summary should be white
3. Use an ipsum generator, [http://generator.lorem-ipsum.info/](http://generator.lorem-ipsum.info/)
to create 3 paragraphs of text and add it under the course summary.

### Add the responsive formatting

1. Update the background to red and color to black if you're not on a mobile device.
2. Make the first 2 elements(the course summary and the image) appear on the same 
(horizontal) line only for non-mobile viewers. Make sure the course summary is on the left. 

### Bonus

<!--Fix this -->
3. Add ``Team Name!`` to the image

## Useful Links

[7 Habits of Highly Effective Media Queries](http://bradfrost.com/blog/post/7-habits-of-highly-effective-media-queries/)

[Media Queries for Standard Devices](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/)

[Why You Don't Need Device Specific Breakpoints](https://responsivedesign.is/articles/why-you-dont-need-device-specific-breakpoints)

[Brad Frost - Navigation Patterns for Responsive Design](http://bradfrost.com/blog/web/complex-navigation-patterns-for-responsive-design/)


## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
