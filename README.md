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
    {% javascripts '@LoamokSubformsMadeEasyBundle/Resources/public/js/dynamicSubforms.js' %}
      <script type="text/javascript" src="{{ asset_url }}"></script>
    {% endjavascripts %}
```