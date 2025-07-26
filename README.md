# web3.py

[![Join the conversation on Discord](https://img.shields.io/discord/809793915578089484?color=blue&label=chat&logo=discord&logoColor=white)](https://discord.gg/GHryRvPB84)
[![Build Status](https://circleci.com/gh/ethereum/web3.py.svg?style=shield)](https://circleci.com/gh/ethereum/web3.py)
[![PyPI version](https://badge.fury.io/py/web3.svg)](https://badge.fury.io/py/web3)
[![Python versions](https://img.shields.io/pypi/pyversions/web3.svg)](https://pypi.python.org/pypi/web3)
[![Docs build](https://readthedocs.org/projects/web3py/badge/?version=latest)](https://web3py.readthedocs.io/en/latest/?badge=latest)

# 🚀 Web3.py - Ethereum Python Library Guide  

A Python library for interacting with **Ethereum** and EVM-compatible blockchains.  

---

## 🔧 **Installation**  
```sh
  python -m pip install web3

  # You may need additional tools like geth or Infura for full functionality.
```
## 🌐 Connect to Ethereum
1. Mainnet (via Infura)
```python
  from web3 import Web3
  
  infura_url = "https://mainnet.infura.io/v3/YOUR_INFURA_PROJECT_ID"
  w3 = Web3(Web3.HTTPProvider(infura_url))
  print("Connected:", w3.is_connected())  # Check connection
```

---
## Documentation

[Get started in 5 minutes](https://web3py.readthedocs.io/en/latest/quickstart.html) or
[take a tour](https://web3py.readthedocs.io/en/latest/overview.html) of the library.

View the [change log](https://web3py.readthedocs.io/en/latest/release_notes.html).

For additional guides, examples, and APIs, see the [documentation](https://web3py.readthedocs.io/en/latest/).

## Want to Help?

Want to file a bug, contribute some code, or improve documentation? Excellent! Read up on our
guidelines for [contributing](https://web3py.readthedocs.io/en/latest/contributing.html),
then check out issues that are labeled
[Good First Issue](https://github.com/ethereum/web3.py/issues?q=is%3Aissue+is%3Aopen+label%3A%22Good+First+Issue%22).

______________________________________________________________________

## Questions on Implementation or Usage?

Join the conversation in the Ethereum Python Community [Discord](https://discord.gg/GHryRvPB84).
