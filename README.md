# volumegauge

Volume Gauges for DeFi 

## Deployment (Mainnet)

1. Deploy volumegaugetracker.vy

2. Deploy swap_volumegauge.vy

3. Deploy with parameters (cDAI, cUSDC, DAI, USDC, DAI/ETH Aggregator, USDC/ETH Aggregator, swap contract, volumegaugetracker)

- Confirm code for constant of eth/usd aggregator address

  `ETHAGGREGATOR: constant(address) = 0x5f4eC3Df9cbd43714FE2740f5E3616155c5b8419`

- constructor parameters

```bash
Coins
    0x5d3a536E4D6DbD6114cc1Ead35777bAB948E3643 cDAI
    0x39AA39c021dfbaE8faC545936693aC917d5E7563 cUSDC

Underlying coins
    0x6B175474E89094C44Da98b954EedeAC495271d0F DAI
    0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48 USDC

Aggregators
    0x773616E4d11A78F511299002da57A0a94577F1f4 DAI / ETH
    0x986b5E1e1755e3C2440e960477f25201B0a8bbD4 USDC / ETH

Base
    0xA2B47E3D5c44877cca798226B7B8118F9BFb7A56  Cruve.fi: Compound Swap
```

4. Register swap_volumegauge address to volumegaugetracker using addGauge() in volumegaugetracker

## Usage (Mainnet)

- Approve token to the swap_volumegauge and run exchange (or exchange_underlying) instead of swap contract.

- Other operations are processed at swap contract.

## Deployment for Test (Rinkeby)

1. Deploy volumegaugetracker.vy

2. Deploy swap_volumegauge.vy

- Update code for constant of eth/usd aggregator address

  `ETHAGGREGATOR: constant(address) = 0x5f4eC3Df9cbd43714FE2740f5E3616155c5b8419`

  to

  `ETHAGGREGATOR: constant(address) = 0x8A753747A1Fa494EC906cE90E9f37563A8AF630e`

- constructor parameters

```bash
Coins
    0x6D7F0754FFeb405d23C51CE938289d4835bE3b14 cDAI
    0x5B281A6DdA0B271e91ae35DE655Ad301C976edb1 cUSDC

Underlying coins
    0x5592EC0cfb4dbc12D3aB100b257153436a1f0FEa DAI
    0x4DBCdF9B62e891a7cec5A2568C3F4FAF9E8Abe2b USDC

Aggregators
    0x74825DbC8BF76CC4e9494d0ecB210f676Efa001D DAI / ETH
    0xdCA36F27cbC4E38aE16C4E9f99D39b42337F6dcf USDC / ETH

Base
    0xA319E978505b19b5E145436Cc040c12E70e1840b  Cruve.fi: Compound Swap
```

3. Deploy test.sol on Rinkeby Testnet.

```bash
constructor parameter: deployed gauge address
```
## Test (Rinkeby)

- Test exchange

  Send cToken(cDAI or cUSDC) on Rinkeby to the deployed smart contract.

  Run "test_compound_token" transaction with parameters same as exchange of swap contract.

- Test exchange_underlying

  Send token(DAI or USDC) on Rinkeby to the deployed smart contract.

  Run "test_underlying_token" transaction with parameters same as exchange of swap contract.

- Deposit
 
  Test might fail as insufficient deposit amount.

  At that time, you can send cTokens(cDAI and cUSDC) to the deployed smart contract and run "deposit" for adding liquidity.

- Faucet Tokens

  https://app.compound.finance/

- Deployed addresses on Rinkeby (deposited only 1K cTokens ~ 20 underlying tokens)

```bash
0x042f2ef486192c633245a0324F60b1911a1Ac245 volumegaugetracker
0x8fB761472A1c466f2E09976ED04F0954D5E61B13 swap_volumegauge 
0x4BE8b1310537D477E9461e3671A553195c858190 Test contract
```

Contract Source Code of the Tokens(DAI, USDC) were not verified. So you won't be able to approve tokens to contracts easily. That's why I built this test contract.
