sf_jquerySlider
===============

SF2 Bundle Allowing you to use jcobb/basic-jquery-slider

Installation
------------

### Add it to your composer.json : 
```yaml
{
    "require": {
        ...,
        "loamok/jqueryslider" : "dev-master"
    }
}
```

### Update your AppKernel.php :
```php
    public function registerBundles() {
        $bundles = array(
            ...,
            new Loamok\JQuerySliderBundle\LoamokJQuerySliderBundle(),
        );
```

Usage
-----
This bundle require Jquery 1.11.1 or compatible.

This bundle is usable with assetic.

Make sure you're correctly configure assetic to run in your bundle :

app/config/config.yml :
```yaml
# Assetic Configuration
assetic:
    bundles:
        ...
        - YourWonderfullBundle
```

Add Jquery to your layout.twig :
```html
    <script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
```

Add the ressources to your layout.twig :
```html
    {% stylesheets '@LoamokJQuerySliderBundle/Resources/public/css/bjqs.css' %}
        <link rel="stylesheet" href="{{ asset_url }}">
    {% endstylesheets %}
    {% javascripts '@LoamokJQuerySliderBundle/Resources/public/js/bjqs-1.3.min.js' %}
      <script type="text/javascript" src="{{ asset_url }}"></script>
    {% endjavascripts %}
```

In a view where you want to slide some pictures :
```html
<!--  Outer wrapper for presentation only, this can be anything you like but with a knowed id -->
    <div id="mySlide">
        <!-- start Basic Jquery Slider -->
        <ul class="bjqs">
            {# example with pictures from a 'Media' entity #}
            {% for media in medias %}
                <li><img src="{{ asset(media.webPath) }}" title="{{ media.alt }}"></li>
            {% endfor %}
        </ul>
        <!-- end Basic jQuery Slider -->
</div>
<!-- End outer wrapper -->
<!-- attach the functionality to your resources. -->
<script>
jQuery(document).ready(function($) {
      $('#mySlide').bjqs({
        animtype      : 'slide',
        height        : 320,
        width         : 620,
        responsive    : true,
        randomstart   : true
      });
    });
// more options on the original project : https://github.com/jcobb/basic-jquery-slider
</script>
```

Options

Here is a full list of all the possible parameters which can used to configure the plugin and their default values.
```html
<script>
    // width and height need to be provided to enforce consistency
    // if responsive is set to true, these values act as maximum dimensions
    width : 700,
    height : 300,

    // animation values
    animtype : 'fade', // accepts 'fade' or 'slide'
    animduration : 450, // how fast the animation are
    animspeed : 4000, // the delay between each slide
    automatic : true, // automatic

    // control and marker configuration
    showcontrols : true, // show next and prev controls
    centercontrols : true, // center controls verically
    nexttext : 'Next', // Text for 'next' button (can use HTML)
    prevtext : 'Prev', // Text for 'previous' button (can use HTML)
    showmarkers : true, // Show individual slide markers
    centermarkers : true, // Center markers horizontally

    // interaction values
    keyboardnav : true, // enable keyboard navigation
    hoverpause : true, // pause the slider on hover

    // presentational options
    usecaptions : true, // show captions for images using the image title tag
    randomstart : true, // start slider at random slide
    responsive : true // enable responsive capabilities (beta)
</script>
```