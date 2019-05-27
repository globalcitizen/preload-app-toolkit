# Gaia Preload webapp generation script [![Build Status](https://travis-ci.org/yurenju/gaia-preload-app.png)](https://travis-ci.org/yurenju/gaia-preload-app) [![Coverage Status](https://coveralls.io/repos/yurenju/gaia-preload-app/badge.png?branch=master)](https://coveralls.io/r/yurenju/gaia-preload-app?branch=master)

## Why need Gaia Preload App script

Pre-bundled webapps are not quite the same as usual webapps, since pre-bundled webapps may be seen before internet connectivity.

They have to store linked icons as built-in base-64 strings, provide the corresponding `metadata.json`, prefetched appcache, etc.

Gaia Preload App script is a `preload.py` script that helps to build a Pre-bundled webapp from a given `.webapp` URL.

## Usage

### fetch a single webapp

Find a webapp URL that you want to bundle, and run the command:

    $ python preload.py http://<webapp url>

It will generate a folder with target webapp name.

### batch process to fetch multiple webapp

You can form a `list` file that batched the process. The format is


    Facebook,http://fa....
    Twitter,https://twi....

Put `preload.py` script with `list` file in the same folder, then run the command:

    $ python preload.py

`preload.py` script will parse the `list` file and do the conversion for you.

You can specify a `--root` folder in which `preload.py` will look for the `list` file
and save the preloaded contents.

    $ python preload.py --root=~/webapps/

You can specify a `--removable` to configure removable attrbute in metadata.json.
By default removable is False.

    $ python preload.py --removable=[true|false]

## Install python six for urllib.request
```shell
$ pip install --upgrade pip
$ pip install six
```

### convert web icon to base64 string

fetch icon from URL and convert it to base64 string

    $ python preload.py --icon http://<icon url>

## Setup unit test
```shell
$ virtualenv .env
$ source .env/bin/activate
$ pip install mock
$ python preload_test.py
```

# Experimental: Minilla web UI

We'd developing the Minilla web UI that help people ease the customization work with web interface.

The Minilla only depends on python, so you can run

    $ python wsgi.py

open browser to http://localhost:8000 and use it.
