# Flex-RTL

RTL version of [Flex](https://github.com/alexandrevicenzi/Flex) theme - a minimalist [Pelican](http://blog.getpelican.com/) theme - with some new small features.

## Features

* Change the direction of important tags to RTL.
* Add support for using multiple custom JS/CSS files.
* Add "featured-image" CSS class for styling featured images.

## How to enable Persian translations?

At first clone the [pelican-plugins](https://github.com/getpelican/pelican-plugins/) repository and enable i18n for your pelican site by adding the following code to your `pelicanconf.py`:

```python
# Enable i18n plugin, probably you already have some others here.
PLUGINS = ['i18n_subsites']
# Enable Jinja2 i18n extension used to parse translations.
JINJA_ENVIRONMENT = {'extensions': ['jinja2.ext.i18n',]}
```

The step above only enable i18n, but it won't translate anything from English.

If you want to translate to another language you need to change `DEFAULT_LANG` and `I18N_TEMPLATES_LANG` in your  `pelicanconf.py`. You should change `LOCALE` and `OG_LOCALE` to match your new configuration too.

To translate to Persian language you can add following code to your `pelicanconf.py`:

```python
# Default theme language.
I18N_TEMPLATES_LANG = 'fa_IR'
# Your time zone.
TIMEZONE = 'Asia/Tehran'
# Your language.
DEFAULT_LANG = 'fa'
LOCALE = 'fa'
```

## How to stop pelican from converting Persian tags and categories to Latin alphabet (Pinglish)?

when you add non ASCII or special characters in tags and categories, pelican converts them to ASCII characters or removes them.
for example if you use `سیب` for tag, pelican converts it to `sb` or `sib`.

to stop this, find `utils.py` in pelican's site-packages folder. find `slugify` function and find this lines and comment out them:

```python
value = unidecode(value)
# ...
value = value.encode('ascii', 'ignore')
# ...
return value.decode('ascii')
```

finally add this line to end of the function:

```python
return value
```
***Attention: these changes may cause unexpected problems.***

## Thanks

Alexandre Vicenzi for Flex Theme - https://github.com/alexandrevicenzi/Flex

Pelican dev team for Pelican static site generator - https://github.com/getpelican/pelican

## License

MIT
