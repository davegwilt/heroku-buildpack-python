Heroku buildpack: Python
========================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for Python apps with support for :

1. [NumPy](http://www.numpy.org)
2. [SciPy](http://www.scipy.org)
3. [scikit-learn](http://scikit-learn.org)

Usage
-----

Example usage:

    $ ls
    Procfile  requirements.txt  web.py

    $ heroku create --stack cedar --buildpack git://github.com/essentia-analytics/heroku-buildpack-python.git#numpy

    $ git push heroku master
    ...

You can also add it to upcoming builds of an existing application:

    $ heroku config:add BUILDPACK_URL=git://github.com/essentia-analytics/heroku-buildpack-python.git#numpy

The NumPy step is triggered if your `requirements.txt` file contains `numpy`, which installs a built distribution of `numpy==1.7.1` and `scipy==0.12.0`.

It will use `pip` to install your dependencies, vendoring a copy of the Python runtime into your slug.
