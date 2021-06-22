# dynamic-slick-slider-shopify
Dynamic Section for Product Slider with Slick in Shopify

=====================================================================

It Will add a custom section to your theme customization part, which will reflect on your Index page of store.

First step, you should have 'Slick Slider' library in your Assets folder of the theme, you can download the files and upload inside Assets, if you don't have. Then, open 'theme.liquid' file and paste the following code before </head> tag:

{% if template == 'index' %}
{{ 'slick.css' | asset_url | stylesheet_tag }}
{{ 'slick-theme.css' | asset_url | stylesheet_tag }}
{% endif %}

And below code before </body> tag:

{% if template == 'index' %}
<script type="text/javascript" src="//code.jquery.com/jquery-1.11.0.min.js"></script>
<script type="text/javascript" src="//code.jquery.com/jquery-migrate-1.2.1.min.js"></script>
{{ 'slick.min.js' | asset_url | script_tag }}
{% endif %}

Now, scroll to the 'Sections', create a new section 'featured-collection-slider.liquid' and copy the code inside this section of file present here with same name.

Then, open 'theme.css' file and paste the following code:

.product-slider {padding: 25px; overflow: hidden;}
.product-slider .slick-track {display: flex;}
.product-slider .product-card {width: 100%;}
.product-slider .slick-prev {left: 0; z-index: 999;}
.product-slider .slick-next {right: 0; z-index: 999;}

Then, open 'theme.js' file and paste the following code:

$(document).ready(function() {
  $('.product-slider').each(function() {
    var num_slides = 2;
    if(window.innerWidth >= 750) {
    	var num_slides = $(this).data('slides');
    }
    $(this).slick({slidesToShow:num_slides, infinite:true, autoplay:false, arrows:true});
  });
});

Then, go to the 'Customize Theme', add section, you will find our newly created section, just add it their by selecting options available.

Thank You.
