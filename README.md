# Customizable TeX Live Environment in Heroku

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks)
for installing Texlive [`scheme-minimal`](https://tug.org/texlive/doc/texlive-en/texlive-en.html#x1-250003.2.2) on heroku.

This buildpack is useless if used alone.
See https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app
to learn how to add this buildpack to an existing app.

    heroku buildpacks:add --index 1 https://github.com/vyuh/heroku-buildpack-tlmgr


This buildpack looks for the file `tl_pkg.txt` in the app's root directory
and creates a portable TeX Live installation in `$BUILD_DIR/TeXLive`.
The installation only has packages included in the plain scheme.
It then and adds packages listed in the file `tl_pkg.txt` of the app.

If you want packages not included in a plain TeXLive distribution then
just add its name to `tl_pkg.txt`.

Example `tl_plg.txt`:

    latex-bin
    xypic


Note:
The creation of the buildpack can last at most 15 minutes.
Then it is forcibly stopped by heroku.
Do not add too many packages.
