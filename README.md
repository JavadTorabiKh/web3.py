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

---

## 🌐 Connect to Ethereum

1. Mainnet (via Infura)
```python
  from web3 import Web3
  
  infura_url = "https://mainnet.infura.io/v3/YOUR_INFURA_PROJECT_ID"
  w3 = Web3(Web3.HTTPProvider(infura_url))
  print("Connected:", w3.is_connected())  # Check connection
```
2. Testnet (Sepolia)
```python
  sepolia_url = "https://sepolia.infura.io/v3/YOUR_INFURA_PROJECT_ID"  # TESTNET
  w3 = Web3(Web3.HTTPProvider(sepolia_url))
```

3. Local Node (Ganache)
```python
  w3 = Web3(Web3.HTTPProvider("http://127.0.0.1:7545"))
```
---

## 💰 Wallet Interactions

Get Balance
```python
  balance = w3.eth.get_balance("0xAddress")
  print("Balance:", w3.from_wei(balance, 'ether'), "ETH")
```
Send Transaction
```python
  tx = {
      'nonce': w3.eth.get_transaction_count("0xSender"),
      'to': "0xReceiver",
      'value': w3.to_wei(0.01, 'ether'),
      'gas': 21000,
      'gasPrice': w3.eth.gas_price,
  }
  signed_tx = w3.eth.account.sign_transaction(tx, "YOUR_PRIVATE_KEY")
  tx_hash = w3.eth.send_raw_transaction(signed_tx.rawTransaction)
  print("TX Hash:", tx_hash.hex())
```
---

## 📜 Smart Contracts

1. Setup Contract
```python
  contract_address = "0xContractAddress"
  contract_abi = '[{"inputs":[], "name":"getValue", "outputs":[{"internalType":"uint256","name":"","type":"uint256"}], "type":"function"}]'
  contract = w3.eth.contract(address=contract_address, abi=contract_abi)
```
2. Call & Transact

Read (Call)
```python
  value = contract.functions.getValue().call()
  print("Value:", value)
```
Write (Transact)
```python
  tx = contract.functions.setValue(123).build_transaction({
      'nonce': w3.eth.get_transaction_count("0xSender"),
      'gas': 200000,
  })
  signed_tx = w3.eth.account.sign_transaction(tx, "YOUR_PRIVATE_KEY")
  w3.eth.send_raw_transaction(signed_tx.rawTransaction)
```

---

## 🔍 Common Use Cases

Check Latest Block
```python
  print("Latest Block:", w3.eth.get_block('latest').number)
```
Listen to Events
```python
  event_filter = contract.events.ValueChanged.create_filter(fromBlock='latest')
  for event in event_filter.get_new_entries():
      print("Event:", event)
```
---

## ⚠️ Security Notes

- Never hardcode private keys! Use environment variables.
- Test on testnets before mainnet.
- Use Web3.py v6+.

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
