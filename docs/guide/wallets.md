---
layout: default
title: Backend wallets
nav_order: 3
---


Backend wallets
===============

LNbits can run on top of many lightning-network funding sources. Currently there is support for CoreLightning, LND, LNbits, LNPay, lntxbot and OpenNode, with more being added regularly.

A backend wallet can be configured using the following LNbits environment variables:


### CoreLightning

Using this wallet requires the installation of the `pylightning` Python package.

- `LNBITS_BACKEND_WALLET_CLASS`: **CoreLightningWallet**
- `CORELIGHTNING_RPC`: /file/path/lightning-rpc

### Spark (c-lightning)

- `LNBITS_BACKEND_WALLET_CLASS`: **SparkWallet**
- `SPARK_URL`: http://10.147.17.230:9737/rpc
- `SPARK_TOKEN`: secret_access_key

### LND (REST)

- `LNBITS_BACKEND_WALLET_CLASS`: **LndRestWallet**
- `LND_REST_ENDPOINT`: http://10.147.17.230:8080/
- `LND_REST_CERT`: /file/path/tls.cert
- `LND_REST_MACAROON`: /file/path/admin.macaroon or Bech64/Hex

or

- `LND_REST_MACAROON_ENCRYPTED`: eNcRyPtEdMaCaRoOn

### LNbits

- `LNBITS_BACKEND_WALLET_CLASS`: **LNbitsWallet**
- `LNBITS_ENDPOINT`: e.g. https://lnbits.com
- `LNBITS_KEY`: lnbitsAdminKey

### LNPay

For the invoice listener to work you have a publicly accessible URL in your LNbits and must set up [LNPay webhooks](https://dashboard.lnpay.co/webhook/) pointing to `<your LNbits host>/wallet/webhook` with the "Wallet Receive" event and no secret. For example, `https://mylnbits/wallet/webhook` will be the Endpoint Url that gets notified about the payment. 

- `LNBITS_BACKEND_WALLET_CLASS`: **LNPayWallet**
- `LNPAY_API_ENDPOINT`: https://api.lnpay.co/v1/
- `LNPAY_API_KEY`: sak_apiKey
- `LNPAY_WALLET_KEY`: waka_apiKey


### lntxbot

- `LNBITS_BACKEND_WALLET_CLASS`: **LntxbotWallet**
- `LNTXBOT_API_ENDPOINT`: https://lntxbot.com/
- `LNTXBOT_KEY`: lntxbotAdminApiKey


### OpenNode

For the invoice to work you must have a publicly accessible URL in your LNbits. No manual webhook setting is necessary.

- `LNBITS_BACKEND_WALLET_CLASS`: **OpenNodeWallet**
- `OPENNODE_API_ENDPOINT`: https://api.opennode.com/
- `OPENNODE_KEY`: opennodeAdminApiKey
