# AAVE v2

* AAVE 白皮书v2= WhitePaper v2 
  * 背景介绍 
    * Aave协议标志着从分散的P2P借贷策略(贷方和借款人之间的直接贷款关系，如ETHLend)到基于池的策略的转变。贷款不需要单独匹配，而是依赖于汇集的资金、借款金额及其抵押品。这使得基于池状态的特征的即时贷款成为可能 
    * 开发Aave V2的主要动力是改进V1中实现的次优解决方案，具体如下: 
      * 无法升级aToken 
      * Gas效率低 
      * 简化架构 
        * 有利于通过模糊测试器和正式验证工具进行自动化测试 
      * 代码简化 
    * 目前在V1中实施的一些解决方案是在以太坊网络明显不同的时候设计和开发的。DeFi的指数级增长使交易数量增加了一倍，而以太坊的Istanbul伊斯坦布尔的发布，给Gas成本增加带来了进一步的压力 
  * V1升级到V2 主要升级点=改进点 
    * 功能点=升级点 概述
      * 固定利率存款 
      * 稳定借贷率 
      * 信用委托 
      * 变更抵押品 
      * 批处理闪电贷 
      * 债务代币化 
      * 社区治理 
    * 详解
      * 固定利率存款 
      * 稳定借贷率 
      * Borrowing=借款 
        * 信用委托=Credit Delegation 
          * 当用户在协议中存入抵押品时，他们可以通过调用相关债务令牌上的approveDelegation()轻松地将信用委托给任何地址 
            * [Debt Tokens | v2 | Developers (aave.com)](https://docs.aave.com/developers/v/2.0/the-core-protocol/debt-tokens#approvedelegation)
          * 请参阅信用委托指南了解更多细节 
            * [Credit Delegation | v2 | Developers (aave.com)](https://docs.aave.com/developers/v/2.0/guides/credit-delegation)
      * 变更抵押品 
      * 批处理闪电贷 = Flash Loans V2 
        * 详见：Flash Loan闪电贷
      * Tokenization 
        * 债务代币化=Debt Tokenization
        * 跟踪用户头寸 
          * 在Aave v2中，所有头寸都被标记。因此，要计算用户拥有的债务，您只需要为该用户的相关债务令牌调用balanceOf() 
          * 有关更多信息，请参阅aTokens和Debt Tokens部分 
            * [aTokens | v2 | Developers (aave.com)](https://docs.aave.com/developers/v/2.0/the-core-protocol/atokens)
            * [Debt Tokens | v2 | Developers (aave.com)](https://docs.aave.com/developers/v/2.0/the-core-protocol/debt-tokens#approvedelegation)
        * 批准ERC20/EIP20代币:LendingPool vs LendingPoolCore 
          * 去掉：LendingPoolCore，新增：LendingPool 
            * 在Aave v2中，去掉了，保存了所有协议的资产的，LendingPoolCore合约。资产直接在相关的aToken合约中持有，LendingPool是协议的“核心”合约。 
        * 支持WETH 
          * 在Aave v2中，为了确保整个协议的一致性，我们现在使用WETH(而不是像v1中那样使用ETH和占位符保留值)。因此，要使用ETH作为资产调用函数，请使用WETH地址 
            * [Main market | v2 | Developers (aave.com)](https://docs.aave.com/developers/v/2.0/deployed-contracts/deployed-contracts#supported-assets)
          * 当在协议中使用ETH时，还有一个ETH助手合约可以帮助包装/解包装ETH 
      * 社区治理 
      * 结构变化 
        * 地址提供程序注册表=Addresses Provider Registry 
          * 在多个市场中，将会有多个AddressesProviders。AddressesProviderRegistry将维护所有Aave市场地址提供程序的注册表 
        * 取代LendingPoolCore 
          * LendingPoolCore不再使用。只使用了LendingPool，这简化了在Aave v2上的集成和构建
  * 细节 
    * Deposit=存款 
      * 通过LendingPool赎回和取款，而不是通过aToken 
        * 在Aave v2中，几乎所有的操作都应该通过LendingPool合约执行。这与v1不同，在v1中，需要在aToken合约中调用aToken的赎回/提取 
        * 在v2中，你只需要在LendingPool合约上调用withdraw 
          * [LendingPool | v2 | Developers (aave.com)](https://docs.aave.com/developers/v/2.0/the-core-protocol/lendingpool#withdraw)
      * 删除了利息重定向功能 
        * 在Aave v2的初始版本中，不支持利息重定向。然而，该特性有可能在稍后通过治理过程添加回来 
    * aToken
    * Collateral trading=抵押物交易 
      * Aave协议V2提供了一种交换存储资产的方式，无论是否用作抵押品。这是通过以下方式利用v2闪贷实现的: 
        * flashLoan()函数由用户调用，传递接收方合同的地址作为参数，实现IFlashLoanReceiver接口，这是一个不可信的合同，应该由用户提前验证;要交换的基础资产列表，这些资产的数量列表和一个包含要交换的资产的额外参数以及用户选择的最大滑动量，都是编码的。 
        * 然后，接收方合同将使用收到的资金将其交换到目标资产，代表用户再次存入，并提取用户的Flash货币存款，以偿还Flash Loan。 
      * 举个例子： 
        * (i)用户在协议中存入了100个LINK和20个UNI，债务为100 USDC。他想把他的存款LINK和UNI都换成AAVE，而不需要在一次交易中偿还任何债务。 
        * (ii)用户调用flashLoan()函数，将包含执行操作的逻辑的接收者合约的地址、LINK和UNI的地址作为参数传递;100和200作为金额，并编码为要交换的资产地址(AAVE)， 2%作为交易的最大滑点。 
        * (iii)接收方合同将使用去中心化交易所将指定数量的LINK和UNI交换到AAVE。 
        * (iii)接收方合同将代表用户在AAVE协议中存放由此产生的AAVE。 
        * (iv)接收方合同将从用户那里以aLINK和aUNI的形式转移等值的闪现金额，将其赎回给LINK和UNI，并将批准池在闪贷结束时提取这些资金以偿还。 
    * Repay with collateral=以抵押物偿还 
      * 该功能也通过使用Flash Loans v2构建，允许用户将一个或多个资产作为协议中的抵押品，使用它们来部分或全部偿还其债务/头寸。与交换流动性和基于Flash贷款的所有功能一样，抵押品还款使用flashLoan()函数和接收者合约，实现IFlashLoanReceiver接口。向这个接收方传递一个要闪现并用于交换和偿还的抵押资产列表、这些资产的金额列表，以及要偿还债务的资产列表、要偿还的债务金额列表和每个债务资产的借贷模式(稳定或可变)列表。值得注意的是，在这种情况下，接收方合约将期望收到需要偿还的确切金额，这与互换流动性不同，互换流动性的预期金额是互换的确切抵押品。这个功能的流程是: 
        * (i)用户在协议中存入100 AAVE，并以可变利率支付200 USDC的债务。由于他目前没有可用的USDC资金来偿还贷款，他想将他的部分AAVE抵押品交换给USDC并用它来偿还贷款。 
        * (ii)用户调用flashLoan()函数作为参数传递:包含执行操作逻辑的接收者合约的地址，AAVE的地址，7作为交换的抵押品金额(估计AAVE需要覆盖200 USDC债务)，200作为偿还的债务金额，变量作为使用的借款模式。 
        * (iii)接收方合同将使用去中心化交易所将7 AAVE交换给USDC。 
        * (iv)接收方合约将使用掉期产生的USDC来代表用户偿还协议中的USDC债务。 
        * (iv)一旦债务被偿还，接收方将转移从用户那里归还闪现的AAVE所需的aAAVE金额，将其赎回为AAVE，并将批准池在闪贷交易结束时提取这些资金。 
        * (v)如果最终由于交换而有任何剩余的7 AAVE，这些资金将代表用户存入协议中或直接发送到他的钱包。 
