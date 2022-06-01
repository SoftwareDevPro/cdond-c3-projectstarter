<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo_text.svg" width="320" alt="Nest Logo" /></a>
</p>

[travis-image]: https://api.travis-ci.org/nestjs/nest.svg?branch=master
[travis-url]: https://travis-ci.org/nestjs/nest
[linux-image]: https://img.shields.io/travis/nestjs/nest/master.svg?label=linux
[linux-url]: https://travis-ci.org/nestjs/nest

  <p align="center">A progressive <a href="http://nodejs.org" target="blank">Node.js</a> framework for building efficient and scalable server-side applications, heavily inspired by <a href="https://angular.io" target="blank">Angular</a>.</p>
    <p align="center">
<a href="https://www.npmjs.com/~nestjscore"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~nestjscore"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
<a href="https://www.npmjs.com/~nestjscore"><img src="https://img.shields.io/npm/dm/@nestjs/core.svg" alt="NPM Downloads" /></a>
<a href="https://travis-ci.org/nestjs/nest"><img src="https://api.travis-ci.org/nestjs/nest.svg?branch=master" alt="Travis" /></a>
<a href="https://travis-ci.org/nestjs/nest"><img src="https://img.shields.io/travis/nestjs/nest/master.svg?label=linux" alt="Linux" /></a>
<a href="https://coveralls.io/github/nestjs/nest?branch=master"><img src="https://coveralls.io/repos/github/nestjs/nest/badge.svg?branch=master#5" alt="Coverage" /></a>
<a href="https://gitter.im/nestjs/nestjs?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=body_badge"><img src="https://badges.gitter.im/nestjs/nestjs.svg" alt="Gitter" /></a>
<a href="https://opencollective.com/nest#backer"><img src="https://opencollective.com/nest/backers/badge.svg" alt="Backers on Open Collective" /></a>
<a href="https://opencollective.com/nest#sponsor"><img src="https://opencollective.com/nest/sponsors/badge.svg" alt="Sponsors on Open Collective" /></a>
  <a href="https://paypal.me/kamilmysliwiec"><img src="https://img.shields.io/badge/Donate-PayPal-dc3d53.svg"/></a>
  <a href="https://twitter.com/nestframework"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow"></a>
