<img src="https://www.royvoetman.nl/images/packages/gitlab.svg" width="100%">

A Gitlab Storage filesystem for [Flysystem](https://flysystem.thephpleague.com/docs/).

[![Latest Version](https://img.shields.io/packagist/v/royvoetman/flysystem-gitlab-storage.svg?style=flat-square)](https://packagist.org/packages/royvoetman/flysystem-gitlab-storage)
[![MIT Licensed](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE)
[![Total Downloads](https://img.shields.io/packagist/dt/royvoetman/flysystem-gitlab-storage.svg?style=flat-square)](https://packagist.org/packages/royvoetman/flysystem-gitlab-storage)

This package contains a Flysystem adapter for Gitlab. Under the hood, Gitlab's [Repository (files) API](https://docs.gitlab.com/ee/api/repository_files.html) v4 is used.

> For Flysystem 2 (PHP 7.4) [use version 2.0.4](https://github.com/RoyVoetman/flysystem-gitlab-storage/tree/v2.0.4)

> For Flysystem 1 (PHP 7.1) [use version 1.1.0](https://github.com/RoyVoetman/flysystem-gitlab-storage/tree/v1.1.0)

## Installation

```bash
composer require royvoetman/flysystem-gitlab-storage
```

## Integrations

* Laravel - [https://github.com/royvoetman/laravel-gitlab-storage](https://github.com/royvoetman/laravel-gitlab-storage)

## Usage
```php
// Create a Gitlab Client to talk with the API
$client = new Client('project-id', 'branch', 'base-url', 'personal-access-token');
   
// Create the Adapter that implements Flysystems AdapterInterface
$adapter = new GitlabAdapter(
    // Gitlab API Client
    $client,
    // Optional path prefix
    'path/prefix',
);

// The FilesystemOperator
$filesystem = new League\Flysystem\Filesystem($adapter);

// see http://flysystem.thephpleague.com/api/ for full list of available functionality
```

### Project ID
Every project in Gitlab has its own Project ID. It can be found at to top of the frontpage of your repository. [See](https://stackoverflow.com/questions/39559689/where-do-i-find-the-project-id-for-the-gitlab-api#answer-53126068)

### Base URL
This will be the URL where you host your gitlab server (e.g. https://gitlab.com)

### Access token (required for private projects)
Gitlab supports server side API authentication with Personal Access tokens

For more information on how to create your own Personal Access token: [Gitlab Docs](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Contributing

Contributions are **welcome** and will be fully **credited**. We accept contributions via Pull Requests on [Github](https://github.com/RoyVoetman/flysystem-gitlab-storage).

### Pull Requests

- **[PSR-2 Coding Standard](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md)** - The easiest way to apply the conventions is to install [PHP Code Sniffer](http://pear.php.net/package/PHP_CodeSniffer).
- **Document any change in behaviour** - Make sure the `README.md` and any other relevant documentation are kept up-to-date.
- **Create feature branches** - Don't ask us to pull from your master branch.
- **One pull request per feature** - If you want to do more than one thing, send multiple pull requests.

## License

The MIT License (MIT). Please see [License File](LICENSE) for more information.
