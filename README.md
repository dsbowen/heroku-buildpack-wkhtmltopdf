# heroku-buildpack-wkhtmltopdf

This buildpack downloads and extracts the most recent
[wkhtmltopdf](https://wkhtmltopdf.org/) binaries and works on both `cedar-14`
and `heroku-16` stacks.


## Add the Buildpack

Just add the buildpack to your heroku app by executing:

```bash
heroku buildpacks:add https://github.com/turicas/heroku-buildpack-wkhtmltopdf.git
```

You can also force this buildpack to be the first Heroku process by using the
`--index` option:

```bash
heroku buildpacks:add --index=1 https://github.com/turicas/heroku-buildpack-wkhtmltopdf.git
```

## Usage

The binaries `wkhtmltopdf` and `wkhtmltoimage` will be available on `/app/bin`,
you can just execute `/app/bin/wkhtmltopdf ...` from your app.
