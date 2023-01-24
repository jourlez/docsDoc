---
sidebar_position: 2
---

# Token (Asset)

A token is a digital asset on the blockchain. A token can be used:

As a cryptocurrency to pay for goods and services within a project, as well as for crowdfunding;

* As an object or resource in games etc.
* A token can represent a physical or an intangible object. The words “token” and “asset” are used interchangeably in the DecentralChain ecosystem. DecentralCoin is the native token on the DecentralChain blockchain. More about **[DecentralCoin](token#decentralcoin)**.

All other tokens are custom tokens issued on behalf of some account. Any account that has enough DecentralCoins to pay the fee can issue its own token. The new token is immediately available:

* For transfers between accounts,
* For trading on **[Decentral.Exchange](http://decentral.exchange/)** (except for **[non-fungible tokens (NFTs)](token#non-fungible-token)**; **[smart assets](token#smart-asset)** trading is temporarily unavailable),
* For payments attached to dApp **[invoke script transactions](transaction#invoke-script-transaction)**.

## Token Issue

You can use **[Decentral.Exchange](http://decentral.exchange/)** online to create an asset.

* On the main screen make sure you are logged into your account, then click on Create Token.
* On the next screen specify the token parameters:
    * Name: The name of the created asset can not be shorter than 4 characters.
    * Description: A short description where you can include website links that can be particularly useful.
    * Quantity: Define the total supply of your asset. The total supply can either be fixed at the issuance or increased later by making the asset re-issuable.
    * Reissuable: Defines if the asset total supply can be increased later. If set to reissuable, the issuer can increase the supply at any time (If reissuable is selected when the asset is created, it can be changed to not reissuable at a later stage).
    * Decimals: Specify how many decimals your asset will have. For example, if you specify 8 decimals, as in Bitcoin, your asset can be divided down to 0.00000001.
    * Smart asset: A **[smart asset](token#smart-asset)** is an asset with an attached script that places conditions on every transaction made for the asset in question.
    * Script (for issuing a smart asset).
* Before creating a new asset, carefully read the creation conditions. If necessary, change the name of the asset according to the conditions, then select the I understand checkbox and click Generate.
* On the next screen double-check the entered data and if everything is correct click Send to finish the creation or click Go Back to make corrections.

The transaction fee is 1 DecentralCoin for a regular token or 0.001 DecentralCoins for a **[non-fungible tokens (NFTs)](token#non-fungible-token)**.
Moreover, the token can be issued by the **[dApp script](account#dapp-and-smart-account)** as a result of the **[invoke script transactions](transaction#invoke-script-transaction)** when the callable function result contains the **[issue action](../ride-language/structures#issue)**. The minimum fee for invoke script transaction is increased by 1 DecentralCoin for each non-NFT token issued.

## Token ID

Token ID is a byte array calculated as follows:

* If the token is issued by **[invoke issue transactions](transaction#issue-transaction)**, the token ID is the same as the transaction ID.
* If the token is issued by **[invoke script transactions](transaction#invoke-script-transaction)** when the callable function of **[dApp script](account#dapp-and-smart-account)** performed the **[issue action](../ride-language/structures#issue)**, the token ID is calculated as the BLAKE2b-256 hash of the byte array containing transaction ID and the fields of the Issue structure.

In the **[Node REST API](#)**, the token identifier is encoded in base58. For example:

"assetId": "8LQW8f7P5d5PZM7GtZEBgaqRPGSzS3DfPuiXrURJ4AJS"

The **[DecentralCoins](token#decentralcoin)** token has no identifier. The Node REST API uses null for DecentralCoin.

## Token Operations

* Transfer to another account: Can be done via a **[transfer](transaction#transfer-transaction)** or a **[mass transfer transaction](transaction#mass-transfer-transaction)**. A **[dApp script](account#dapp-and-smart-account)** can transfer the token via a **[scripttransfer script action](../ride-language/structures#scripttransfer)** script action as a result of an **[invoke script transactions](transaction#invoke-script-transaction)**.

* Exchange (trade deal): Three accounts can participate in the exchange: one user creates an **[order](order)** to buy a token, the other creates an order to sell a token. The matcher combines buy and sell orders with suitable parameters and creates an **[exchange transaction](transaction#exchange-transaction)**.

* Burning: Decreases the amount of token on the account and thereby the total amount of the token on the blockchain. Any token owner can burn it, not only the issuer. It is impossible to burn **[DecentralCoins](token#decentralcoin)**. Can be done via a **[burn transaction](transaction#burn-transaction)**. A dApp script can burn the token via a **[burn script action](../ride-language/structures#burn)** as a result of the Invoke script transaction.

* Payment to **[dApp](account#dapp-and-smart-account)**: An invoke script transaction can contain up to two payments to the dApp. Payment amount and token are available to the callable function.

### Operations Available Only to Issuer

The following token operations can only be performed by the account that issued the token:

* Sponsorship setup: The token issuer can enable sponsorship which allows all users to pay fees in this token (instead of DecentralCoins) for invoke script transactions and transfer transactions. **[More about sponsorship](transaction#sponsored-fees)**. Enabling or disabling sponsorship can be done via a **[sponsor fee transaction](transaction#sponsor-fee-transaction)**. A dApp script can set up sponsorship using a **[sponsorfee](../ride-language/structures#sponsorfee)** as a result of the invoke script transaction.

* Reissue: Increases the amount of token on the blockchain. The reissuable field of token determines whether the token can be reissued. Can be done via a **[reissue transaction](transaction#reissue-transaction)**.
A dApp script can reissue the token via a **[reissue script action](../ride-language/structures#reissue)** as a result of the invoke script transaction.

* Replacing the asset script: Can be done via a **[set asset script transactions](transaction#set-asset-script-transaction)**. If the token is not a smart asset, that is, the script was not attached when the token was issued, then it is impossible to attach the script later.

* Modifying the token name and / or description: Can be done via an **[update asset info transaction](transaction#update-asset-info-transaction)**.

## Token Types

### Non-Fungible Token

Non-fungible token or NFT is a special type of a token that is issued with the following parameters:

* “quantity”: 1
* “decimals”: 0
* “reissuable”: false

An NFT is a singular entity that has a unique ID. This contrasts with a regular token, two coins of which (for example, two WBTC) cannot be distinguished from each other. NFTs can be used as in-game items, collectibles, certificates, or unique coupons.

#### Issue of NFT

An NFT can be issued in the same ways as a regular token, see **[token issue](token#token-issue)**. The minimum fee for an NFT issue is 0.001 DecentralCoins, 1000 times less than for a regular token.

### Smart Asset

A smart asset is a token that has an **[asset script](../ride-language/script-types#asset-script)** assigned to it.
By default, tokens on the DecentralChain blockchain are not smart contracts, and any transactions with them are allowed. The script endows a token with functionality that sets the rules for its circulation. Each transaction involving a smart asset is automatically checked against the conditions specified in the script. If the asset's script allows the transaction, it will be executed; if the script denies the transaction, it is either not put onto the blockchain at all or saved as failed. More on the **[transaction validation](transaction#transaction-validation)** article.

Using smart assets, you can implement various financial instruments on the blockchain (options, interval trading, taxation), game mechanics (allowing transactions only between characters with certain properties). Please note:

* If a token is issued without a script, then the script cannot be added later.
* The script cannot be removed, so it is impossible to turn a smart asset into a regular one.
* The asset script can be changed using the **[set asset script transactions](transaction#set-asset-script-transaction)**, unless prohibited by the asset script itself (as well as by the **[dApp or account script](account#dapp-and-smart-account)** assigned to the issuer account).
* The **[minimum fee](transaction#minimum-fee)** for transaction is increased by 0.004 DecentralCoins for each smart asset involved, except for:

  * **[invoke script transactions](transaction#invoke-script-transaction)**,
  * Smart assets used as matcher fee in **[exchange transactions](transaction#exchange-transaction)**.

### Tokens of Other Blockchains

A token issued on another blockchain cannot be used directly on the DecentralChain blockchain. A new token representing the original one can be issued on the DecentralChain blockchain, and a gateway that pegs the two tokens 1 : 1 can be deployed.

## DecentralCoin

DecentralCoin is the native token of the DecentralChain blockchain. **[Block generators](node#generating-node)** receive **[transaction fees](transaction#transaction-fees)** and **[block rewards](node#block-reward)** in DecentralCoins, which encourages generators to maintain and develop the blockchain network infrastructure. The more DecentralCoins the generator holds (by ownership or lease), the greater its chance to add the next block is.

### DecentralCoin Parameters

DecentralCoins are present on the blockchain since inception, there is no issue transaction for it, therefore the DecentralCoin token does not have an ID. The REST API uses null for DecentralCoins.
The number of decimal places (decimals) for DecentralCoins is 8. The atomic unit called Decentralite is $\frac{1}{100,000,000}$ DecentralCoins.

### Leasing

The owner of DecentralCoins can lease them via a **[lease transaction](transaction#lease-transaction)**. DecentralCoins received on lease are included in the **[generating balance](account#account-balance)**. Block generators send back different percentages as rewards to lessors. A lessor can cancel the lease at any time via a **[lease cancel transaction](transaction#lease-cancel-transaction)**. **[More about leasing](node#leased-proof-of-stake)**.

### How to Get DecentralCoin

You can buy DecentralCoins tokens at **[Decentral.Exchange](http://decentral.exchange/)** or at one of the centralized exchanges. In addition, cryptocurrency gateways can be used to transfer external cryptocurrencies such as Bitcoin, Ethereum etc. from the external blockchain to the DecentralChain blockchain and vice versa. The gateway provides the user with the address on the external blockchain. After receiving a confirmation of transfer to this external address, the gateway transfers the corresponding asset (minus the fee) to the user’s DecentralChain address.

## Token Custom Parameters

Below is an example of JSON representation returned by the GET /assets/details/{assetId} method of Node REST API:

```
  {
    "assetId": "DG2xFkPdDwKUoBkzGAhQtLpSGzfXLiCYPEzeKH2Ad24p",
    "issueHeight": 1806810,
    "issueTimestamp": 1574429393962,
    "issuer": "3PC9BfRwJWWiw9AREE2B3eWzCks3CYtg4yo",
    "issuerPublicKey": "BRnVwSVctnV8pge5vRpsJdWnkjWEJspFb6QvrmZvu3Ht",
    "name": "USD-N",
    "description": "Neutrino USD",
    "decimals": 6,
    "reissuable": false,
    "quantity": 999999999471258900,
    "scripted": false,
    "minSponsoredAssetFee": 7420,
    "originTransactionId": "DG2xFkPdDwKUoBkzGAhQtLpSGzfXLiCYPEzeKH2Ad24p"
  }
```

### Atomic Unit

