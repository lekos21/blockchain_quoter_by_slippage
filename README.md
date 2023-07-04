# Maximum Swap Size Finder for a given Slippage
This Python script is designed to find the maximum swap size for a given slippage on different Ethereum-based decentralized exchanges (DEXs) such as Uniswap and Curve. The script uses binary search to find the swap size that results in a target slippage. It's predisposed for Uniswap (v2 and v3) and Curve. The code interrogates the DEX multiple times requesting a quotation on a trade, converging to a particular size where the slippage is equal to the target. 

## Requirements
* Python 3.6 or higher
* web3 Python library

## Setup
1. Install the required Python libraries with pip:
`pip install web3`
2. Replace the alchemy_url variable with your Alchemy API URL.
`alchemy_url = '...'`
3. define the target slippage and the tolerance of the convergence around it.
```python
target_slippage = 0.01  # 1%
tolerance = 0.05  # 0.05 = target_slippage between 0.95% and 1.05%
``` 
4. Define the pools you want to optimize for in the pools list. Each pool is represented as a list with the following format: [tokenA, tokenB, pool address, protocol, version, fee, name].
```python
pools = [
    ["0xae7ab96520DE3A18E5e111B5EaAb095312D7fE84", "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2", "0x4028DAAC072e492d34a3Afdbef0ba7e35D8b55C4", "uniswap", "v2", 0, "stETH-WETH-v2"],
    ...
]
```
## Usage
Run the script with Python:

`python optimal_swap.py`

The script will print the maximum swap size for each pool in the pools list. The maximum swap size is the amount of tokenA that results in the target slippage when swapped for the other token in the pool.

## Note
This script is for educational purposes only. Always do your own research and consider the risks before performing any transactions on Ethereum.
