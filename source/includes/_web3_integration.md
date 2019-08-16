
# **Quickstart (Web3)**

Already have a ÐApp using web3.js? Plug in Squarelink in minutes!

If you have not done so already, please [register your ÐApp](#getting-started) in the [Squarelink Developer Console](https://dev.squarelink.com).

> Install the Squarelink bundle from a CDN

```html
<script src="https://squarelink.com/js/squarelink.min.js"></script>
```

> ...Or install Squarelink from NPM

```shell
$ npm install squarelink
```

### Installation

First, install Squarelink's Web3 Provider from your preferred source. (See on the right)


> Basic Usage of Squarelink

```javascript
import Squarelink from 'squarelink'
import Web3 from 'web3'

const sqlk = new Squarelink('<YOUR CLIENT ID>')
window.web3 = new Web3(sqlk.getProvider())

// Use standard Web3 methods as you normally would
window.web3.eth.getAccounts().then(console.log)
```

### Usage

Initialize the Squarelink Object and set it as your Web3 Provider for your application. **Sweet, you're already finished!**

`const sqlk = new Squarelink(clientId [, network, opts])`

Parameter | Type | Description
--------- | ------- | -----------
`clientId` | **String** | This is the `clientId` associated with your ÐApp.
`network` | **String&#124;Object** | The name of a network supported by Squarelink, or your own custom network configuration (See below). Defaults to `mainnet`.
`opts` | **Object** | Additional options to pass to the Squarelink constructor (see below)



### Supported Networks:

- **Ethereum Mainnet** - `mainnet`
- **xDai Network** - `xdai`
- **Ropsten Network** - `ropsten`
- **Kovan Network** - `kovan`
- **Rinkeby Network** - `rinkeby`
- **Goerli Network** - `goerli`
- **Private/Custom Networks** - see below

> Custom network example

```javascript
...
const sqlk = new Squarelink('<YOUR CLIENT ID>', {
  url: 'https://localhost:8545',
  chainId: 420
})
...
```

### Custom Network Configuration:

Parameter | Type | Description
--------- | ------- | -----------
`url` | **String** | The JSON_RPC endpoint Squarelink will connect to.
`chainId` | **Number** | *(optional)* Chain ID for your network

> Custom Methods Example

```javascript
...
const sqlk = new Squarelink('<YOUR CLIENT ID>', 'mainnet', {
  scope: ['user:name','user:email']
})
sqlk.getName()
> Satoshi Nakamoto

sqlk.getEmail()
> satoshi@buttcoin.io
...
```

### Options (`opts`)

Parameter | Type | Description
--------- | ------- | -----------
`scope` | `Array` | Request additional scopes to use custom Squarelink functions.

#### Available Scopes:
- `user` - Equivalent to all scopes below
- `user:name` - Access to read user's name
- `user:email` - Access to user's email address
- `user:security` - Access to read user's security settings

### Custom Squarelink Methods

- *Squarelink*.**getName()** - requires the `user` or `user:name` scope

- *Squarelink*.**getEmail()** - requires the `user` or `user:email` scope

- *Squarelink*.**getSecuritySettings()** - requires the `user` or `user:security` scope