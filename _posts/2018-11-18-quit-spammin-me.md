---
ID: 6393
post_title: 'Quit Spammin&#8217; Me'
author: SEO Anseo
post_excerpt: >
  Blocking those pesky contact form spam
  messages!
layout: post
permalink: https://seoanseo.ca/quit-spammin-me/
published: true
post_date: 2018-11-18 22:13:09
---
<!-- wp:paragraph {"fontSize":"medium"} -->
<p class="has-medium-font-size">Contact form spam is not only annoying, it can sometimes be incredibly detrimental to your business. In these article we'll go through a few methods to combat it.</p>
<!-- /wp:paragraph -->

<!-- wp:button {"backgroundColor":"vivid-red","textColor":"very-light-gray","className":"is-style-squared"} -->
<div class="wp-block-button is-style-squared"><a class="wp-block-button__link has-text-color has-very-light-gray-color has-background has-vivid-red-background-color" href="#121gigawatts">I'm from the future. take me to the modern solution</a></div>
<!-- /wp:button -->

<p>When it comes time to running your own website, one of the more annoying nuisances you can encounter is spam coming at you from your site. You’re fresh and ready for emails to start streaming in from customers eager to do business with you when you get:</p>
<blockquote>
<p>"I am love you opinion on webite, could you please advise on this:<br>&lt;!---insert link to black market Viagra website here ---&gt;"</p>
</blockquote>
<p>Or worse still, the old:</p>
<blockquote>
<p>"Your site is doing terribly and not showing up in Goolge, but we at Spammy &amp; Spamster Web Design can fix it for you"</p>
</blockquote>
<p>That last one always makes me laugh. How exactly have they found you? A Google for sites that don’t show up in Google???</p>
<p>What’s to be done about these spammy jerkbots?</p>
<p>You’ll hear some hear some mad advice about these sorts of thing, mad and/or outdated;</p>
<p></p>
<p></p>
<ul>
<li><em>Don’t put your email address up on your site</em></li>
<li><em>Don’t have a contact form on your site</em></li>
<li><em>Use a captcha on a contact form if you must have one</em></li>
</ul>
<p></p>
<p></p>
<p>Well, frankly these are some pretty lame solutions. Let's take a look at why.</p>
<h2>Don’t put your email address up on your site???</h2>
<p>You don’t see it as much nowadays, but every now and then you’ll still see people using <em>myemail(at)mydomain.com</em> as a method to thwart the spambots. Which…well, sure it may work. But you end up looking like a total amateur and completely sacrifice user experience in the process. In this day and age I’m not going to bother retyping it, I’m just moving on.</p>
<p>The smarter fix for this is the javascript replacement method. One of the themes we use has this built in, but you can also <a href="http://stackoverflow.com/questions/483212/effective-method-to-hide-email-from-spam-bots" target="-blank">DIY it.</a></p>
<p>The basic idea is this:</p>
<p>The html shows something like myemail*mydomain.com, but the javascript fiddles it so to human eyes it looks like myemail@mydomain.com and the click on the link will also go to that address, but all the spambots will see when they try to scrape your site is myemail*mydomain.com and move quietly on its way.</p>
<h2>Don’t have a contact form on your site???/Use a captcha on a contact form if you must have one???</h2>
<p>To be honest if your web designer is telling you not to put a contact form on your site because they’re "magnets for spam" I’d question how current their knowledge is.</p>
<p>We use <a href="https://wordpress.org/plugins/contact-form-7/" target="_blank" rel="noopener">Contact Form 7</a>, a hugely versatile contact form plugin for wordpress.</p>
<p>[caption id="attachment_1927" align="alignright" width="300"]<a href="https://wordpress.org/plugins/contact-form-7/" target="_blank" rel="noopener"><img class="size-medium wp-image-1927" src="http://seoanseo.ie/wp-content/uploads/2016/04/banner-1544x500-300x97.png" alt="Contact Forms Used by SEO Anseo Ireland" width="300" height="97"></a> Contact Form 7 is a hugely versatile plugin with new addons being created all the time by creative people in the community[/caption]</p>
<p>Out of the box it doesn’t have any spambot jedi mind tricks, but as it’s sort of the industry standard for wordpress contact forms there have been lots of addons built for it.</p>
<p>The one that’s saved us the most headaches? <a href="https://wordpress.org/plugins/contact-form-7-honeypot/" target="_blank" rel="noopener">Contact Form 7 Honeypot</a></p>
<p>What this genius little plugin does is add an input field to your contact form that is invisible to humans but "visible" to spambots. Because they don’t know any better the bots assume they have to put something in that field and BOOM, give themselves away and the attempt will never make it to your inbox.</p>
<p>This is neat and super user-friendly alternative to the ugly as hell, outdated flow-killing captchas.<br>I’ve never actually abandoned a website because I had to put in a captcha, but I’ve sure though about it (tickemaster, I’m looking at you! Why do I have to put it in 20 times to compare tickets!!!)</p>
<p>Now Googles (relatively) new No CAPTCHA reCAPTCHA on the other had I could get behind a little more. It uses behavioural analysis, so it’s often the case that the customer can verify that they’re not a robot with one simple click.</p>
<p>But for the moment I’m sticking with the Honeypot solution, it’s got zero impact on the customers journey, which is exactly what you want.</p>
<h2>The Nuclear Option</h2>
<p>[caption id="attachment_1929" align="alignleft" width="200"]<img class="size-thumbnail wp-image-1929" src="http://seoanseo.ie/wp-content/uploads/2016/04/bouncer4_3263188c-150x150.jpg" alt="SEO Anseo block traffic by countries" width="200" height="200"> It may not suit everyone to block all traffic for a given country, but if it does it's a great time saver.[/caption]</p>
<p>No method will be fool proof and every now and then something can slip through, in particular <a href="https://blog.akismet.com/2010/04/22/state-of-web-spam/" target="_blank" rel="noopener">human-posted spam</a> can’t be tackled by honeypots or captcha’s of any kind.</p>
<p>Here’s where you’re faced with a big choice and it’s a choice that’s not going to suit everyone, but for us it’s been effective in blocking even the human-posted spam. It’s also pretty good as a method for blocking hacking attempts.</p>
<p>Over the last month or so we got dribs and drabs of spam coming in despite the above blocking methods. They’d come in groups of three, which is probably an indicator of being human in origin (getting more bang for your buck from the low-paid hired spammers)</p>
<p>More than a little annoyed, we took to our <a href="http://analytics.google.com" target="_blank" rel="noopener">Google Analytics</a> to see where this crap was coming from. We needed to look at the unfiltered view to see where all those shady referrals were coming from (stay tuned for our post on setting up Analytics filters, it’s important for getting a handle on where your audience is really coming from).</p>
<p>Sure enough, the hits that lead to the spam were coming from some shady "SEO ranker" type sites, looking for hits back. But the hostnames were correct, so they had actually visited the site and clicked through the form, etc.</p>
<p>The other crucial bit of information we take from the Analytics is the country of origin. Every one of the spam hits came from Russia.</p>
<p>Now luckily for us in this case, we’re a local business (meeting clients for a coffee in town is way cheaper than meeting them for a coffee in Moscow) so we’ve no need to be seen by by clients in Russia.<br>So, knowing that, we can wholesale block all traffic from that country.</p>
<p>To do this we head over to <a href="http://www.ip2location.com/free/visitor-blocker" target="_blank" rel="noopener">The IP2 Location Visitor Blocker</a>, select the country we want to block and paste their output into our .htaccess.</p>
<p>I like to use the built in .htaccess editor in <a href="https://yoast.com/wordpress/plugins/seo/" target="_blank" rel="noopener">Yoast’s SEO Plugin</a>, it’s slightly less tedious than accessing it via ftp. But word to the wise; if you’re not certain about what you’re doing go by ftp and keep a back-up copy of the file, white-screening your website is a very real possibility.</p>
<p><strong>Of course if you do business internationally this will be less of an option for you. You could instead pinpoint the IP addresses of the specific spam and block them one by one. </strong></p>
<p>So there we have it. All the tools and tricks you need to wage war on contact form spam.<br>Keep up the good fight and don’t let the spammers get you down!</p>
<p>Any other suggestions to fight contact form spam? Any war stories? Let us know below!</p>
<p>Oh yeah, and don't forget...if you need to give us a shout, just scroll a little further down to the contact form!</p>
<div class="container">&nbsp;</div>

