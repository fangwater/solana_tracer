# Solana_tracer
solana trace for coin and pool

## Word explain
### Liquidity pool
在去中心化金融（DeFi）中，池子（流动性池）需要流动性（Liquidity） 的核心原因是为了实现高效、低滑点的资产交易，并支撑整个去中心化交易所（DEX）的运作。

### 
流动性池通过预先存入两种代币（如 SOL/USDC），允许用户直接与池子交易，无需等待对手方。
例如：用户随时可以用 SOL 兑换 USDC，只要池子中有足够的 USDC 储备。

### LP（Liquidity provider）
每笔交易收取手续费（如 0.25%），按比例分配给流动性提供者。按 LP 份额分配。许多协议（如 Raydium）会额外发行治理代币（如 $RAY）奖励 LP，激励用户提供流动性。

### TVL（Total Value Locked）
最大单笔交易容量，交易量与TVL比率

### Pump.fun
### DEX
#### Raydium
#### Orca
### AMM 模型

## Tracing liquidity pool
### Events affect the liquidity pool
#### 用户添加流动性（Deposit）
用户向池子存入两种代币（如 SOL/USDC 交易对中的 SOL 和 USDC）,池子的流动性总量（TVL）增加, 池中代币的比例变化可能影响价格（若存入比例与当前池比例不一致）,用户获得 LP（流动性提供者）代币，代表其在池中的份额。

#### 用户移除流动性（Withdraw）
用户销毁 LP 代币，从池中提取对应的两种代币。池子的流动性总量（TVL）减少。池中代币比例可能变化，影响交易价格。

#### 用户交易（Swap）
用户通过池子兑换代币（例如用 SOL 兑换 USDC）。池中两种代币的数量发生变化（例如 SOL 减少，USDC 增加）。币价格根据恒定乘积公式（AMM 模型）重新计算，导致价格波动。

#### 套利行为
套利者利用池子价格与其他交易所（如 Serum 订单簿）的价差进行交易。池子价格被拉回与市场一致，但池中代币比例发生变化。

#### 流动性挖矿激励
用户质押 LP 代币参与 Raydium 的流动性挖矿（Farming）。激励可能吸引更多用户提供流动性，间接增加池子 TVL。
#### 协议参数调整
Raydium 协议或池子创建者调整参数（如手续费率、奖励分配）。
#### 订单簿交互（与 Serum 集成）
Raydium 的流动性池与 Serum 订单簿交互（如限价订单成交）。订单簿的成交可能触发从池子中提取流动性，导致池子代币数量变化。

### Tracing liquidity pool
#### 

## Raydium-sdk
### 
https://github.com/raydium-io/raydium-sdk-V2
