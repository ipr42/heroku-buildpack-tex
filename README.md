Heroku buildpack: XeLaTeX
=====================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks)
for XeLaTeX documents compilation on heroku. It just bundles a statically-linked
working TeX Live environment - nothing more.

To use the environment, unpack the .tar.xz archive in some directory and add its
./buildpack/bin/x86_64-linux directory into the $PATH.

Then just run your command - e.g.:

    $ xelatex --shell-escape -synctex=1 -interaction=nonstopmode *.tex


How to add this buildpack as second one
---------------------------------------

It is advised to use this buildpack as a second one. It makes you not to forget about the fact it
just adds a commandline TeX utility, so it is useless solely.

    $ heroku buildpacks:add --index 2 https://github.com/milos-korenciak/heroku-buildpack-tex.git

Then just run usual push / deploy:

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom build pack... done
    -----> XeLaTeX app detected
    -----> Fetching XeLaTeX Live statically linked
    ...


How to add this buildpack as second one
---------------------------------------

It is advised to use this buildpack as a second one. It makes you not to forget about the fact it
just adds a commandline TeX utility, so it is useless solely.

    $ heroku buildpacks:add --index 2 https://github.com/milos-korenciak/heroku-buildpack-tex.git

Adding new fonts, .sty packages, etc.
-------------------------------------

If you added some .sty packages, reindex them:

    $ mktexlsr

The fonts are a bit problem - simply link them hard manner through their path.

Note: Make sure you copy also the file, not just the link! (Fonts in Linux are often just linked.)


Local playing with XeLaTeX
--------------------------

This repository is forked [mezis / heroku-buildpack-tex](https://github.com/milos-korenciak/heroku-buildpack-tex.git).
It can be better for some usages.


