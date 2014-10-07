[![Dependencies Status](https://depending.in/gremo/CiconiaBundle.png)](http://depending.in/gremo/CiconiaBundle)

# CiconiaBundle
Symfony 2 bundle for Ciconia Markdown parser for PHP.

## Installation
Add the bundle in your `composer.json` file:


```js
{
    "require": {
        "gremo/ciconia-bundle": "dev-master"
    }
}
```

Then enable the bundle in the kernel:

```php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Gremo\CiconiaBundle\GremoCiconiaBundle(),
        // ...
    );
}
```

## Configuration
Configuration is optional, **extensions are disabled** by default:

```yml
# GremoCiconiaBundle Configuration
gremo_ciconia:
    renderer: ~ # Or null or "html" or "xhtml"
    extensions: ~ # Enable all with true or null (false to disable)
```

To selectively enable an extension:

```yml
# GremoCiconiaBundle Configuration
gremo_ciconia:
    # ...
    extensions:
        fencedCodeBlock: ~ # Or true or null (false to disable) 
        # ...
```

## Usage
Get the `ciconia` service from the service container:

```php

/** @var \Ciconia\Ciconia $ciconia */
$ciconia = $container->get('ciconia');

// Refer to kzykhys/Ciconia for examples
$html = $ciconia->render('Markdown is **awesome**');

// <p>Markdown is <em>awesome</em></p>
```
## Dependency Injection Tags
Give the service a tag named `ciconia.extension` to automatically registered it as an extension.