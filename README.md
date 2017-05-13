# heroku-buildpack-wkhtmltopdf

This buildpack downloads and extracts the most recent
[wkhtmltopdf](https://wkhtmltopdf.org/) binaries and works on both `cedar-14`
and `heroku-16` stacks.


## Add the Buildpack

Just add the buildpack to your heroku app by executing:

```bash
heroku buildpacks:add https://github.com/simplefractal/heroku-buildpack-wkhtmltopdf.git
```

You can also force this buildpack to be the first Heroku process by using the
`--index` option:

```bash
heroku buildpacks:add --index=1 https://github.com/simplefractal/heroku-buildpack-wkhtmltopdf.git
```

## Usage

The binaries `wkhtmltopdf` and `wkhtmltoimage` will be available on `/app/bin`,
you can just execute `/app/bin/wkhtmltopdf ...` from your app.


## Why another wkhtmltopdf buildpack

- None of the [available
  buildpacks](https://elements.heroku.com/search/buildpacks?q=wkhtmltopdf)
  (made by the community - there's no official wkhtmltopdf buildpack by Heroku)
  uses the newest wkhtmltopdf version (and there's a security warning on their
  website for oldest versions, so it's better to stick with the newest one);
- Almost all of the available buildpacks downloads wkhtmltopdf from
  [gna.org](http://gna.org/), but the service is not active anymore and will
  probably stop serving these files;
- Some of the buildpacks available set new environment vars instead of just
  leaving the binary in some location. It increases the boot time since new
  shell script files needed to be loaded (inside `.profile.d/`);
- Most of the available buildpacks works only on `cedar-14` stack -- and
  [`heroku-16` is the default dyno stack since May 08,
  2017](https://devcenter.heroku.com/changelog-items/1139).

This buildpack addresses the following issues:

- Uses wkhtmltopdf version 0.12.4
- Downloads wkhtmltopdf binaries from [wkhtmltopdf.org](http://wkhtmltopdf.org)
- Do not add new environment variables or shell scripts
- Tested on both `cedar-14` and `heroku-16` stack images

## Sample app

Want to see this buildpack running? See
[websitetopdf](https://github.com/turicas/websitetopdf).
