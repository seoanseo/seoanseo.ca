---
ID: 6356
post_title: >
  Capturing Google Ad Campaign Info In A
  Contact Form
author: SEO Anseo
post_excerpt: ""
layout: post
permalink: >
  https://seoanseo.ca/capturing-google-ad-campaign-info-in-a-contact-form/
published: true
post_date: 2018-11-17 12:13:26
---
<h2>The Problem:</h2>
A client is getting 20 leads a day through their contact form. Some of them more qualified than others. We want to determine if there's a correlation between certain campaigns and the qualities of the leads.

Contact form submission is being tracked by Google Ads (still hard not to say AdWords since they changed the name!) so we know which campaigns are generating leads. But there's no immediate way to tell which of those leads were qualified and which were time-wasters.

We know which campaigns are bringing in the most leads, but we want to know which are bringing in the best!

<hr class="wp-block-separator">

<h2>The Solution:</h2>
A field on the email you get that indicates which campaign led to that specific email.

<hr class="wp-block-separator">

<h2>Tools:</h2>
- Google Ads
<del datetime="2018-11-13T20:43:09+00:00">- Google AdWords Editor (will really speed up adding variables to ad urls)</del> Turns out we don't need this any more as URL Options can be set at campaign level, with the added bonus of your ads not having to be resubmitted for approval.
- <a href="https://contactform7.com/">Contact Form 7</a>
- <a href="https://wordpress.org/plugins/contact-form-7-dynamic-text-extension/">Contact Form 7 Dynamic Text Extension</a>
- A Child Theme (Optional, but you'll save yourself having to do this all over again when your theme and/or plugins get updated.

<hr class="wp-block-separator">

<h2>Super Simple Version:</h2>
<h3>1. Add variables to ad URLs that indicate which campaign brought a lead to the site.</h3>
We used 'cid' (which stands for campaign id) but you could use whatever you want so long as your consistent in the steps that follow.
<ul>
 	<li>In your Google Ads dashboard click into a Campaign, then Settings&gt;Additional Settings&gt;Campaign URL Options</li>
 	<li>Set up your marker. You can set up <a href="https://support.google.com/google-ads/answer/6305348?co=ADWORDS.IsAWNCustomer%3Dfalse&amp;hl=en">all sorts awesome dynamic variables</a> to get more detail but we're going to keep it super simple and go with something like 'cid={campaignid}' which will attach the Campaign ID assigned by Google Ads to your final url. Or to make it even simpler, we can set the marker ourselves so in our example we'll set it to 'cid=LST' (standing for 'Lead Search Toronto'). That way we get an instantly recognizable string rather than a series of numbers we'd have to cross reference.</li>
 	<li>Hit the test button to see that you've set up your tracking correctly, then on to the contact form setup</li>
</ul>
<img class="alignnone size-large wp-image-6480" src="https://seoanseo.ca/wp-content/uploads/2018/11/Screenshot-2018-11-30-17.58.43-1024x465.jpg" alt="" width="859" height="390">
<h3>2. <a href="https://wordpress.org/plugins/contact-form-7-dynamic-text-extension/" target="_blank" rel="noopener">Set up Contact Form 7 Dynamic Text Extension</a></h3>
<h3>3. Add your dynamic text field to your contact form.</h3>
Ultimately we're going to make this a hidden field but we'll leave it visible while we're testing. To do this we'll use the shortcode:

<code>[dynamictext urldata "CF7_GET key='cid'"]</code>

We'll put this in our wpcf7 contact form.

<img class="alignnone size-large wp-image-6482" src="https://seoanseo.ca/wp-content/uploads/2018/11/Screenshot-2018-11-30-17.34.35-1024x437.jpg" alt="" width="859" height="367">

Baring in mind hear that if you didn't use 'cid' as your query parameter you need to change it in this shortcode too.

As with all Contact Form 7 fields, remember to add it to the 'Mail' tab as well as the 'Form' tab or you won't get any info in the message sent to you. So in the above example we'll want to add <code>[urldata]</code> to the Mail tab somewhere.
<h3>4. Test</h3>
Go to your page with the contact form adding a test query string (e.g. www.yoursite.com/?cid=AWESOME)

You should see your dynamic text field is now filled with AWESOME

<img src="https://seoanseo.ca/wp-content/uploads/2018/11/ezgif-5-bc0f83eba888.gif" alt="AdWords Tracking in WPCF7" width="100%">
<h3>5. Make the field hidden</h3>
Change <code>[dynamictext urldata "CF7_GET key='cid'"]</code> to <code>[dynamichidden urldata "CF7_GET key='cid'"]</code> in your contact form.
<h3>6. Go home, you're donezo.</h3>
Pretty straightforward, right?

The drawback to this method is that the string query will only exist on the page the user lands on, so if they navigate elsewhere on your site before deciding to contact you, you won't get the info.

<hr class="wp-block-separator">

<h2>More Thorough Version:</h2>
In order to get around the drawback of the above simple version above we're going to save some session variables and then create a custom callback to them in wpcf7.
<h3>1. Create A Session Variable</h3>
First we want to turn our cid query string above into a session variable that will follow the user from page to page while they're browsing your website. To do this we're going to start a session in the header of your site (put it in your child theme to avoid it being overwritten on update!)

<code>	&lt;?php
session_start();
function setseshvars(){
if (!isset($_SESSION['done'])) { // We only want to run this once per browsing session
$_SESSION['campaignid'] = $_GET["cid"]; // Captures the 'cid' that we placed in our Google ad final url and sets it as a session variable called 'campaignid'
$_SESSION['done'] = 1; // Sets a value for 'done' so this won't run again when we load another page.
}
}
setseshvars();
?&gt;</code>
<h3>2. Create A Shortcode to capture the session variable</h3>
For this we're going to want to set up a shortcode through our child theme's functions.php that we'll be putting in our contact form.

Here I'm using a modified version of one of the shortcodes set up by Contact Form 7 Dynamic Text Extension

<code>
/* Insert a $_SESSION variable */
function cf7_sess($atts){
extract(shortcode_atts(array(
'key' =&gt; 0,
), $atts));
$value = '';
if( isset( $_SESSION[$key] ) ){
$value = urldecode($_SESSION[$key]);
}
return $value;
}
add_shortcode('CF7_SESSION', 'cf7_sess');
</code>

Basically it's going to call a session variable instead of a query from the url.
<h3>3. Add your shortcode to the contact from.</h3>
Something like:
<code>[dynamictext sessiondata "CF7_SESSION key='campaignid'"]</code>

And don't forget to include <code>[sessiondata]</code> in the mail section somewhere so that it gets sent to you.
<h3>4. Test it out!</h3>
For the purposes of testing you could make your both use both the URL query string field ans the session data field and set the both to be visible by using the dynamictext shortcode.

Go to the site with a test query string again (e.g. www.yoursite.com/?cid=AWESOME) then jump to your contact form. You should see that both of them show your variable (e.g. AWESOME)

<img class="wp-image-6519" src="https://seoanseo.ca/wp-content/uploads/2018/12/ezgif-2-756d0fc8d262.gif" alt="">

Then go to another page that also has your contact form on it. You'll notice that the query string box is now empty but the session variable box remains set.

<img class="wp-image-6519" src="https://seoanseo.ca/wp-content/uploads/2018/12/ezgif-2-e7d0978f2086.gif" alt="">
<h3>5. Make your fields hidden again.</h3>
Keep it all neat and tidy.
<h3>6. Buy yourself a beer, celebrate!</h3>
Good job! Now you're ready to capturing that sweet, sweet Google Ad campaign info in your contact form.

<hr class="wp-block-separator">

<h2>Other Options:</h2>
- You could use Contact Form 7's built in Mail 2 to send yourself two copies of the email, one with the added info and one without.
That way when you reply to the client you won't be sending any messy varible info.

- For bonus points you could use filters in gmail or gsuite to:
1. Separate your Mail 2 versions, making it clearer which ones are for data purposes (bypassing the inbox) and which one's are to be replied to.
2. Separate out mail by campaign.
A tidy inbox with mail filtered by campaign can tell you a story about what's going on even with just a glance.

- I'm toying around with using {loc_physical_ms}

{loc_physical_ms} is pretty cool, it can tell you where the physical click happened. The only issue is that it'll echo a numerical value that corresponds to a location in a table of locations Google has. I'd probably want that to correspond to the name of the place in the email. I'm thinking you could have hidden checkboxes, the value of which would be the loc_physical_ms numeric value, but I'd need to think about it a bit more.

<hr class="wp-block-separator">