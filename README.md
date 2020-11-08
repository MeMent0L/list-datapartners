[![banner](https://raw.githubusercontent.com/oceanprotocol/art/master/github/repo-banner%402x.png)](https://oceanprotocol.com)

> Ocean Market Positive-Label Lists

---

- [🦑 Policies](#-policies)
- [🐬 List Files](#-list-files)
- [🤿 List Schema](#-list-schema)
- [🏄‍♀️ List Usage](#️-list-usage)
- [⬆️ Releases](#️-releases)
- [🏛 License](#-license)

---

## 🦑 Policies

**[Here](policies/README.md)** are the policies & processes by which accounts or assets may aquire positive labels such as `Pledged`.

## 🐬 List Files

There is one json file for each list:
- list-accounts-pledged.json - accounts with `Pledged` label
- list-accounts-data-launch-partner.json - accounts with `Data Launch Partner` label
- list-accounts-publicly-traded.json - accounts with `Publicly Traded' label

There are also lists that link the account with other online identities. 
- list-accounts-email.json - accounts with authenticated email address
- list-accounts-twitter.json - accounts with authenticated Twitter handle

## 🤿 List Schema

All account lists follow this schema. (FIXME this can be simplified)

```json
{
  "address": "0x.....",
  "name": "Individual or Organization Name",
},
{
   ...
}
```

For the list of authenticated email addresses:
```json
{
  "address": "0x.....",
  "email": "foo@bar.com",
}, ...
```

For the list of authenticated Twitter accounts:
```json
{
  "address": "0x.....",
  "email": "https://twitter.com/foobar",
}, ...
```

## 🏄‍♀️ List Usage

```bash
npm i @oceanprotocol/list-datapartners
```

This list is published as a npm module and the [`market`](https://github.com/oceanprotocol/market) uses it as a dependency to enhance the UI for those data partners.

After every change, a new version of the list needs to be released.

You can also directly fetch the list from the `main` branch:

```text
https://raw.githubusercontent.com/oceanprotocol/list-datapartners/main/list-datapartners.json
```

JavaScript usage:

```js
import listPartners from '@oceanprotocol/list-datapartners'

// old-school
const listPartners = require('@oceanprotocol/list-datapartners')
```

TypeScript usage:

```ts
import listPartners from '@oceanprotocol/list-datapartners'
import { PartnerData } from '@oceanprotocol/list-datapartners/types'
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
