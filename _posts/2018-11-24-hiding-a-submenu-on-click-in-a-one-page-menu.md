---
ID: 6465
post_title: >
  Hiding A Submenu On Click in A One Page
  UberMenu
author: SEO Anseo
post_excerpt: ""
layout: post
permalink: >
  https://seoanseo.ca/hiding-a-submenu-on-click-in-a-one-page-menu/
published: true
post_date: 2018-11-24 12:33:03
---
Ubermenu is awesome. It's incredibly versatile and makes the most beautiful wordpress menus out there.

In this quickie we're looking at a specific use case in which ubermenu needs a little tweak.

<hr class="wp-block-separator">

<h2>The Problem:</h2>
We want to use submenu items to link to different sections in a page (by id), which works great. The issue arises when your on the page itself. Because the submenu items aren't loading a new page but scrolling to a section the submenu remains open when you click it.

<img src="https://seoanseo.ca/wp-content/uploads/2018/11/uber-before.gif" alt="ubermenu submenu visible">

<hr class="wp-block-separator">

<h2>The Solution:</h2>
This simple bit of code removes the 'ubermenu-active' class from the parent item when the submenu item is clicked.

<code>jQuery(function($) {
$(".ubermenu-submenu li").click(function(){
$(this).parent().parent().removeClass("ubermenu-active");
});
}); </code>

<img src="https://seoanseo.ca/wp-content/uploads/2018/11/uber-after.gif" alt="ubermenu submenu visible">

Depending on your wordpress theme you may have a place to paste custom code. Otherwise you can put it in script tags in your header template.

<hr class="wp-block-separator">