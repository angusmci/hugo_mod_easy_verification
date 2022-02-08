# hugo_mod_easy_verification

[![standard-readme compliant](https://img.shields.io/badge/standard--readme-OK-green.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)

A small [module](https://gohugo.io/hugo-modules/) for [Hugo](https://gohugo.io/) to simplify adding Google and Bing verification/validation codes to web pages.

The module inserts the required `<meta>` tags into the `<head>` element of your home page.

## Table of Contents

- [Background](#background)
- [Install](#install)
- [Usage](#usage)
- [API](#api)
- [Maintainers](#maintainers)
- [Contributing](#contributing)
- [License](#license)

## Background

Tools such as [Google Search Console](https://search.google.com/search-console/) or [Microsoft Bing Webmaster Tools](https://www.bing.com/webmasters/) require that website owners prove their ownership of a website before the site can be managed by the tool. One method for doing this is to insert a special verification or validation token (unique to each site or owner) in the `<head>` of the site's homepage.

This module provides a simple way to add the verification codes to a site built using Hugo. It provides a single partial that can be invoked from whatever layouts generate `<head>` code for your site.

If you need different validation codes for production and development sites, look at the [Hugo documentation on configuration directories](https://gohugo.io/getting-started/configuration/#configuration-directory).

## Install

To use the module, add an import to your `config.toml` as follows:

```
[module]
  [[module.imports]]
    path = 'github.com/angusmci/hugo_mod_easy_verification'
```

If you need to update the module, do:

```
hugo mod get -u
```

## Usage

Specify the validation codes that you want to use by adding them to your `config.toml` file or configuration directory as part of the site parameters.

```
[params]
google_verification = "..."
ms_verification = "..."
```

(Replace the '...' by the codes that you get from Google or Microsoft).

To add the relevant links to the `<head>` of your HTML documents, use the `easy-verification` partial in whatever layouts generate the `<head>` of your document, e.g.

```
{{ partial "easy-verification" . }}
```

This will add the relevant meta tags to the document `<head>`. It inserts the required `<meta>` tags _only_ on the homepage of your site (so you don't need a special layout for your homepage only; just invoke the partial from whatever layout generates the `<head>` for your pages). It will only insert tags for the codes that you define in your site parameters. So if you only specify a code for Google, it will insert a `<meta>` tag to validate your site to Google, but not one for Microsoft Bing.

## Maintainers

[@angusmci](https://github.com/angusmci)

## Contributing

PRs accepted (but remember that the goal is to keep everything as simple as possible).

## License

MIT © 2022 Angus McIntyre






