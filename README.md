About
=====

I bootstrap my API's using this repo to create NodeJS based micro-services.

It is licensed under [MIT](https://en.wikipedia.org/wiki/MIT_License), so feel free to use it for any project and of course please feel free to raise issues and contribute through pull requests. 

[Demo](https://api-bootstrap.herokuapp.com/documentation) (hosted on heroku free plan - available 18h/day)


Features
========

 - Server: [NodeJS](https://nodejs.org)
 - Linting: [Standard](http://standardjs.com)
 - Task Management: [Gulp](http://gulpjs.com)
 - API:
   - Framework: [Hapi](http://hapijs.com)
   - Testing: [Lab](https://github.com/hapijs/lab), [Code](https://github.com/hapijs/code)
   - Validation: [Joi](https://github.com/hapijs/joi)
   - Documentation: [Swagger](http://swagger.io)


Installation
============

Clone this repository to your development machine:

`git clone https://github.com/iRomain/api-bootstrap.git`

Enter the newly created directory:

`cd api-bootstrap`

Install NPM dependencies:

`npm install`


Dev
===
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](http://standardjs.com/)

If you have not installed gulp globally, we suggest you do it with `npm install -g gulp` otherwise run the following commands from the node_modules directory: `./node_modules/gulp/bin/gulp.js`

Run `gulp`, it will automatically test, lint and start your API, watching any modification and re-linting/starting with nodemon.

Gulp sets the environment variable `NODE_ENV=dev`

> Use [TDD](https://en.wikipedia.org/wiki/Test-driven_development):

> 1. Write a test in `./test/`
> 2. Add your endpoint in `./lib/api.js`
> 3. Run `gulp`

You can see your API on [http://localhost:3000](http://localhost:3000) and see its documentation on [http://localhost:3000/documentation](http://localhost:3000/documentation)


Test
====

Travis CI [![Build Status](https://api.travis-ci.org/iRomain/api-bootstrap.svg)](https://travis-ci.org/iRomain/api-bootstrap)
---------

This API is compatible with [Travis](https://travis-ci.org).

It sets the environment variable `NODE_ENV=test`

> Add this repo (which you most likely forked already):

> 1. [Sync Travis with your Github account](https://travis-ci.org/profile) and add this repo
> 2. Push your repo (if you didn't change/remove the [`deploy`](.travis.yml#L7) part, it will fail at deployment)

Code Climate [![Code Climate](https://codeclimate.com/github/iRomain/api-bootstrap/badges/gpa.svg)](https://codeclimate.com/github/iRomain/api-bootstrap) [![Test Coverage](https://codeclimate.com/github/iRomain/api-bootstrap/badges/coverage.svg)](https://codeclimate.com/github/iRomain/api-bootstrap/coverage)
------------

This API is compatible with [Code Climate](https://codeclimate.com) through the [Travis/Code Climate integration](http://docs.travis-ci.com/user/code-climate/)

> 1. Add this repo to Code Climate and get the repo token
> 2. Edit the `addons.code_climate.repo_token` in [.travis.yml](.travis.yml)
> Tip: Use [Travis to encrypt](http://docs.travis-ci.com/user/encryption-keys/) your token with `travis encrypt <token> --add addons.code_climate.repo_token`

This API is also compatible with Codacy [![Codacy Badge](https://api.codacy.com/project/badge/5e7e5bcce27744baad9248c94e3e98c9)](https://www.codacy.com/app/iRomain/api-bootstrap)


Prod
====

Heroku hosting [![Deployment Status](http://heroku-badge.herokuapp.com/?app=api-bootstrap&style=flat&root=documentation)](https://api-bootstrap.herokuapp.com/documentation)
--------------

This API is compatible with [Heroku](http://keroku.com) through the [Travis/Heroku integration](http://docs.travis-ci.com/user/deployment/heroku/).

> Create your app on Heroku:

> 1. [Create a new app](https://dashboard.heroku.com/new)
> 2. In your newly created app settings, create a new config var with key `NODE_ENV` and value `prod`


> Change the Deploy configuration in [.travis.yml](.travis.yml):

> 1. Change your `deploy.app` name
> 2. Change your `deploy.api_key`
> Tip: Use [Travis to encrypt](http://docs.travis-ci.com/user/encryption-keys/) your api key with `travis encrypt <api key> --add deploy.api_key`

> Push to GitHub:

> 1. Watch the build in Travis
> 2. Watch the deployment in Heroku
> 3. Your API is now available on `https://<app name>.herokuapp.com/documentation`

Docker image
--------------
A [Docker image](https://hub.docker.com/r/iromain/api-bootstrap/) is automatically built by using the [Travis/Docker integration](http://docs.travis-ci.com/user/docker/). It could be setup with docker hub [automated build](https://hub.docker.com/add/automated-build) functionality but I prefer how everything can be configured in .travis.yml close to the code.

> Change the Docker image build configuration in [.travis.yml](.travis.yml):

> 1. Change your image repo in `before_install` for both the build and push commands
> 2. Change your [encrypted](http://docs.travis-ci.com/user/encryption-keys/) docker email, username, password in `env`

Cloud Foundry hosting
--------------
Cloud Foundry hosting for [this API](http://api-bootstrap.apps.eu01.cf.canopy-cloud.com/documentation) is provided by [Canopy](http://www.canopy-cloud.com)
This API is compatible with [CloudFoundry](https://www.cloudfoundry.org) through the [Travis/Cloud Foundry integration](http://docs.travis-ci.com/user/deployment/cloudfoundry/).

> Change the Deploy configuration in [.travis.yml](.travis.yml):

> 1. Change your `deploy.organization` name
> 2. Change your `deploy.space` name
> 3. Change your `deploy.api`
> 4. Change your `deploy.username`
> 5. Change your `deploy.password`
> Note: For privacy reasons, I decided to encrypt the api endpoint, my username and my password. Use [Travis to encrypt](http://docs.travis-ci.com/user/encryption-keys/) at least your password with `travis encrypt <password> --add deploy.password`

> Push to GitHub:

> 1. Watch the build in Travis
> 2. Watch the deployment in Cloud Foundry
> 3. Your API is now available on `https://<app name>.<cloudfoundry domain>/documentation`


**Note for Cloud Foundry Docker deployment**

Diego supports docker containers, however as of today it has issues to interpret the command CMD in Dockerfiles. A workaround is to specify manually the start command when pushing.

> Example: 
> `cf push api-bootstrap -o iromain/api-bootstrap -c "node api.js"`


New Relic monitoring
--------------------

This API is compatible with [New Relic](http://newrelic.com) through the [Heroku/New Relic integration](https://docs.newrelic.com/docs/agents/nodejs-agent/hosting-services/nodejs-agent-heroku)

> 1. [Add the New Relic element](https://elements.heroku.com/addons/newrelic) to your app
> 2. Edit the `app_name` in [newrelic.js](newrelic.js) with your heroku app name (recommended but could be any name)
> 3. Edit the `logging.level` in [newrelic.js](newrelic.js) to suit [your desired logging level](https://github.com/trentm/node-bunyan#levels)

----------

*Original credits to: [iRomain/api-bootstrap](https://github.com/iRomain/api-bootstrap)*