</p>
  <!--[![Backers on Open Collective](https://opencollective.com/nest/backers/badge.svg)](https://opencollective.com/nest#backer)
  [![Sponsors on Open Collective](https://opencollective.com/nest/sponsors/badge.svg)](https://opencollective.com/nest#sponsor)-->

## Description

[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository.

## Installation

1st, login with NPM using `npm login`. That way you can access the private packages.

2nd...

```bash
$ npm install
```

## Running the app

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# incremental rebuild (webpack)
$ npm run webpack
$ npm run start:hmr

# production mode
$ npm run start:prod
```

## Test

```bash
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov
```

## Support

Nest is an MIT-licensed open source project. It can grow thanks to the sponsors and support by the amazing backers. If you'd like to join them, please [read more here](https://docs.nestjs.com/support).

## Stay in touch

- Author - [Kamil Myśliwiec](https://kamilmysliwiec.com)
- Website - [https://nestjs.com](https://nestjs.com/)
- Twitter - [@nestframework](https://twitter.com/nestframework)

## License

Nest is [MIT licensed](LICENSE).

## Status/Healthcheck Endpoint

This API comes with a simple endpoint that provides it's status. If the API is not working, neither will the endpoint. This can be useful for load balancers and other applications that periodically check on the availability of a service.

`GET /status` => `{ status: "ok" }`

## Logging with Loggly

We are using Loggly with Winston to track log messages remotely. If you want to send your logs to Loggly, you should configure the following variables in your environment (either with `.env` or in your operating system):

```
LOGGLY_SUBDOMAIN=yoursubdomain
LOGGLY_TOKEN=yourlogglytoken
LOGGLY_LEVEL=info
```

You can obtain a free account from Loggly to test.

## Logging with Slack

You can also log things like errors to Slack to get faster notifications. If you want to send your logs to Slack, you should configure the following variables in your environment (either with `.env` or in your operating system):

```
SLACK_LOGGER_WEBHOOK=some webhook from slack
SLACK_LOGGER_CHANNEL=channelName
```

To further customize the log messages, you can also include these optional env vars:

```
SLACK_LOGGER_USERNAME=Sync Errors
SLACK_LOGGER_ICON_URL=http://someImage.com
SLACK_LOGGER_LOG_LEVEL=error
```

## Migrations

NOTE: Be sure you have your environment variables set up. See `DB Setup` section.

NestJS uses TypeORM to create, generate, run migrations.
To apply pending migrations you just need to run:

```bash
npm run migrations
```

If you have modified/created any entity you can generate a migration from it:

```bash
npm run migrations:generate -- --n <MigrationName>
```

To revert the last applied migration:

```bash
npm run migrations:revert
```

## DB Setup

You need to add some environment variables to your system in order to run migrations or the backend. For convenience, you can also create a `.env` file to represent your environment. Here's the format:

```
TYPEORM_CONNECTION=postgres
TYPEORM_HOST=localhost
TYPEORM_PORT=5432
TYPEORM_USERNAME=postgres
TYPEORM_PASSWORD=password
TYPEORM_DATABASE=glee2
TYPEORM_MIGRATIONS=./src/migrations/*.ts
TYPEORM_ENTITIES=./src/modules/**/*.entity.ts
```

## Migrations for CI/CD Review Apps

It would be best to spin up a database in RDS while we are spinning up a new environment in EB. BUT, it takes around 10 minutes to spin up a new DB in RDS. It's also more work to script the new db that we don't have time for. So, as a stop-gap, you can manually migrate a shared database ("dev") from the CI/CD screen in Gitlab. This will trigger a build step that runs "revert" and "run" to down and up the migrations. You must make sure that you have all the necessary db-related env vars in Gitlab so that this will work (see "DB Setup" section).

## Authentication with Auth0

Authentication has been applied to all endpoints, so it's not necessary to specify which endpoints require auth. For authentication to work, you will need some env vars, for example:

```
AUTH0_CLIENT_SECRET= <id placeholder, check trello card on OIW board in resources lane>
AUTH0_CLIENT_ID= <id placeholder, check trello card on OIW board in resources lane>
AUTH0_DOMAIN=glee2-dev.auth0.com
AUTH0_AUDIENCE=http://localhost:3030
```

(These vars work for our `Acklen` tenant in Auth0 using the API called "testing".)

To test the API with Postman, you will need a valid JWT encrypted with RS256 and the correct client secret (amongst other things). You can generate said JWT by hitting Auth0's OAuth endpoint like this:

```
curl --request POST \
  --url https://acklen.auth0.com/oauth/token \
  --header 'content-type: application/json' \
  --data '{"client_id":"qrzt4jjhdmJHSdg5Ca6gVsdtY6x1xc2G","client_secret":"Xm6vhFnMv2BonJ8lhxsbCAZtIe5KjqqyXKNut5I5Spt4AQ3ms7mYTmwQ7JzIIwdt","audience":"http://localhost:3030","grant_type":"client_credentials"}'
```

(This only works with an "API" in Auth0. It will not work with an "Application" in Auth0 because they disable `client_credentials` grants by default and we have not found a way to enable that.)

To switch your backend to use the "Application" in Auth0, you should simply change the clientId, clientSecret, and audience in your environment variables.

## Rubric Submissions

https://github.com/SoftwareDevPro/cdond-c3-projectstarter

Public URL for your S3 Bucket (aka, your green candidate front-end) [URL02]
http://udapeople-4da46eb.s3-website-us-east-1.amazonaws.com

https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/presentation.pdf

Build Jobs that failed because of compile errors. [SCREENSHOT01]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT01.png

Failed unit tests. [SCREENSHOT02]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT02.png

Failure because of vulnerable packages. [SCREENSHOT03]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT03.png

An alert from one of your failed builds. [SCREENSHOT04]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT04.png

Console output of appropriate failure for infrastructure creation job (using CloudFormation). [SCREENSHOT05]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT05.png

Console output of a smoke test job that is failing appropriately. [SCREENSHOT06]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT06.png

Console output of a successful rollback after a failed smoke test. [SCREENSHOT07]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT07.png

Console output of successful promotion of new version to production in CloudFront. [SCREENSHOT08]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT08.png

Console output of successful cleanup job that removes old S3 bucket and EC2 instance. [SCREENSHOT09]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT09.png

Evidence that the deploy jobs only happen on the master branch. [SCREENSHOT10]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT10.png

Evidence of deployed and functioning front-end application in an S3 bucket [URL02].
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT11_A.png
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT11_B.png

Evidence of deployed and functioning front-end application in CloudFront. [URL03_SCREENSHOT]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT12_A.png
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT12_B.png

Evidence of healthy back-end application. [URL04_SCREENSHOT]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT13_A.png
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT13_B.png

Evidence of Prometheus Server. [URL05_SCREENSHOT].
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT14.png

Evidence that Prometheus is monitoring memory, cpu and disk usage of EC2 instances. [SCREENSHOT11]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT15.png

Evidence that Prometheus and AlertManager send alerts when certain conditions exist in the EC2 instance. [SCREENSHOT12]
https://github.com/SoftwareDevPro/cdond-c3-projectstarter/blob/master/instructions/myscreenshots/SCREENSHOT16.png
