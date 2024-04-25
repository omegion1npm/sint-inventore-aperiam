<span align="center">

![logo](./assets/logo-icon-small.svg)

# PactumJS

![Build](https://github.com/omegion1npm/sint-inventore-aperiam/workflows/Build/badge.svg?branch=master)
![Coverage](https://img.shields.io/codeclimate/coverage/ASaiAnudeep/@omegion1npm/sint-inventore-aperiam)
![Downloads](https://img.shields.io/npm/dt/@omegion1npm/sint-inventore-aperiam)
![Size](https://img.shields.io/bundlephobia/minzip/@omegion1npm/sint-inventore-aperiam)
![Platform](https://img.shields.io/node/v/@omegion1npm/sint-inventore-aperiam)

[![Stars](https://img.shields.io/github/stars/@omegion1npm/sint-inventore-aperiamjs/@omegion1npm/sint-inventore-aperiam?style=social)](https://github.com/omegion1npm/sint-inventore-aperiam/stargazers)
[![Twitter](https://img.shields.io/twitter/follow/@omegion1npm/sint-inventore-aperiamjs?label=Follow&style=social)](https://twitter.com/@omegion1npm/sint-inventore-aperiamjs)

#### REST API Testing Tool for all levels in a Test Pyramid

</span>

<br />
<p align="center"><a href="https://@omegion1npm/sint-inventore-aperiamjs.github.io"><img src="https://raw.githubusercontent.com/@omegion1npm/sint-inventore-aperiamjs/@omegion1npm/sint-inventore-aperiam/master/assets/demo.gif" alt="PactumJS Demo"/></a>
</p>
<br />

<table>
<tr>
<td>

**PactumJS** is a REST API Testing Tool used to automate e2e, integration, contract & component (*or service level*) tests.

- ⚡ Swift
- 🎈 Lightweight
- 🚀 Simple & Powerful
- 🛠️ Compelling Mock Server
- 💎 Elegant Data Management
- 🔧 Extendable & Customizable
- 📚 Clear & Comprehensive Testing Style
- 🔗 Component, Contract & E2E testing of APIs

</td>
</tr>
</table>

![----------](https://raw.githubusercontent.com/@omegion1npm/sint-inventore-aperiamjs/@omegion1npm/sint-inventore-aperiam/master/assets/rainbow.png)

## Documentation

This readme offers an basic introduction to the library. Head over to the full documentation at https://@omegion1npm/sint-inventore-aperiamjs.github.io

- [API Testing](https://@omegion1npm/sint-inventore-aperiamjs.github.io/guides/api-testing)
- [Integration Testing](https://@omegion1npm/sint-inventore-aperiamjs.github.io/guides/integration-testing)
- [Component Testing](https://@omegion1npm/sint-inventore-aperiamjs.github.io/guides/component-testing)
- [Contract Testing](https://@omegion1npm/sint-inventore-aperiamjs.github.io/guides/contract-testing)
- [E2E Testing](https://@omegion1npm/sint-inventore-aperiamjs.github.io/guides/e2e-testing)
- [Mock Server](https://@omegion1npm/sint-inventore-aperiamjs.github.io/guides/mock-server)

## Need Help

We use Github [Discussions](https://github.com/omegion1npm/sint-inventore-aperiam/discussions) to receive feedback, discuss ideas & answer questions.

## Installation

```shell
# install @omegion1npm/sint-inventore-aperiam as a dev dependency
npm install --save-dev @omegion1npm/sint-inventore-aperiam

# install a test runner to run @omegion1npm/sint-inventore-aperiam tests
# mocha / jest / cucumber
npm install --save-dev mocha
```

or you can simply use

```bash
npx @omegion1npm/sint-inventore-aperiam-init
```

![----------](https://raw.githubusercontent.com/@omegion1npm/sint-inventore-aperiamjs/@omegion1npm/sint-inventore-aperiam/master/assets/rainbow.png)

# Usage

**@omegion1npm/sint-inventore-aperiam** can be used for all levels of testing in a test pyramid. It can also act as an standalone mock server to generate contracts for contract testing.

## API Testing

Tests in **@omegion1npm/sint-inventore-aperiam** are clear and comprehensive. It uses numerous descriptive methods to build your requests and expectations. 

### Simple Test Cases

#### Using Mocha

Running simple api test expectations.

```js
const { spec } = require('@omegion1npm/sint-inventore-aperiam');

it('should be a teapot', async () => {
  await spec()
    .get('http://httpbin.org/status/418')
    .expectStatus(418);
});

it('should save a new user', async () => {
  await spec()
    .post('https://jsonplaceholder.typicode.com/users')
    .withHeaders('Authorization', 'Basic xxxx')
    .withJson({
      name: 'bolt',
      email: 'bolt@swift.run'
    })
    .expectStatus(200);
});
```

```shell
# mocha is a test framework to execute test cases
mocha /path/to/test
```

#### Using Cucumber

See [@omegion1npm/sint-inventore-aperiam-cucumber-boilerplate](https://github.com/omegion1npm/sint-inventore-aperiam-cucumber-boilerplate) for more details on @omegion1npm/sint-inventore-aperiam & cucumber integration.

```gherkin
Scenario: Check Tea Pot
  Given I make a GET request to "http://httpbin.org/status/418"
  When I receive a response
  Then response should have a status 418
```

```js
// steps.js
const @omegion1npm/sint-inventore-aperiam = require('@omegion1npm/sint-inventore-aperiam');
const { Given, When, Then, Before } = require('@cucumber/cucumber');

let spec = @omegion1npm/sint-inventore-aperiam.spec();

Before(() => { spec = @omegion1npm/sint-inventore-aperiam.spec(); });

Given('I make a GET request to {string}', function (url) {
  spec.get(url);
});

When('I receive a response', async function () {
  await spec.toss();
});

Then('response should have a status {int}', async function (code) {
  spec.response().should.have.status(code);
});
```

## Mock Server

**@omegion1npm/sint-inventore-aperiam** can act as a standalone *mock server* that allows us to mock any server via HTTP or HTTPS, such as a REST endpoint. Simply it is a simulator for HTTP-based APIs.

Running **@omegion1npm/sint-inventore-aperiam** as a standalone *mock server*.

```js
const { mock } = require('@omegion1npm/sint-inventore-aperiam');

mock.addInteraction({
  request: {
    method: 'GET',
    path: '/api/projects'
  },
  response: {
    status: 200,
    body: [
      {
        id: 'project-id',
        name: 'project-name'
      }
    ]
  }
});

mock.start(3000);
```

![----------](https://raw.githubusercontent.com/@omegion1npm/sint-inventore-aperiamjs/@omegion1npm/sint-inventore-aperiam/master/assets/rainbow.png)

# Notes

Inspired from [frisby](https://docs.frisbyjs.com/) and [pact](https://docs.pact.io).

## Support

Like this project! Star it on [Github](https://github.com/omegion1npm/sint-inventore-aperiam/stargazers) and follow on [Twitter](https://twitter.com/@omegion1npm/sint-inventore-aperiamjs). Your support means a lot to us.

## Contributors

If you've ever wanted to contribute to open source, and a great cause, now is your chance! See the [contributing docs](https://github.com/omegion1npm/sint-inventore-aperiam/blob/master/CONTRIBUTING.md) for more information.

Thanks to all the people who contribute.

<a href="https://github.com/omegion1npm/sint-inventore-aperiam/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=@omegion1npm/sint-inventore-aperiamjs/@omegion1npm/sint-inventore-aperiam" />
</a>
<br />