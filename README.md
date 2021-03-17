# Very short description of the package

[![Latest Version on GitHub](https://img.shields.io/github/v/blnsoftware/cakephp-subdomains.svg?style=flat-square)](https://github.com/blnsoftware/cakephp-subdomains)
[![Total Downloads](https://img.shields.io/github/dt/blnsoftware/cakephp-subdomains.svg?style=flat-square)](https://github.com/blnsoftware/cakephp-subdomains)

Easily add sub domains to your CakePHP application using route prefixes. Based on package [Multidimensional/Subdomains](https://github.com/multidimension-al/cakephp-subdomains) adding the possibility to rename folders for subdomains.

## Requirements

* CakePHP 3.3+
* PHP 5.5.9+

## Installation

You can install the package via composer:

```bash
composer require blnsoftware/cakephp-subdomains
```

## Setup


Load the plugin by running following command in terminal:

```
bin/cake plugin load RcnCapital/cakephp-subdomains -b -r
```

Or by manually adding following line to your app's `config/bootstrap.php`:

```php
Plugin::load('RcnCapital/cakephp-subdomains', ['bootstrap' => true, 'routes' => true]);
```

## Configuration

Run the installation script command in termainl:

```
bin/cake SubdomainsInstall
```

This command will allow you to automatically create a configuration file with the list of your subdomains for the plugin to use. You can also run this command to add or delete additional subdomains.

Alternatively, you can create a `config/cakephp-subdomains.php` file in your main CakePHP config folder:

```php
return [
    'RcnCapital/cakephp-subdomains' => [
		'Subdomains' => [
			'{SUBDOMAIN_1}', 
			'{SUBDOMAIN_2}', 
			/*...*/ 
			'{SUBDOMAIN_N}'
		]
	]
];
```

In case you have a subdomain for testing, you can easily translate that subdomain into the expected one, and access the same code base using 2 or more subdomains:

```php
return [
    'RcnCapital/cakephp-subdomains' => [
		'Subdomains' => [
			'subdomain1', 
			'subdomain2', 
			/*...*/ 
			'subdomain_n'
		],
		'SubdomainToPrefix' => [
			'dev-subdomain1' => 'subdomain1',
			'dev-subdomain2' => 'subdomain2'
		]
	]
];
```

This way, whenever you access your application thru https://dev-subdomain.mydomain.tld it will be the same as accessing thru https://subdomain.mydomain.tld. This is useful when you have more than one server and only one domain, with some subdomains pointing to a production server, and some other to a staging server. Your code will always use one set of controllers, no matter which application are you running, or if you are in a local development environment


## Usage

The plugin will automatically add the subdomains you specify as CakePHP prefixes. 

When generating links, include the subdomain prefix you want to use and the Router will automatically create the link using the subdomain URL.

```php
//Link to http://example.com/articles/
$this->Html->link(['prefix'=>false, 'controller'=>'Articles', 'action'=>'index']);

//Link to http://admin.example.com/articles/
$this->Html->link(['prefix'=>'admin', 'controller'=>'Articles', 'action'=>'index']);
```

### Testing

``` bash
composer test
```

### Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

If you discover any security related issues, please email daniel.marjos@bairesdev.com instead of using the issue tracker.

## Credits

- [Daniel Marjos](https://github.com/blnsoftware)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