<!-- wp:heading -->
<h2 id="121gigawatts">Modern Solution</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Nowadays Contact Form 7 has Google ReCaptcha Built in.</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<div class="schema-how-to wp-block-yoast-how-to-block"><p class="schema-how-to-description"></p> <ol class="schema-how-to-steps"><li class="schema-how-to-step"><strong class="schema-how-to-step-name">Set up a Google v3 reCAPTCHA<br></strong> <p class="schema-how-to-step-text">Go to <a href="https://www.google.com/recaptcha/" target="_blank">https://www.google.com/recaptcha/</a> to set it up and follow the instructions<br></p> </li><li class="schema-how-to-step"><strong class="schema-how-to-step-name">Enter your site key and secret key in WPCF7's integration section</strong> <p class="schema-how-to-step-text">You'll find this at YOURSITE.COM/wp-admin/admin.php?page=wpcf7-integration&amp;service=recaptcha&amp;action=setup</p> </li><li class="schema-how-to-step"><strong class="schema-how-to-step-name">That's it!</strong> <p class="schema-how-to-step-text">Simple.</p> </li><li class="schema-how-to-step"><strong class="schema-how-to-step-name">Hide reCAPTCHA badge</strong> <p class="schema-how-to-step-text">Some folks won't want that floating badge on every page of their site. You can hide it with some css<br>[code].grecaptcha-badge {
    display: none;
}[/code]<br>Of course you'll have to indicate to your users that you're using reCaptcha.</p> </li></ol></div>
<!-- /wp:html -->

<!-- wp:code -->
<pre class="wp-block-code"><code>You are allowed to hide the badge as long as you include the reCAPTCHA
branding visibly in the user flow. Please include the following text:

This site is protected by reCAPTCHA and the Google
    &lt;a href="https://policies.google.com/privacy">Privacy Policy&lt;/a> and
    &lt;a href="https://policies.google.com/terms">Terms of Service&lt;/a> apply.</code></pre>
<!-- /wp:code -->

<!-- wp:html -->
- <a target="_blank" href="https://developers.google.com/recaptcha/docs/faq">reCAPTCHA FAQ</a>
<!-- /wp:html -->

<!-- wp:paragraph -->
<p>Alternatively, you could allow the badge to show on your contact form page.</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code {"language":"css"} -->
<pre class="wp-block-syntaxhighlighter-code">.page-id-YOURCONTACTPAGE-ID .grecaptcha-badge {
    display: block;
}</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>Anyway, hopefully by now you're well on your way to blocking those pesky spammers.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Have a break and listen to some Tom Petty:</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p></p>
<!-- /wp:paragraph -->

<!-- wp:core-embed/youtube {"url":"https://www.youtube.com/watch?v=TCFAzPl1QmE","align":"wide"} -->
<figure class="wp-block-embed-youtube alignwide wp-block-embed"><div class="wp-block-embed__wrapper">
https://www.youtube.com/watch?v=TCFAzPl1QmE
</div></figure>
<!-- /wp:core-embed/youtube -->