<div align="center">

![Sapphire Logo](https://cdn.skyra.pw/gh-assets/sapphire-banner.png)

# @sapphire/ratelimits

**Bucket implementation for Ratelimits.**

[![GitHub](https://img.shields.io/github/license/sapphiredev/utilities)](https://github.com/sapphiredev/utilities/blob/main/LICENSE.md)
[![codecov](https://codecov.io/gh/sapphiredev/utilities/branch/main/graph/badge.svg?token=OEGIV6RFDO)](https://codecov.io/gh/sapphiredev/utilities)
[![npm bundle size](https://img.shields.io/bundlephobia/min/@sapphire/ratelimits?logo=webpack&style=flat-square)](https://bundlephobia.com/result?p=@sapphire/ratelimits)
[![npm](https://img.shields.io/npm/v/@sapphire/ratelimits?color=crimson&logo=npm&style=flat-square)](https://www.npmjs.com/package/@sapphire/ratelimits)

</div>

**Table of Contents**

-   [Description](#description)
-   [Features](#features)
-   [Installation](#installation)
-   [Usage](#usage)
    -   [Token RateLimitManager](#token-ratelimitmanager)
    -   [Leaky RateLimitManager](#leaky-ratelimitmanager)
-   [API Documentation](#api-documentation)
-   [Buy us some doughnuts](#buy-us-some-doughnuts)
-   [Contributors ✨](#contributors-%E2%9C%A8)

## Description

There is often a need to apply ratelimits to protect a network from excessive traffic levels on connections routed through it, or limit bot command usages in your Discord bot, or similar things. This package offers two different techniques in the same implementation: the [Token Bucket](https://en.wikipedia.org/wiki/Token_bucket), and the [Leaky Bucket](https://en.wikipedia.org/wiki/Leaky_bucket).

## Features

-   Written in TypeScript
-   Bundled with Rollup so it can be used in NodeJS and browsers
-   Offers CommonJS, ESM and UMD bundles
-   Fully tested

## Installation

You can use the following command to install this package, or replace `npm install` with your package manager of choice.

```sh
npm install @sapphire/ratelimits
```

## Usage

**Note:** While this section uses `require`, the imports match 1:1 with ESM imports. For example `const { RateLimitManager } = require('@sapphire/ratelimits')` equals `import { RateLimitManager } from '@sapphire/ratelimits'`.

### Token RateLimitManager

```ts
// Import the Bucket class
const { RateLimitManager } = require('@sapphire/ratelimits');

// Define a bucket with 1 usage every 5 seconds
const rateLimitManager = new RateLimitManager(5000);

// Acquire the rate limit. The ID can be something like `'global'`, a Discord channel/server/user ID, or anything else.
const ratelimit = rateLimitManager.acquire('some-unique-id-here');

// Check if there is a rate limit right now
if (ratelimit.limited) {
	// Do something when limited, such as throwing an error
}

// We're not rate limited so we drip the bucket. After consuming once, the second run through we'll be rate limited.
ratelimit.consume();

// And now we can finish the flow by returning some form of "success" state.
```

### Leaky RateLimitManager

```ts
// Import the Bucket class
const { RateLimitManager } = require('@sapphire/ratelimits');

// Define a bucket with 2 usages every 5 seconds
const rateLimitManager = new RateLimitManager(5000, 2);

// Acquire the rate limit. The ID can be something like `'global'`, a Discord channel/server/user ID, or anything else.
const ratelimit = rateLimitManager.acquire('some-unique-id-here');

// Check if there is a rate limit right now
if (ratelimit.limited) {
	// Do something when limited, such as throwing an error
}

// We're not rate limited so we drip the bucket. After consuming twice, the third run through we'll be rate limited.
ratelimit.consume();

// And now we can finish the flow by returning some form of "success" state.
```

---

## API Documentation

For the full API documentation please refer to the TypeDoc generated [documentation](https://sapphiredev.github.io/utilities/modules/_sapphire_ratelimits.html).

## Buy us some doughnuts

Sapphire Community is and always will be open source, even if we don't get donations. That being said, we know there are amazing people who may still want to donate just to show their appreciation. Thank you very much in advance!

We accept donations through Open Collective, Ko-fi, PayPal, Patreon and GitHub Sponsorships. You can use the buttons below to donate through your method of choice.

|   Donate With   |                       Address                       |
| :-------------: | :-------------------------------------------------: |
| Open Collective | [Click Here](https://sapphirejs.dev/opencollective) |
|      Ko-fi      |      [Click Here](https://sapphirejs.dev/kofi)      |
|     Patreon     |    [Click Here](https://sapphirejs.dev/patreon)     |
|     PayPal      |     [Click Here](https://sapphirejs.dev/paypal)     |

## Contributors ✨

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://favware.tech/"><img src="https://avatars3.githubusercontent.com/u/4019718?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Jeroen Claassens</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=Favna" title="Code">💻</a> <a href="#infra-Favna" title="Infrastructure (Hosting, Build-Tools, etc)">🚇</a> <a href="#projectManagement-Favna" title="Project Management">📆</a> <a href="https://github.com/sapphiredev/utilities/commits?author=Favna" title="Documentation">📖</a> <a href="https://github.com/sapphiredev/utilities/commits?author=Favna" title="Tests">⚠️</a></td>
    <td align="center"><a href="https://github.com/kyranet"><img src="https://avatars0.githubusercontent.com/u/24852502?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Antonio Román</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=kyranet" title="Code">💻</a> <a href="#projectManagement-kyranet" title="Project Management">📆</a> <a href="https://github.com/sapphiredev/utilities/pulls?q=is%3Apr+reviewed-by%3Akyranet" title="Reviewed Pull Requests">👀</a> <a href="https://github.com/sapphiredev/utilities/commits?author=kyranet" title="Tests">⚠️</a></td>
    <td align="center"><a href="https://github.com/PyroTechniac"><img src="https://avatars2.githubusercontent.com/u/39341355?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Gryffon Bellish</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=PyroTechniac" title="Code">💻</a> <a href="https://github.com/sapphiredev/utilities/pulls?q=is%3Apr+reviewed-by%3APyroTechniac" title="Reviewed Pull Requests">👀</a> <a href="https://github.com/sapphiredev/utilities/commits?author=PyroTechniac" title="Tests">⚠️</a></td>
    <td align="center"><a href="https://github.com/vladfrangu"><img src="https://avatars3.githubusercontent.com/u/17960496?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Vlad Frangu</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=vladfrangu" title="Code">💻</a> <a href="https://github.com/sapphiredev/utilities/issues?q=author%3Avladfrangu" title="Bug reports">🐛</a> <a href="https://github.com/sapphiredev/utilities/pulls?q=is%3Apr+reviewed-by%3Avladfrangu" title="Reviewed Pull Requests">👀</a> <a href="#userTesting-vladfrangu" title="User Testing">📓</a> <a href="https://github.com/sapphiredev/utilities/commits?author=vladfrangu" title="Tests">⚠️</a></td>
    <td align="center"><a href="https://github.com/Stitch07"><img src="https://avatars0.githubusercontent.com/u/29275227?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Stitch07</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=Stitch07" title="Code">💻</a> <a href="#projectManagement-Stitch07" title="Project Management">📆</a> <a href="https://github.com/sapphiredev/utilities/commits?author=Stitch07" title="Tests">⚠️</a></td>
    <td align="center"><a href="https://github.com/apps/depfu"><img src="https://avatars3.githubusercontent.com/in/715?v=4?s=100" width="100px;" alt=""/><br /><sub><b>depfu[bot]</b></sub></a><br /><a href="#maintenance-depfu[bot]" title="Maintenance">🚧</a></td>
    <td align="center"><a href="https://github.com/apps/allcontributors"><img src="https://avatars0.githubusercontent.com/in/23186?v=4?s=100" width="100px;" alt=""/><br /><sub><b>allcontributors[bot]</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=allcontributors[bot]" title="Documentation">📖</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/Nytelife26"><img src="https://avatars1.githubusercontent.com/u/22531310?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Tyler J Russell</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=Nytelife26" title="Documentation">📖</a></td>
    <td align="center"><a href="https://github.com/Alcremie"><img src="https://avatars0.githubusercontent.com/u/54785334?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Ivan Lieder</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=Alcremie" title="Code">💻</a> <a href="https://github.com/sapphiredev/utilities/issues?q=author%3AAlcremie" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://github.com/RealShadowNova"><img src="https://avatars3.githubusercontent.com/u/46537907?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Hezekiah Hendry</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=RealShadowNova" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/Stitch07"><img src="https://avatars.githubusercontent.com/u/29275227?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Stitch07</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=Stitch07" title="Code">💻</a> <a href="https://github.com/sapphiredev/utilities/commits?author=Stitch07" title="Tests">⚠️</a></td>
    <td align="center"><a href="https://github.com/Vetlix"><img src="https://avatars.githubusercontent.com/u/31412314?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Vetlix</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=Vetlix" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/ethamitc"><img src="https://avatars.githubusercontent.com/u/27776796?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Ethan Mitchell</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=ethamitc" title="Documentation">📖</a></td>
    <td align="center"><a href="https://github.com/noftaly"><img src="https://avatars.githubusercontent.com/u/34779161?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Elliot</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=noftaly" title="Code">💻</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://jurien.dev"><img src="https://avatars.githubusercontent.com/u/5418114?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Jurien Hamaker</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=jurienhamaker" title="Code">💻</a></td>
    <td align="center"><a href="https://fanoulis.dev/"><img src="https://avatars.githubusercontent.com/u/38255093?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Charalampos Fanoulis</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=cfanoulis" title="Documentation">📖</a></td>
    <td align="center"><a href="https://github.com/apps/dependabot"><img src="https://avatars.githubusercontent.com/in/29110?v=4?s=100" width="100px;" alt=""/><br /><sub><b>dependabot[bot]</b></sub></a><br /><a href="#maintenance-dependabot[bot]" title="Maintenance">🚧</a></td>
    <td align="center"><a href="https://kaname.netlify.app/"><img src="https://avatars.githubusercontent.com/u/56084970?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Kaname</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/commits?author=kaname-png" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/nandhagk"><img src="https://avatars.githubusercontent.com/u/62976649?v=4?s=100" width="100px;" alt=""/><br /><sub><b>nandhagk</b></sub></a><br /><a href="https://github.com/sapphiredev/utilities/issues?q=author%3Anandhagk" title="Bug reports">🐛</a></td>
  </tr>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!
