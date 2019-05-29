---
ID: 6609
post_title: >
  Setting Up A Multi-Service Booking
  System With Woocommerce
author: SEO Anseo
post_excerpt: >
  In which we create a booking page for
  multiple different services under one
  roof.
layout: post
permalink: >
  https://www.seoanseo.dev.cc/setting-up-a-multi-service-booking-system-with-woocommerce/
published: true
post_date: 2019-01-28 23:09:53
---
<p>We recently had the pleasure of working with the good folks over at <a href="https://pitchedperfect.ie">pitchedperfect.ie</a></p>
<p>They wanted a booking form for their Pamper Palour at festivals, where festival-goers can come to get glammed up to the nines with the option to book various treatments with either a make-up artist or a hair dresser.</p>
<p>So they needed a booking form that could accept bookings for the two different service providers (make-up &amp; hair) and then select specific treatments.</p>

<!-- wp:heading -->
<h2>Tools</h2>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li><a href="https://woocommerce.com/products/woocommerce-booking?aff=10948">Woocommerce Bookings</a></li><li><a href="https://woocommerce.com/products/product-add-ons/?aff=10948">Woocommerce Product Add-Ons</a></li><li>jQuery (We'll only need this if you have two different types of service provider, e.g. Make-up and Hair)</li></ul>
<!-- /wp:list -->

<!-- wp:heading -->
<h2>Steps</h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3>1. Set Up Your Plugins</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Nothing super complicated here. We're going to set up <a href="https://woocommerce.com/products/woocommerce-booking?aff=10948">Woocommerce Bookings</a> in the same way we would any plugin. We're only going to need <a href="https://woocommerce.com/products/product-add-ons/?aff=10948">Woocommerce Product Add-Ons</a> if our main services (or service providers in our case) have sub-categories or "sub-services" (add-ons!). With Pitched Perfect in our Make-up service provider offers Full Face Festival Make-Up or Eyes &amp; Jewels as options. The Hair Dresser service provider offers blow drying, plaits, blowdry with curls, etc.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>2. Add a 'Resource'</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Your 'resources' are the service providers you have. In the case of Pitched Perfect these were Make-Up and Hair Dresser. Hover over Bookings on the dashboard and click Resources</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":6614} -->
<figure class="wp-block-image"><img src="https://www.seoanseo.dev.cc/wp-content/uploads/2019/01/Screenshot-2019-01-28-19.53.05-1024x576.png" alt="" class="wp-image-6614"/></figure>
<!-- /wp:image -->

<!-- wp:html -->
<ol type="a"><li>Add a name for your service provider</li><li>Add the available quantity (in our case this represent the amount of make-up artists working)</li><li>Add a bookable date range for the resource (in our case it's going to be the specific dates of the festival</li></ol>
<!-- /wp:html -->

<!-- wp:image {"id":6617} -->
<figure class="wp-block-image"><img src="https://www.seoanseo.dev.cc/wp-content/uploads/2019/01/Screenshot-2019-01-28-20.18.38-1024x576.png" alt="" class="wp-image-6617"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Set up any other top level service providers. In our case the other service provider is the Hair Dresser.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>3. Set Up A Product</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Set up a product like you would any other. But set the product type to "Bookable Product". Then you'll be given options specific to bookable products.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Set your booking duration. This is what it sounds like - how long each booked block lasts. In out case 30 minutes.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>In order to add your resources (service providers) - tick the "has resources" box and go to the Resources tab below.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Add each resource and enter a label to tell customers to pick an option.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":6620} -->
<figure class="wp-block-image"><img src="https://www.seoanseo.dev.cc/wp-content/uploads/2019/01/Screenshot-2019-01-28-20.42.19-1024x576.png" alt="" class="wp-image-6620"/></figure>
<!-- /wp:image -->

<!-- wp:heading {"level":3} -->
<h3>4. Set Up Your Specific Services (Add-ons)</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>This is where the <a href="https://woocommerce.com/products/product-add-ons/?aff=10948">Woocommerce Product Add-Ons</a> plugin will come in. It's going to allow us to set up multiple services (technically as add-ons)</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Click on the Add-Ons tab and click the add field button.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>We want it to be checkboxes and a required field.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":6624} -->
<figure class="wp-block-image"><img src="https://www.seoanseo.dev.cc/wp-content/uploads/2019/01/Screenshot-2019-01-28-21.25.43-1024x576.png" alt="" class="wp-image-6624"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Then set up all of your options and prices (for all/both service providers). You'll notice below that we've set up options that correspond to the service providers. These are optional. In our case we used some css to style these as headers.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>5. Use jQuery To Hide Services That Don't Apply To The Service Provider Chosen</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>At this point if you click into the product/booking form you'll notice that all the add-ons/services show up, even for the service provider that the add on doesn't apply to. This will be confusing for customers, so we want to hide non-applicable services based on what service provider is selected in the dropdown above. This is because  <a href="https://woocommerce.com/products/product-add-ons/?aff=10948">Woocommerce Product Add-Ons</a>  and  <br><a href="https://woocommerce.com/products/woocommerce-booking?aff=10948">Woocommerce Bookings</a>  aren't set up to natively integrate like this (yet? Maybe it could be suggested <a href="http://ideas.woocommerce.com">here</a>)</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>In the meantime, we don't want this to be confusing for customers, so we want to hide non-applicable services based on what service provider is selected in the dropdown above.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>To do this we're going to set up some custom jQuery. It's going to target the resource dropdown ( #wc_bookings_field_resource ) and look for the word 'make' as in make-up and if that's selected we'll hide all the options that don't apply to it. Use inspect element in your browser to determine the class of the items you want to hide</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Here's the jQuery we used. You'll obviously need to adjust it to match your use case, service names, etc.</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>// Pamper Service Switcher 

jQuery( "#wc_bookings_field_resource" ).ready(function() {
    var selected = jQuery('#wc_bookings_field_resource option:selected').text();
    var pattern = /Make/;

//returns true or false...
var exists = pattern.test(selected);

if(exists){
  jQuery('.make-up, .full-face-festival-make-up, .eyes-jewels').css("display","block");
    jQuery('.hair-dresser, .straight-blow-dry, .curly-blow-dry, .blow-dry-hair-with-extensions, .plaits, .curls-plaits').css("display","none");
}else{
  jQuery('.hair-dresser, .straight-blow-dry, .curly-blow-dry, .blow-dry-hair-with-extensions, .plaits, .curls-plaits').css("display","block");
  jQuery('.make-up, .full-face-festival-make-up, .eyes-jewels').css("display","none");
}
});

jQuery( "#wc_bookings_field_resource" ).change(function() {
    var selected = jQuery('#wc_bookings_field_resource option:selected').text();
    var pattern = /Make/;

//returns true or false...
var exists = pattern.test(selected);

if(exists){
  jQuery('.make-up, .full-face-festival-make-up, .eyes-jewels').css("display","block");
    jQuery('.hair-dresser, .straight-blow-dry, .curly-blow-dry, .blow-dry-hair-with-extensions, .plaits, .curls-plaits').css("display","none");
	jQuery('input[value="hair-dresser"], input[value="straight-blow-dry"], input[value="curly-blow-dry"], input[value="blow-dry-hair-with-extensions"], input[value="plaits"], input[value="curls-plaits"]').prop('checked', false);
}else{
  jQuery('.hair-dresser, .straight-blow-dry, .curly-blow-dry, .blow-dry-hair-with-extensions, .plaits, .curls-plaits').css("display","block");
  jQuery('.make-up, .full-face-festival-make-up, .eyes-jewels').css("display","none");
  jQuery('input[value="make-up"], input[value="full-face-festival-make-up"], input[value="eyes-jewels"]').prop('checked', false);
}
});</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>Now when your customers book an appointment on the 25th with your Hair Dresser, there won't be any confusion about which services they provide.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>There you go, you've jut set up a multi-service booking system for woocommerce!</p>
<!-- /wp:paragraph -->