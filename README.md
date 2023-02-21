# Smart-Contract-Security

## ERC777 Reentrancy Attack

Like ERC20, ERC777 is a standard for fungible tokens, and is focused around allowing more complex interactions when trading tokens. More generally, it brings tokens and Ether closer together by providing the equivalent of a msg.value field, but for tokens.

The main reason for this exploit was that in any transfer of tokens, an ERC777 contract is basically going to:

1. Call the sender of tokens
2. Execute the transfer (i.e., swap balances and reduce allowances if appropriate)
3. Call the recipient of tokens

Now, if the sender is a smart contract instead of an address, a reentrancy attack can be orchestrated.

[This blog by openzeppelin explains this particular attack in more detail.](https://blog.openzeppelin.com/exploiting-uniswap-from-reentrancy-to-actual-profit/)

[This issue was also reported in uniswap audit report - 2018](https://github.com/ConsenSys/Uniswap-audit-report-2018-12#31-liquidity-pool-can-be-stolen-in-some-tokens-eg-erc-777-29)
