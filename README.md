# Hedera Agent Kit - CoinCap Plugin Python version

A plugin for [Hedera Agent Kit PY](https://github.com/hashgraph/hedera-agent-kit-py) that provides integration with the CoinCap API

In this plugin we use CoinCap to get the current price in USD of one HBAR and combine it with the power of the Hedera Agent Kit to get your current balance of HBA in USD currency.

## Overview

This plugin enables `AI agents` to interact with the CoinCap API

## Installation in the example index.js agent

1.- Install the plugin

```bash
pip install coincap-hedera-agent-kit-plugin
```

2.- Add your CoinCap API Bearer token in the .env file ( You get it in the CoinCap website )

```
# Coincap API needed by coincap-hedera-plugin
COINCAP_BEARER_TOKEN=******************************
```

3.- Import the plugin code in your index.js (Hedera Agent)

```py
from coincap_hedera_plugin import conincap_h_plugin
```

4.- Add the plugin in the plugins secion of the agent

```py
const hederaAgentToolkit = new HederaLangchainToolkit({
client,
configuration: {
    tools: [],
    plugins: [coreQueriesPlugin, coreAccountPlugin, CoinCapHederalugin], // <---- Add these
```

5.- Use a prompt to ask for you current balance and tell the agent to want it in USD currency, for example like this:

```py
response = await agent.ainvoke(
    {"messages": [{"role": "user", "content": "Get my balance in HBAR and also convert it to USD please"}]},
```

6.- Now you can run the example agent and you should get your current HBAR balance converted to USD currency

```bash
python main.py
```

## Tools

```py
# Use the CoinCap API to get the current price in USD of one HBAR
def get_hbar_price_from_coincap():
```

## (Optional, only needed when creating your own python package) How to publish a PyPi package
1.- Read the [instructions](https://towardsdatascience.com/how-to-upload-your-python-package-to-pypi-de1b363a1b3/)

1.- Create the distribution package
```bash
python setup.py sdist
```

2.- Install twine
```bash
pip install twine
```

3.- Upload package
```bash
twine upload dist/*
```
