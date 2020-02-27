Sugarchain
==========
one-CPU-one-vote, the world's fastest PoW blockchain  
https://sugarchain.org


Yumekawa的含义
-----------------------
Sugarchain's first node software is called `Yumekawa (夢川)`. It can be translated in some ways.
 - "Yume (夢)" means dream and "Kawa (川)" means river. So it's `Dream River` in japanese.
 - The second letter "Kawa" stands for "Kawaii (可愛い)". In this case the meaning is `Dreamy Cute`.
 - Also Yumekawa replaces the word `Core` (ie: Bitcoin Core). We think it sounds a bit centralized.


技术细节
--------------
|||
| ---- | ---- |
|出块时间: | `5` seconds |
|难度算法: | SugarShield-N510 (基于Zcash's Digishield修改版 )|
|出块奖励: | `42.94967296` SUGAR|
|减半间隔: | `12,500,000` 个区块 (约 2 年)|
|总释放量: | `1,073,741,824` SUGAR|
|共识算法: | YespowerSugar (基于Yespower 1.0.1)|
|端  口: | 34230 (RPC 34229)|
|预  挖: | 无 (无 ICO, 无预售, 无区块奖励)|


全球最快的POW区块链
----------------------------------
- 5秒交易速度
  * 比 Bitcoin 快120倍
  * 比 Litecoin 快30倍
  * 比 Dogecoin 快12倍
- 稳定的交易时间:
  * Even if the hash power suddenly increases, the block time remains 5 seconds. It is against hash attacks.
- 不用为孤块担心: 
  * According to the testnet results, the average orphan rate is under 3% and no problem occurs.


更严格的减半
-----------------------------
- Halving is everything: 
  * Bitcoin is valuable because its total supply has been strictly limited, unlike traditional currencies. 
  * This total supply is controlled *only* by that halving. There is nothing else.
  * We made this halving better.
- 区块奖励: 
  * The block reward should be to a *power of two*, so that it halves correctly.
  * ie) `2^32/100000000 = 42.94967296 SUGAR`
- 减半计划: 
  * Interval `12500000 blocks (5^8*32)` which is about 2 years (exactly 1.9818619989852864... years).
  * The total number of times halving will occur is `33 times`, over the span of `66 years`.
- 总释放量: 
  * `1073741824 SUGAR` in theory, and `1073741823.875 SUGAR` in actual.
  * The difference is `0.125 SUGAR`. One Satoshi (0.00000001) limitation makes this difference. In addition, this number is meaningful. FYI: `1 GB = 1073741824 Byte (2^30)`.
  * The total supply of Sugarchain is about `51 times` greater than Bitcoin.
- Halving Chart: ![Halving Chart](_images/halving_chart.png)
- Halving Table: ![Halving Table](_images/halving_table.png)


每CPU一票
----------------
> "31/Oct/2008 Proof-of-work 本质上是每CPU一票"

Satoshi Nakamoto talked about the importance of decentralized mining in his whitepaper. We want to create a blockchain that anyone can do mining easily without any entry barriers.


- 仅限CPU挖矿
  * YespowerSugar (基于Yespower 1.0.1)是专为Sugarchain定制的算法, 不兼容于其它Yespower算法币种.
  * The minimum difficulty (powlimit) is set low enough for two reasons. The first is to handle fast block time; The second is to allow mining on slow CPUs.
- 挖矿效率: 
  * According to the test results, the most efficient is using 8 threads on a single CPU.
  * YespowerSugar is more suitable for older CPUs, because it is essentially a multi-threading resistor. Suitable for smartphones and raspberrypi.
- 无GPU: 无法通过GPU开采.
- 无ASIC: 无法通过ASIC开采.


其它优势
----------------
- 默认原生Segwit (Bech32) 地址: 开头为 `sugar1q...`
- Fast blockchain synchronization: Using sha256d in header indexing, the initial synchronization speed is as fast as Litecoin.


FAQ
---
- 硬盘空间需求: 
  * Blockchain size growth is around `10 MB per 1 day` and 3.65 GB per year.
- 网络规则: 
  * To prevent fraud and timestamp attacks, nodes should be within `70 seconds` of accurate internet time, or they will be banned.
- Selfish mining & time warp attack: 
  * Fraud techniques for manipulating timestamps are already known. We use a future time limit (FTL) to prevent this. Blocks that differ `60 seconds` or more from the current head will be banned. (credit: zawy12)
- 交易所上币: 
  * We do not have a listing plan at this moment. However, it will be discussed in our community and will be listed in the future. If you have any suggestions for exchange websites, contact us.


附录
--------
- Block time vs difficulty at first launching on testnet
  * To keep the block time 5 seconds, SugarShield-N510 adjusts the difficulty level. Unlike the Zcash's modification version, we use a moving average of `510 blocks` (about 42.5 minutes). It counts from block 1, an adjustment is made at block 511, and the actual control begins at block 512. [(log: time-diff)](https://github.com/sugarchain-project/website/blob/master/log/time_vs_difficulty-13536.log)
  * ![Blocktime vs Difficulty](_images/time_vs_difficulty.png)

- Nonce distribution at first launching on testnet 
  * The nonce is randomly well distributed. Difficulty changes but no bias. [(log: nonce-diff)](https://github.com/sugarchain-project/website/blob/master/log/nonce_vs_difficulty-13548.log)
  * ![Nonce vs Difficulty](images/nonce_vs_difficulty.png)

许可授权
-------
Sugarchain Yumekawa is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.
- Copyright (c) 2009-2010 Satoshi Nakamoto
- Copyright (c) 2009-2018 The Bitcoin Core developers
- Copyright (c) 2013-2019 Alexander Peslyak - Yespower 1.0.1
- Copyright (c) 2016-2018 The Zcash developers - DigiShieldZEC
- Copyright (c) 2018-2019 The Sugarchain developers
