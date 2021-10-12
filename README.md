# php-feather

PHP Library for [Feather](https://feathericons.com/).

For more information on Feather itself, please refer to their [README](https://github.com/feathericons/feather).

## Installation

Install `php-feather` using [Composer](https://getcomposer.org/).

```bash
composer require pixelrobin/php-feather
```

## Usage

### Icons

`Icons` are retrieved from an `IconManager`.

```php
<?php
$icons = new \Feather\IconManager();
?>

<!-- Display the 'anchor' icon -->
<?php echo $icons->getIcon('anchor'); ?>

<!-- Get creative! -->
<button class="icon-button">
    Learn More <?= $icons->getIcon('arrow-right'); ?>
</button>
```

`Feather\IconManager::getIcon()` returns an `Icon` object. To render the icon html itself, either cast the `Icon` as a string or call its `render()` function.

```php
$icons->getIcon('anchor'); // Returns an Icon object
$html = $icons->getIcon('anchor')->render(); // Returns the icon's html
echo $icons->getIcon('anchor'); // Outputs the icon's html, since it is cast as a string
```
### Attributes

Attributes can be modified on both the `IconManager` and on `Icon` objects. Attributes can be modified directly using the `setAttribute(s)` functions or by using the helper functions.

Attribute changes on the `IconManager` will affect all `Icon` objects created by the `IconManager`. Changes on `Icon` objects will only affect the individual icons.

```php
// Use on the IconManager instance to set default attributes for all icons
$icons->setAttributes(['stroke' => '#fff', 'stroke-width' => 2]);
$icons->setAttribute('stroke', '#fff');

$icons->setSize(24);
$icons->setColor('#fff');
$icons->setWeight(2);
$icons->addCssClass('foo');

// Or use on a single icon to only affect that one
echo $icons->getIcon('alert-triangle')->setColor('red')->setAttribute('data-alert', 'true');
```

### Accessibility

When getting an `Icon`, alt text can be passed as an argument or can be set on the `Icon` at a later time.

```php
$icons->getIcon('anchor', [], 'Icon of an anchor');

$icon->setAltText('Icon of an anchor');
```

### Aliases

Aliases can be set to make larger changes across a theme easier, such as replacing the actual icon used for a specific use case. For example, what if for the close button icon, you wanted to switch
from using the `x` icon to `x-circle`. Instead of having the icon name hardcoded, you could use an alias for the use case and update the value in one place. Aliases are set on the `IconManager`.

```php
$icons->addAlias('close-button', 'x');
```

## Contributing

Feel free to open up issues and PRs for suggestions.

## License

Licensed under the [MIT License](https://github.com/Pixelrobin/php-feather/blob/master/LICENSE).

The icons in this code are from [Feather](https://github.com/feathericons/feather). It is also licensed under the [MIT License](https://github.com/feathericons/feather/blob/master/LICENSE).
