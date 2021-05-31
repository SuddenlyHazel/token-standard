# Internet Computer Token Standard

This standard tries to introduce a simple ERC20-like common interface which could be used for tokens on Dfinity's Internet Computer.

The candid interfaces are included in the `candid` directory. The `token.did` is the actual interface that includes the basic functionality of the
token that is mandatory to implement by all tokens. The idea was to keep the interface as simple and unopinionated as possible. 


In addition to the main token interface, we also list several other optional features that we feel could be useful add-ons to tokens in the future given the 
unique challenges of the Internet Computer. These are listed in the `extensions` directory. To start, we listed 3 extenisons, however we hope the community will add more overtime. The first 3 extensions are:

  1. BURNABLE: The token can be burned and destroyed, reducing the supply.
  2. DEX: To make the token automatically convertible to Cycles, so the captured fees can
help pay for the canister costs.
  3. HISTORY: To make the transaction log visible and scalable by using archive canisters.

The HISTORY extension is a way to address the question of 'how/where do I store historical transactions for my token/token holders?' and 'how do I do it in a scalable/futureproof way?'. Since the IC uses orthogonal persistence, this is a unique challenge/question many tokens will have. 

The DEX extensions is a way to address the question of 'who is responsible for paying for the cycles/computation related to my token canister, transfers, queries, etc. and to essentially keep my token running?'. Since the IC uses a reverse gas model, this is a unique challenge since users won't necessarily be paying for the computation with each transaction/transfer. So the idea is that tokens could potentially implement a transaction fee in the native token, which could then be automatically converted into cycles in order to cover the cost of computation, transfers, queries, etc. So essentially users would be covering the costs, but in a seamless, user friendly, and abstracted way. The transaction fee would also be useful to deter spam, which would definitely become an issue if tokens had no transaction fee and users were not responsible in any way for paying for the computation related to the token. 
