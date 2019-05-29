---
ID: 6741
post_title: Creating A Sticky Sidebar
author: SEO Anseo
post_excerpt: ""
layout: post
permalink: >
  https://www.seoanseo.dev.cc/creating-a-sticky-sidebar/
published: true
post_date: 2019-02-19 12:41:14
---
<!-- wp:paragraph {"fontSize":"medium"} -->
<p class="has-medium-font-size">A sticky sidebar both looks snazzy and stops your page from having great big stretches of whitespace on longer posts. But depending on their size and if their content is variable, they can sometimes be tricky to implement.<br></p>
<!-- /wp:paragraph -->

<!-- wp:button {"backgroundColor":"vivid-red","textColor":"very-light-gray","className":"is-style-squared"} -->
<div class="wp-block-button is-style-squared"><a class="wp-block-button__link has-text-color has-very-light-gray-color has-background has-vivid-red-background-color" href="#bestest">Take me to your bestest method</a></div>
<!-- /wp:button -->

<!-- wp:paragraph -->
<p>

Quick note on the below. I'll be writing jQuery each time instead of $ to avoid <a target="_blank" href="https://digwp.com/2011/09/using-instead-of-jquery-in-wordpress/" rel="noreferrer noopener">conflicts with Wordpress's jQuery</a>. I usually find it easiet if I'm just working on something short.<br>You can feel free to wrap you code in:

</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code {"language":"jscript","makeURLsClickable":false} -->
<pre class="wp-block-syntaxhighlighter-code">jQuery(function($) {

});</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>and then replace 'jQuery' with '$' if you prefer.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>The jQuery scrollTop Method</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>This is the older method, but we'll put it here for posterity.<br><br>All of the below methods apply to the theme we use as a base for most of our site (x theme). It uses aside tags for the sidebar, but your theme may use something different (a div with a sidebar class?)<br></p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>The jQuery</h3>
<!-- /wp:heading -->

<!-- wp:html -->
[code lang="js"]
// sticky sidebar

function sticky_side() {
//Get the scroll position and the position of the bottom of the window
var winTop = jQuery(window).scrollTop();
var winBot = winTop + jQuery(window).height();
//Get the top and bottom positions of our sidebar
var elementTop = jQuery('aside').offset().top;
var elementBot = elementTop + jQuery('aside').height();
//Get the top and bottom position of our header elements
var headTop = jQuery('bg_featured').offset().top;
var headBot = headTop + jQuery('bg_featured').height();

//Get the top position of our footer
var footTop = jQuery('footer').offset().top;

//We want the sidebar to be fixed once the bottom of it comes on screen
if (elementBot &amp;amp;lt; winBot) {
			jQuery('aside').addClass('sticky-sidebar');
        }
// When the footer comes on the screen, we do not want the sidebar to be fixed anymore or it will overlap
if (elementBot &amp;amp;gt; footTop) {
			jQuery('aside').addClass('bottomed-sidebar');
        } 
// When scrolling back up, we want the sidebar to be fixed again
if (winBot &amp;amp;lt; footTop) {
			jQuery('aside').removeClass('bottomed-sidebar');
        }
// When we return to the top we don't want the sidebar to be fixed anymore or it will overlap over header content
if (elementTop &amp;amp;lt; headBot) {
            jQuery('aside').removeClass('sticky-sidebar');
        } 
}
jQuery(window).scroll(sticky_side);
[/code]
<!-- /wp:html -->

<!-- wp:heading {"level":3} -->
<h3>The CSS</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Here we need to flesh out the classes we created above.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>We also have to make sure our content container is set to relative so that our "bottomed-sidebar" class doesn't just fly off the page.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
[code lang="css"]
/* sticky sidebar */
.single-post .x-container.max.width.offset {
    position: relative;
}
.sticky-sidebar
{
    position: fixed;
    bottom: 1.45%;
    right: 2.6%;

}
.bottomed-sidebar
{
position: absolute;
    bottom: 0.45%;
    right: 0%;
}
[/code]
<!-- /wp:html -->

