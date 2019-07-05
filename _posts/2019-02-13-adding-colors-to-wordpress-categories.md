---
ID: 6703
post_title: Adding Colors to WordPress Categories
author: SEO Anseo
post_excerpt: ""
layout: post
permalink: >
  https://www.seoanseo.dev.cc/adding-colors-to-wordpress-categories/
published: true
post_date: 2019-02-13 14:25:31
---
<!-- wp:paragraph -->
<p>I wanted to add a color to our blog categories (notice how each category tag has it's own color?)
</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>
The below code adds a new field to the post categories on the backend. I'm using it for color but you could use it for anything. You'll add it to the functions.php of your child theme.
</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>
Ultimately I'm going to swap out the text input for a color picker, but this is fine for the moment.
<br></p>
<!-- /wp:paragraph -->

<!-- wp:shortcode -->
[code lang="php"]
//Create Extra Category Field
function seo_tax_meta_adder($term) {
     
      $seo_color = get_term_meta($term-&amp;gt;term_id, 'seo_cat_col', true);
    ?&amp;gt;
       &amp;lt;tr class="form-field term-name-wrap"&amp;gt;
            &amp;lt;th scope="row"&amp;gt;&amp;lt;label for="name"&amp;gt;Color&amp;lt;/label&amp;gt;&amp;lt;/th&amp;gt;
            &amp;lt;td&amp;gt;&amp;lt;input type="text" name="seo_cat_col" id="seo_cat_col" value="&amp;lt;?php echo esc_attr($seo_color); ?&amp;gt;"&amp;gt;
        &amp;lt;p class="description"&amp;gt;&amp;lt;?php _e('Hex Please'); ?&amp;gt;&amp;lt;/p&amp;gt;&amp;lt;/td&amp;gt;
        &amp;lt;/tr&amp;gt;
 
    &amp;lt;?php
}
 
 
add_action('category_add_form_fields', 'seo_tax_meta_adder', 10, 2);
add_action('category_edit_form_fields', 'seo_tax_meta_adder', 10, 2);
 
 
//Save Extra Category Field
function seo_tax_meta_saver($term_id) {
 
    $seo_cat_col = filter_input(INPUT_POST, 'seo_cat_col');
 
 
    update_term_meta($term_id, 'seo_cat_col', $seo_cat_col);
 
}
 
add_action('edited_category', 'seo_tax_meta_saver', 10, 1);
add_action('create_category', 'seo_tax_meta_saver', 10, 1);
[/code]
<!-- /wp:shortcode -->

<!-- wp:paragraph -->
<p> Then we put the below wherever we want the color to show up: </p>
<!-- /wp:paragraph -->

<!-- wp:shortcode -->
[php]// We're using the Yoast 'Primary Category' feature. This part looks for the primary category
		$wpseo_primary_term = new WPSEO_Primary_Term( 'category', get_the_id() );
		$wpseo_primary_term = $wpseo_primary_term-&amp;gt;get_primary_term();
		$term = get_term( $wpseo_primary_term );
$category_display = $term-&gt;name;
			$category_link = get_category_link( $term-&gt;term_id );
			$lowercased = strtolower($category_display);
		$category_class = str_replace(" ","-",$lowercased);
// Then we echo our custom meta like so:
echo get_term_meta($term-&amp;gt;term_id, 'seo_cat_col', true);[/php]
<!-- /wp:shortcode -->

<!-- wp:paragraph -->
<p>

In our case we're using it for the bottom border of each category:
</p>
<!-- /wp:paragraph -->

<!-- wp:shortcode -->
[php firstline="87"]echo '&amp;lt;div class="'.$category_class.' category" style="border-bottom-color:'.get_term_meta($term-&amp;gt;term_id, 'seo_cat_col', true).';"&amp;gt;';
[/php]
<!-- /wp:shortcode -->

<!-- wp:paragraph -->
<p>If you're not using Yoast you could use the below code: </p>
<!-- /wp:paragraph -->

<!-- wp:html -->
[php]$category = get_the_category(); 
$term = $category[0];
		/* END TESTING */
/* $term = get_term( $wpseo_primary_term ); */
	$category_display = $term->name;
			$category_link = get_category_link( $term->term_id );
			$lowercased = strtolower($category_display);
		$category_class = str_replace(" ","-",$lowercased);[/php]
<!-- /wp:html -->