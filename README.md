Heroku buildpack: customizable TeX Live env with package manager
=====================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks)
for (Xe)(La)TeX documents compilation on heroku. It creates anew statically-linked working TeX Live environment in $BUILD_DIR/buildpack/bin/x86_64-linux and adds into it required packages (tex_install.txt) + removes unwanted ones (tex_uninstall.txt in the app root).

To use the buildpack's binaries, you need to add $BUILD_DIR/buildpack/bin/x86_64-linux at the end of PATH.


To run TeX compilation, try e.g. (provided you added xelatex to be installed):

    $ xelatex --shell-escape -synctex=1 -interaction=nonstopmode $BUILD_DIR/buildpack/bin/x86_64-linux/test.tex
    

Note:
The creation of the buildpack can last 15 min at max. Then it is forcibly stopped by heroku. Do not add TOO much packages!


How to add this buildpack as second one
---------------------------------------

Just run from commandline

    $ heroku buildpacks:add --index 2 https://github.com/milos-korenciak/heroku-buildpack-tex.git

Then just run usual push / deploy:

    $ git push heroku master
    ...
    Heroku receiving push
    Fetching custom build pack... done
    XeLaTeX app detected
    Fetching XeLaTeX Live statically linked
    ...


Adding new fonts, .sty packages, etc.
-------------------------------------

If you want to add more packages, just add them into tex_install.txt file at the end of first line. (There should be one and ONLY one line!).

If it adds some unwanted packages, you can remove it immediately after its addition by adding it into tex_uninstall.txt file at the end of first line. (There should be one and ONLY one line!).


Local playing with XeLaTeX
--------------------------

This repository is upgrade of my original one: [milos-korenciak / heroku-buildpack-tex](https://github.com/milos-korenciak/heroku-buildpack-tex.git).

It is customizable in its content + packages.



