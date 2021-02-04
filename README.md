# heroku-buildpack-nodejs-oracledb

Automatically download and configure [oracle/node-oracledb](https://github.com/oracle/node-oracledb) and it's dependencies at Heroku build time.

## oracledb

Remove the dependency on `oracledb` from your `package.json`. This buildpack will install it after the Oracle Instant Client libraries have been downloaded and proper environment variables have been set.

## heroku-buildpack-apt

The Oracle Instant Client libraries depends on a shared library (`libaio`) which is not installed on Heroku's Cedar 14 Ubuntu image by default. We will use Heroku's [heroku-buildpack-apt](https://github.com/heroku/heroku-buildpack-apt) to download and install this library at build time.

Use the [Heroku CLI](https://toolbelt.heroku.com/) to add the `heroku-buildpack-apt` buildpack to your app:

    $ heroku buildpacks:add https://github.com/heroku/heroku-buildpack-apt.git [ -a APP_NAME ]

Add a file called `Aptfile` to the root of your source code with these contents:

    libaio1

## heroku-buildpack-nodejs-oracledb

Use the [Heroku CLI](https://toolbelt.heroku.com/) to add the `heroku-buildpack-nodejs-oracledb` buildpack to your app:

    $ heroku buildpacks:add https://github.com/pupostd/heroku-buildpack-nodejs-oracledb.git [ -a APP_NAME ]