<!-- wp:heading {"level":3} -->
<h3>Issues With This Method</h3>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li>It's a bit fiddly. You're going to need to figure out positioning for both the fixed and position absolute and get them to match up.</li><li>Using scroll events can be cumbersome and may slow down your page.</li></ul>
<!-- /wp:list -->

<!-- wp:heading -->
<h2>CSS Position Sticky Method<br></h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Position sticky is a relatively new way to position elements with css. It's sort of a hybrid of  position:relative and postion:fixed. It operates as the former until the </p>
<!-- /wp:paragraph -->

<!-- wp:html -->
[code]aside {
  position:sticky;
position: -webkit-sticky;
  position: -moz-sticky;
  position: -ms-sticky;
  position: -o-sticky;
  top: 0;
}

/* Also note that sticky won't work if an ancestor has overflow hidden so we'll override that */

body, div#top {
    overflow: visible;
}
[/code]
<!-- /wp:html -->

<!-- wp:heading -->
<h2>Issues With This Method</h2>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li>Position sticky will get messed up if any of it's ancestors has an overflow:hidden;</li></ul>
<!-- /wp:list -->

<!-- wp:paragraph -->
<p>In our case, our theme sets:</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
[code]body{
overflow-x:hidden;
}[/code]

So we had to override that with:

[code]body{
overflow-x:visible;
}[/code]

Which has had no ill effects. But this is likely because them theme is put together well enough, so we're not encountering any overflows anyway.
<!-- /wp:html -->

<!-- wp:list -->
<ul><li>The sticky position is fixed.</li></ul>
<!-- /wp:list -->

<!-- wp:paragraph -->
<p>You have to set a fixed position to tell the element where to stick (top:0px;).<br>Which is fine if your element is both smaller than the window height and of a fixed size.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>If it's bigger than the window size (as our sidebars often are), it's likely going to 'stick' the top part of the sidebar content to the screen until you get top the bottom part of the page. Or worse still it may 'stick' somewhere in the middle of the sidebar content. </p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>You might be able to work around this if your sidebar was of a fixed size by fiddling around with your top value. say if you had a sidebar that was 900px tall, you could set a top value of -450px. That way the sidebar would only 'stick' once 450px of it was off screen.<br><br>But that won't be of any help if your sidebar content is of variable height. Furthermore, you might still have issues with where the sidebar sticks on varying screen sizes. <br>It's not the end of the world, the content at the bottom of the sidebar will show up once the user scrolls far enough. But it's not the smoothest looking implimentation. </p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2 id="bestest">The jQuery/CSS Position Sticky Method<br></h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>This clean little solution is the best of both worlds. It avoids all the clunkieness of the jQuery scroll method. But it also dynamically figures out the height of our sidebar, so it knows just where to 'stick' it so that it holds exactly when the bottom of the sidebar comes on screen and not before.<br><br>It'll achieve this by using jQuery to get the height of the sidebar and then subtracting the height of the window from it. Then it'll set the top value of the sidebar to minus the remainer (plus twenty in our code to give us a nice little bit of margin, not just content flush to the window)</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
[code]
// Blog sidebar

var sideBar = jQuery('aside').height();
var winHeight =  jQuery(window).height();
var newHeight = (sideBar - winHeight) +20;
var minus = newHeight * -1;
jQuery('aside').css('top',minus);
[/code]
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>Don't forget to add your position sticky to your CSS</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
[code]aside {
  position: sticky;
  position: -webkit-sticky;
  position: -moz-sticky;
  position: -ms-sticky;
  position: -o-sticky;
}

/* Also note that sticky won't work if an ancestor has overflow hidden so we'll override that */

body, div#top {
    overflow: visible;
}
[/code]
<!-- /wp:html -->