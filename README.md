# UAL for EOSIO Reference Authenticator

This authenticator is meant to be used with the [EOSIO Reference Authenticator Apps](#supported-environments) and the [Universal Authenticator Library](https://github.com/EOSIO/universal-authenticator-library).

![EOSIO Labs](https://img.shields.io/badge/EOSIO-Labs-5cb3ff.svg)

## About EOSIO Labs

EOSIO Labs repositories are experimental.  Developers in the community are encouraged to use EOSIO Labs repositories as the basis for code and concepts to incorporate into their applications. Community members are also welcome to contribute and further develop these repositories. Since these repositories are not supported by Block.one, we may not provide responses to issue reports, pull requests, updates to functionality, or other requests from the community, and we encourage the community to take responsibility for these.

## Getting Started

`yarn add ual-eosio-reference-authenticator`

#### Dependencies

* All apps must follow the [Manifest Specification](https://github.com/EOSIO/manifest-spec)

* You must use one of the UAL renderers below.

  * React - `ual-reactjs-renderer`

  * PlainJS - `ual-plainjs-renderer`


#### Basic Usage with React

```javascript
import { EOSIOAuth } from 'ual-eosio-reference-authenticator'
import { UALProvider, withUAL } from 'ual-reactjs-renderer'

const exampleNet = {
  chainId: '',
  rpcEndpoints: [{
    protocol: '',
    host: '',
    port: '',
  }]
}

const App = (props) => <div>{JSON.stringify(props.ual)}</div>
const AppWithUAL = withUAL(App)

const eosioAuth = new EOSIOAuth([exampleNet], { appName: 'Example App' })

<UALProvider chains={[exampleNet]} authenticators={[eosioAuth]}>
  <AppWithUAL />
</UALProvider>
```

## Supported Environments

The UAL EOSIO Reference Authenticator is currently supported on the following environments and their required [options](https://github.com/EOSIO/ual-eosio-reference-authenticator/blob/master/src/interfaces.ts#L18) are listed below:

* Chrome Desktop Browser - [EOSIO Reference Chrome Extension Authenticator App](https://github.com/EOSIO/eosio-reference-chrome-extension-authenticator-app)
  * Required option: `appName`
  * Optional option: `securityExclusions`
  ```javascript
  const securityExclusions = {
    addAssertToTransactions: false
  }
  const eosioAuth = new EOSIOAuth([exampleNet], { appName: 'Example App', securityExclusions })
  ```
* iOS - [EOSIO Reference iOS Authenticator App](https://github.com/EOSIO/eosio-reference-ios-authenticator-app)
  * Required options: `appName`, `protocol`
  * Optional option: `securityExclusions`
  ```javascript
  const securityExclusions = {
    addAssertToTransactions: false
  }
  const eosioAuth = new EOSIOAuth([exampleNet], { appName: 'Example App', protocol: 'eosio', securityExclusions })
  ```

## Contributing

[Contributing Guide](./CONTRIBUTING.md)

[Code of Conduct](./CONTRIBUTING.md#conduct)

## License

[MIT](./LICENSE)

## Important

See LICENSE for copyright and license terms.  Block.one makes its contribution on a voluntary basis as a member of the EOSIO community and is not responsible for ensuring the overall performance of the software or any related applications.  We make no representation, warranty, guarantee or undertaking in respect of the software or any related documentation, whether expressed or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement. In no event shall we be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or documentation or the use or other dealings in the software or documentation. Any test results or performance figures are indicative and will not reflect performance under all conditions.  Any reference to any third party or third-party product, service or other resource is not an endorsement or recommendation by Block.one.  We are not responsible, and disclaim any and all responsibility and liability, for your use of or reliance on any of these resources. Third-party resources may be updated, changed or terminated at any time, so the information here may be out of date or inaccurate.  Any person using or offering this software in connection with providing software, goods or services to third parties shall advise such third parties of these license terms, disclaimers and exclusions of liability.  Block.one, EOSIO, EOSIO Labs, EOS, the heptahedron and associated logos are trademarks of Block.one.

Wallets and related components are complex software that require the highest levels of security.  If incorrectly built or used, they may compromise users’ private keys and digital assets. Wallet applications and related components should undergo thorough security evaluations before being used.  Only experienced developers should work with this software.
