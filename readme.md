![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

<!--1:30 5 minutes -->

#Responsive Design

<!--Hook: Raise your hand if you've ever opened a webpage on your phone, and it looks ugly?  Buttons all over the place, text falling off the screen?  You are not alone.  The purpose of Responsive Design is to solve this problem, so whether you are looking at one of your projects on a laptop, desktop, tablet, or smartphone, it is always readable and user-friendly. -->

##Objectives

* **Define** responsive design
* **Understand** the purposes and benefits of responsive design
* **Explain** the purpose of the viewport meta tag in context of responsive design
* **Utilize** media queries to change a web page's layout

<!--1:35 5 minutes -->

##What is responsive design?

> "Responsive Design" is the strategy of making a site that "responds" to the browser and device that it is being shown on... by looking awesome no matter what.

Or, the dryer Wikipedia definition:

> Responsive web design (RWD) is a web design approach aimed at crafting sites to provide an optimal viewing experience—easy reading and navigation with a minimum of resizing, panning, and scrolling—across a wide range of devices (from mobile phones to desktop computer monitors).

### More devices

Not that long ago building a successful online presence meant just ensuring that your website worked correctly in all the major desktop browsers. 

Fast forward to today (2016) and the desktop computer is dying, and more than 71% of the US population owns a smartphone.

* **195 million** tablet devices were sold in 2013.
* The number of active mobile devices and human beings crossed over somewhere around the [7.19 billion mark](http://www.independent.co.uk/life-style/gadgets-and-tech/news/there-are-officially-more-mobile-devices-than-people-in-the-world-9780518.html).
* New devices like iWatches are changing the game as well.

<!--1:40 10 minutes -->

## Mobile is the future

> "Having a mobile friendly website is no longer just important, it’s critical." 

[Forbes Ecommerce Marketing Checklist for 2013](http://www.forbes.com/sites/brentgleeson/2013/03/14/ecommerce-marketing-checklist-for-2013/)


### Examples of responsive sites:

<!--Show these, shrink screen to demo responsiveness -->

- [Boston Globe](http://www.bostonglobe.com/)  
- [GA](https://generalassemb.ly/)

#### Non-responsive sites

You'll be hard-pressed to find a major website that doesn't deal with mobile devices somehow. Reddit isn't specifically responsive, but you do have the option of switching to a mobile-optimized site.

#### Exercise

If you look at the Reddit site on your phone, try hitting the hamburger menu in the top right corner, and selecting desktop site. How does this change your experience?

<!-- CFU: Think-pair-share -->

<!--1:50 5 minutes -->

## The Web has always been responsive

From the beginning, the web has been meant to be shown on a variety of different screens. Text wraps, floats automatically position themselves based on screen size, and we've had percentage sizing in CSS basically forever.

If we go to this simple example, we see that floats reflow, depending on screen width:

http://codepen.io/jsera/pen/MaobYW

Likewise, the paragraphs remain at 50% of screen width, no matter what the screen width is.

This works to an extent, but we'd really like a few more tools for changing layout based on screen size.

<!--1:55 5 minutes -->

## The Viewport

Everyone's used Pinch to zoom on their phone. The portion of the page you see while panning is called the viewport. Go to [the Lorem Ipsum Generator](http://www.lipsum.com), open your Chrome Developer Tools,
look for the magnifying glass in the upper left hand corner, and click the phone icon next to that. If you expand the phone window and shrink it down again, you'll notice that you only see a portion of the
page, and the rest is represented as a shadow outside the viewport.

When designing sites for mobile, we want to minimize this panning. We can make viewport match the page width on load by using the viewport tag:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

The user will still be able to pinch and zoom, and that's fine, but at least we can guarantee they will start in a reasonable state.

Some devices start out zoomed in, some don't, and in some cases, it's a browser setting, but using this ensures a consistent experience.

<!--2:30 5 minutes -->

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

By default, all p tags will have red text, unless they have the class blue_text, in which case, the text will be blue. We can do a similar thing with media queries.

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

Now, all p tags will be red, until the screen size reaches 600px, when they'll turn blue.

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

You notice how the above looks slightly backwards? That's because we're using a mobile-first strategy. Rather than designing for the biggest, most capable screens first,
and take things away, we aim for the smallest, least capable screens, ensure they have a good experience, then add things like frosting on a cake. That way, even if we don't
have time to implement everything, everyone gets a good experience.

This means using the min-width query instead of the max-width query. This just means the styles aren't applied unless, at minimum, the screen is X pixels wide.

<!--2:35 30-40 minutes -->

## Independent Practice

Create a responsive page for our class.

Here's an example of our mobile view:

<!-- Replace with our class -->

![mobile page design](https://github.com/den-wdi-1/css-responsive-design-and-flexbox/blob/master/images/mobile_view.png)

And this is our desktop view:
![desktop page design](https://github.com/den-wdi-1/css-responsive-design-and-flexbox/blob/master/images/desktop_view.png) 

### Create a mobile view
Add the following elements to an HTML page:

1. The team image (the JPG in the top folder of this repo) below the h1 tag
2. A course summary 
  1. A h2 tag ``WDI Denver, Da Best``
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
