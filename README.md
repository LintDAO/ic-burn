## ic-burn

ic-burn is a sample project to port rust's burn library to IC. 

It uses IC's random number API raw_rand instead of burn's getrandom.

Train an LSTM (Long Short-Term Memory) model and reason about the corresponding price through the Coin ICP price history in 2024.

## Prerequisites
Rust: Version 1.85.0.

DFX: Version 0.24.3.

Node.js: Version v16.13.1.


## Installation
```bash
npm i
dfx deploy
```
## Useage
1. Must upload `/assets/icp_history_price_2024.json` via the front-end on the first run, otherwise there is no data for train or predict.

2. The following `train` method must be executed for the first run, otherwise model initialization is not possible
```bash
dfx canister call ic_burn_backend train '(5:nat64)'
```
Show: 
```bash
2025-04-18 07:40:02.643838571 UTC: [Canister bkyz2-fmaaa-aaaaa-qaaaq-cai] Epoch 1: Loss = 0.07873835
2025-04-18 07:40:02.643838571 UTC: [Canister bkyz2-fmaaa-aaaaa-qaaaq-cai] Epoch 2: Loss = 0.0785257
2025-04-18 07:40:02.643838571 UTC: [Canister bkyz2-fmaaa-aaaaa-qaaaq-cai] Epoch 3: Loss = 0.07831413
2025-04-18 07:40:02.643838571 UTC: [Canister bkyz2-fmaaa-aaaaa-qaaaq-cai] Epoch 4: Loss = 0.07810363
2025-04-18 07:40:02.643838571 UTC: [Canister bkyz2-fmaaa-aaaaa-qaaaq-cai] Epoch 5: Loss = 0.07789419
2025-04-18 07:40:02.643838571 UTC: [Canister bkyz2-fmaaa-aaaaa-qaaaq-cai] Train consumed 4134426 cycle
```

3. Run predict
```bash
dfx canister call ic_burn_backend predict
```
Show:
```bash
(3.2142498 : float32)
```
