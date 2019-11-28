# Hash.js
Hash.js is a Hedera Hashgraph javascript library. You can trigger send crypto, manage smart contracts, and interact with dApps using the Composer for Hedera Hashgraph chrome extension.

* [Upgrade Notes](#important-notes-for-existing-users)
* [Installation](#installation)
* [API](#api)
* [Browser](#browser)
* [Contributing](#contributing)
* [License](#license)

Hash.js is an Open Source Project, see the Contributing section to find out what this means.


## Important Notes for Existing Users
V1.0 is based on new Composer for Hedera Hasphgraph. It is injected automatically into window.hash. The extension is available at the [chrome store](https://chrome.google.com/webstore/detail/composer-for-hedera-hashg/hdjnnemgikeoehneddegfcmkljenlean). You can simply check for window.hash and display a notice for the user.



## Installation
### What do you need to get started?
You need a Hedera Account which can be gained by going to portal.hedera.com or by downloading the Composer for Hedera Chrome Extension as it includes a free create account tool for both TestNet and MainNet. You can also configure it with your own wallet. Just make sure it’s funded with HBAR or you'll receive "insufficient fee" when attempting to transact.

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Table of Contents

-   [extensionid][3]
    -   [Examples][4]
-   [enable][5]
    -   [Parameters][6]
    -   [Examples][7]
-   [triggerCryptoTransfer][8]
    -   [Parameters][9]
    -   [Examples][10]
-   [triggerSmartContract][11]
    -   [Parameters][12]
    -   [Examples][13]
-   [deploySmartContract][14]
    -   [Parameters][15]
    -   [Examples][16]
-   [triggerCheckBalance][17]
    -   [Parameters][18]
    -   [Examples][19]
-   [ethAddressToAccountId][20]
    -   [Parameters][21]
    -   [Examples][22]
-   [accountIdToEthAddress][23]
    -   [Parameters][24]
    -   [Examples][25]


## extensionid

Variable that gives id of extension when the composer extension is up and running

### Examples

```javascript
console.log(extensionid);
```

Returns **[string][26]** "igptwehnsjcokfkansilfhgntepvjbojm"

## enable

Triggers a prompt on website for composer extension connect guide

### Parameters

-   `cb` **[function][27]** 

### Examples

```javascript
hash.enable((err,res)=>{
  if(err){
      //error case
      console.log('Error:::',err);
  }else{
      //success case
      console.log('Success:::',res);
  }
});
// triggers a prompt window on your website
```

Returns **[function][27]** callback

## triggerCryptoTransfer

Triggers a Cryptotransfer prompt from composer extension

### Parameters

-   `data`  
-   `cb` **[function][27]** 

### Examples

```javascript
hash.triggerCryptoTransfer(data, (err,res)=>{
  if(err){
      //error case
      console.log('Error:::',err);
  }else{
      //success case
      console.log('Success:::',res);
  }
});
// tiggers cryptotransfer extension prompt
```

Returns **[function][27]** callback

## triggerSmartContract

Triggers a Smart Contract call prompt from composer extension

### Parameters

-   `data` **[object][28]** An object containing
    -   `data.contractid` **[string][26]** contract Id can be of account id type('0.0.1234') or domain name type ('mydomain.hh')
    -   `data.memo` **[string][26]** short message specifying the purpose or message relating to the call
    -   `data.paymentserver` **[string][26]** (optional) - a node server that is connected to hedera and forwards all calls to the network (optional, default `https://mps.hashingsystems.com`)
    -   `data.params` **[string][26]** (optional) - string of Array which contains parameters of contract function to be executed
    -   `data.abi-null` **[string][26]** string array of objects which contains details of contract function
    -   `data.extensionid` **[string][26]** (optional) - extension id of composer
    -   `data.gasfee` **[number][29]** cost of transaction fee(tinybars) needed for call
    -   `data.transactionfee` **[number][29]** cost of transaction fee(tinybars) needed for call
    -   `data.amount` **[number][29]** (optional)
-   `cb` **[function][27]** 

### Examples

```javascript
hash.triggerSmartContract(data, (err,res)=>{
  if(err){
      //error case
      console.log('Error:::',err);
  }else{
      //success case
      console.log('Success:::',res);
  }
});
// tiggers smart contract call extension prompt
```

Returns **[function][27]** callback

## deploySmartContract

Triggers a Smart Contract Deploy prompt from composer extension

### Parameters

-   `data` **[object][28]** An object containing
    -   `data.fileid` **[string][26]** (alternative to bytecode) - id of the file if created already
    -   `data.memo` **[string][26]** short message specifying the purpose or message relating to the call
    -   `data.params` **[string][26]** (optional) - string of Array which contains parameters of contract function to be executed
    -   `data.abi-null` **[string][26]** string array of objects which contains details of contract function
    -   `data.bytecode` **[string][26]** (alternative to fileid) - low-level code version of actual file
    -   `data.extensionid` **[string][26]** (optional) - extension id of composer
    -   `data.gasfee` **[number][29]** cost of transaction fee(tinybars) needed for call
    -   `data.transactionfee` **[number][29]** cost of transaction fee(tinybars) needed for call
    -   `data.expirationTime` **[number][29]** (optional) expiry time of contract in milliseconds (optional, default `7890000000`)
    -   `data.amount` **[number][29]** (optional)
-   `cb` **[function][27]** 

### Examples

```javascript
hash.deploySmartContract(data, (err,res)=>{
  if(err){
      //error case
      console.log('Error:::',err);
  }else{
      //success case
      console.log('Success:::',res);
  }
});
// tiggers smart contract deploy extension prompt
```

Returns **[function][27]** callback

## triggerCheckBalance

Checks balance of current account selected in composer extension or checks the balance of the given account id

### Parameters

-   `accountID` **[string][26]** account id in accountID format("0.0.12345")
-   `cb` **[function][27]** 

### Examples

```javascript
hash.triggerCheckBalance("0.0.12345", (err,res)=>{
  if(err){
      //error case
      console.log('Error:::',err);
  }else{
      //success case
      // {
      //   res:{
      //           balance:"2363161",
      //           currentAccount:"0.0.12345",
      //           currentNetwork:"mainnet"
      //       }
      // }
      console.log('Success:::',res);
  }
});
```

Returns **[function][27]** callback

## ethAddressToAccountId

Converts hexadecimal eth address to account id type('0.0.1234')

### Parameters

-   `ethAddress` **[string][26]** an hexadecimal value

### Examples

```javascript
hash.ethAddressToAccountId("0000000000000000000000000000000000003039);
//returns "0.0.12345"
```

## accountIdToEthAddress

Converts account id type('0.0.1234') to hexadecimal eth address

### Parameters

-   `accountId`  
-   `ethAddress` **[string][26]** an hexadecimal value

### Examples

```javascript
hash.accountIdToEthAddress("0.0.12345");
```

Returns **[string][26]** "0000000000000000000000000000000000003039"

[1]: #extensionid

[2]: #examples

[3]: #extensionid-1

[4]: #examples-1

[5]: #enable

[6]: #parameters

[7]: #examples-2

[8]: #triggercryptotransfer

[9]: #parameters-1

[10]: #examples-3

[11]: #triggersmartcontract

[12]: #parameters-2

[13]: #examples-4

[14]: #deploysmartcontract

[15]: #parameters-3

[16]: #examples-5

[17]: #triggercheckbalance

[18]: #parameters-4

[19]: #examples-6

[20]: #ethaddresstoaccountid

[21]: #parameters-5

[22]: #examples-7

[23]: #accountidtoethaddress

[24]: #parameters-6

[25]: #examples-8

[26]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String

[27]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function

[28]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object

[29]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number


## Browser
You can learn more at [api.hashingsystems.com](https://api.hashingsystems.com/)


## Contributing
You're welcome to contribute code on here. Fork and create a detailed pull request. 

For more info you can chat with us at https://hashingsystems.com

## License
See LICENSE for details. Hashing Systems © 2019

