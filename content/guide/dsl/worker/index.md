---
id: worker-indexer
title: Worker
description: Understanding what a worker is.
---

## Introduction

A worker is the most basic unit of a Node that includes a set of logics to index, structure, and store Open Information.
Some logics are shared among different workers to reduce the code complexity.

## Workflow

A worker’s workflow is pretty simple:

The worker continuously monitors a specific Open Data Protocol (ODP). Access to the ODP is configured in the Node’s config.yaml.

The worker indexes Open Information from the ODP when there is an update.

The worker follows a rule-based interpretation to structure the indexed information.

The worker stores the structured data in the Node’s database.

## Available Workers

Here is a list of available workers.

<!-- network-worker table starts -->
| Network/Worker | arbitrum | arweave | avax | base | binance-smart-chain | crossbell | ethereum | farcaster | gnosis | linea | mastodon | near | optimism | polygon | rsshub | vsl | x-layer |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **core**[1] | ✓ |   | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |   | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| 1inch | ✓ |   | ✓ | ✓ | ✓ |   | ✓ |   | ✓ |   |   |   | ✓ | ✓ |   |   |   |
| aave | ✓ |   | ✓ | ✓ | ✓ |   | ✓ |   | ✓ |   |   |   | ✓ | ✓ |   |   |   |
| aavegotchi |   |   |   |   |   |   |   |   |   |   |   |   |   | ✓ |   |   |   |
| arbitrum | ✓ |   |   |   |   |   | ✓ |   |   |   |   |   |   |   |   |   |   |
| base |   |   |   | ✓ |   |   | ✓ |   |   |   |   |   |   |   |   |   |   |
| cow | ✓ |   |   | ✓ |   |   | ✓ |   | ✓ |   |   |   |   |   |   |   |   |
| crossbell |   |   |   |   |   | ✓ |   |   |   |   |   |   |   |   |   |   |   |
| curve | ✓ |   | ✓ | ✓ | ✓ |   | ✓ |   | ✓ |   |   |   | ✓ | ✓ |   |   | ✓ |
| ens |   |   |   |   |   |   | ✓ |   |   |   |   |   |   |   |   |   |   |
| highlight | ✓ |   |   |   |   |   | ✓ |   |   |   |   |   | ✓ | ✓ |   |   |   |
| iqwiki |   |   |   |   |   |   |   |   |   |   |   |   |   | ✓ |   |   |   |
| kiwistand |   |   |   |   |   |   |   |   |   |   |   |   | ✓ |   |   |   |   |
| lens |   |   |   |   |   |   |   |   |   |   |   |   |   | ✓ |   |   |   |
| lido |   |   |   |   |   |   | ✓ |   |   |   |   |   |   |   |   |   |   |
| linea |   |   |   |   |   |   | ✓ |   |   | ✓ |   |   |   |   |   |   |   |
| linear |   |   |   |   |   |   |   |   |   |   |   | ✓ |   |   |   |   |   |
| looksrare |   |   |   |   |   |   | ✓ |   |   |   |   |   |   |   |   |   |   |
| mastodon |   |   |   |   |   |   |   |   |   |   | ✓ |   |   |   |   |   |   |
| matters |   |   |   |   |   |   |   |   |   |   |   |   | ✓ |   |   |   |   |
| mirror |   | ✓ |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
| momoka |   | ✓ |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
| nearsocial |   |   |   |   |   |   |   |   |   |   |   | ✓ |   |   |   |   |   |
| nouns |   |   |   |   |   |   | ✓ |   |   |   |   |   |   |   |   |   |   |
| opensea |   |   |   |   |   |   | ✓ |   |   |   |   |   |   |   |   |   |   |
| optimism |   |   |   |   |   |   | ✓ |   |   |   |   |   | ✓ |   |   |   |   |
| paragraph |   | ✓ |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
| paraswap | ✓ |   | ✓ | ✓ | ✓ |   | ✓ |   |   |   |   |   | ✓ | ✓ |   |   |   |
| polymarket |   |   |   |   |   |   |   |   |   |   |   |   |   | ✓ |   |   |   |
| rainbow | ✓ |   | ✓ | ✓ | ✓ |   | ✓ |   |   | ✓ |   |   | ✓ | ✓ |   |   |   |
| rss3 |   |   |   |   |   |   | ✓ |   |   |   |   |   |   |   |   |   |   |
| stargate | ✓ |   | ✓ | ✓ | ✓ |   | ✓ |   |   | ✓ |   |   | ✓ | ✓ |   |   |   |
| uniswap | ✓ |   | ✓ | ✓ | ✓ |   | ✓ |   |   | ✓ |   |   | ✓ | ✓ |   |   |   |
| vsl |   |   |   |   |   |   | ✓ |   |   |   |   |   |   |   |   |   |   |
| zerion | ✓ |   | ✓ | ✓ | ✓ |   |   |   | ✓ | ✓ |   |   | ✓ | ✓ |   |   | ✓ |
| **Subtotal** | 12 | 3 | 9 | 11 | 9 | 2 | 21 | 1 | 6 | 6 | 1 | 3 | 13 | 14 | 1 | 1 | 3 |
<!-- network-worker table ends -->

[1] A core worker covers all the data on the open data protocol where it operates, except for the data already covered by other workers.

## Contribution

Workers are maintained by the community.

If you didn’t find the worker you need, you are welcome to fork our repository and submit pull requests for contributions.

We have a detailed guide on how to contribute a new worker, when you are ready, proceed to the next page.
