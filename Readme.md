Heroku buildpack: Python
========================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for Python apps, powered by [pip](http://www.pip-installer.org/).

[![Build Status](https://secure.travis-ci.org/norbert/heroku-buildpack-python.png?branch=numpy)](http://travis-ci.org/norbert/heroku-buildpack-python)


Usage
-----

Example usage:

    $ ls
    Procfile  requirements.txt  web.py

    $ heroku create --stack cedar --buildpack git://github.com/norbert/heroku-buildpack-python.git#numpy

    $ git push heroku master
    ...

You can also add it to upcoming builds of an existing application:

    $ heroku config:add BUILDPACK_URL=git://github.com/norbert/heroku-buildpack-python.git#numpy

The buildpack will detect your app as Python if it has the file `requirements.txt` in the root.

The NumPy step is triggered if your `requirements.txt` file contains `numpy`, which installs a built distribution of `numpy==1.7.1` and `scipy==0.12.0`.

It will use Pip to install your dependencies, vendoring a copy of the Python runtime into your slug.
