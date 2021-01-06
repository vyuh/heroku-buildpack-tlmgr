Heroku buildpack: customizable TeX Live env with package manager
=====================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks)
for installing `texlive plain` on heroku.
It creates a portable TeX Live installation in `$BUILD_DIR/TeXLive` and
adds into it required packages (tl_pkg.txt).

To use the buildpack's binaries, you need to
add `$BUILD_DIR/buildpack/bin/$PLATFORM` at the end of `PATH`.


Note:
The creation of the buildpack can last 15 min at max.
Then it is forcibly stopped by heroku.
Do not add TOO much packages!

This buildpack is useless if used alone.
See https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app
to learn how to add this buildpack to an existing app.


If you want to add more packages than a plain TeXLive distribution has,
just add its name to `tl_pkg.txt`.
