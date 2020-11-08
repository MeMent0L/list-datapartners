[![banner](https://raw.githubusercontent.com/oceanprotocol/art/master/github/repo-banner%402x.png)](https://oceanprotocol.com)

> Ocean Market Positive-Label Lists

---

- [🦑 Policies](#-policies)
- [🤿 List Schema](#-list-schema)
- [🏄‍♀️ List Usage](#️-list-usage)
- [⬆️ Releases](#️-releases)
- [🏛 License](#-license)

---

## 🦑 Policies

**[Here](policies/README.md)** are the policies & processes by which accounts get labels like `Pledged' and attach to online accounts.


## 🤿 List Schema

The file [list-accounts-pledged.json](list-accounts-pledged.json) has accounts with `Pledged` label. It follows this schema.

```json
{
  "address": "0x.....",
  "pledge": "Text of pledge",
}, ...
```

The file [list-accounts-data-launch-partner.json](list-accounts-data-launch-partner.json) has accounts with `Data Launch Partner` label. It follows this schema.

```json
{
    "accounts": ["0xf00ba4"],
    "name": "Foo Bar Inc.",
    "links": {
      "Home": "https://www.foobar.com/",
      "Twitter": "https://twitter.com/FooBar"
    }
}, ...
```

The file [list-accounts-publicly-traded.json](list-accounts-publicly-traded.json) has accounts with `Publicly Traded` label. It follows this schema.

```json
{
  "address": "0x.....",
  "name": "Individual or Organization Name",
}, ...
```

The file [list-accounts-email.json](list-accounts-email.json) has accounts with authenticated email address. It follows this schema.

```json
{
  "address": "0x.....",
  "email": "foo@bar.com",
}, ...
```

The file [list-accounts-twitter.json](list-accounts-twitter.json) has accounts with authenticated Twitter handle. It follows this schema.

```json
{
  "address": "0x.....",
  "twitter": "https://twitter.com/foobar",
}, ...
```

## 🏄‍♀️ List Usage

```bash
npm i @oceanprotocol/list-datapartners
```

These lists are published as a npm module and the [`market`](https://github.com/oceanprotocol/market) uses it as a dependency to enhance the UI for those data partners.

After every change, a new version of the list needs to be released.

You can also directly fetch the list from the `main` branch:

```text
https://raw.githubusercontent.com/oceanprotocol/list-datapartners/main/list-accounts-data-launch-partner.json
```

JavaScript usage:

```js
import listPartners from '@oceanprotocol/list-datapartners'

// old-school
const listPartners = require('@oceanprotocol/list-datapartners')
```

TypeScript usage:

```ts
import listPartners from '@oceanprotocol/list-accounts-data-launch-partner'
import { PartnerData } from '@oceanprotocol/list-accounts-data-launch-partner/types'
```

## ⬆️ Releases

Releases are managed semi-automatically. They are always manually triggered from a developer's machine with release scripts.

From a clean `main` branch you can run the release task bumping the version accordingly based on semantic versioning:

```bash
npm run release
```

The task does the following:

- bumps the project version in `package.json`, `package-lock.json`
- auto-generates and updates the CHANGELOG.md file from commit messages
- creates a Git tag
- commits and pushes everything
- creates a GitHub release with commit messages as description
- Git tag push will trigger Travis to do a npm release

For the GitHub releases steps a GitHub personal access token, exported as `GITHUB_TOKEN` is required. [Setup](https://github.com/release-it/release-it#github-releases)

## 🏛 License

```text
Copyright 2020 Ocean Protocol Foundation Ltd.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
