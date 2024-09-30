# Siloed Borrowing

* AAVE协议V3：Siloed Borrowing=孤立借贷=单独借贷=筒仓式借贷 
  * 概述 
    * 孤立借贷允许具有潜在可操纵的资产(例如非流动性的Uni V3对)在Aave上作为单一借贷资产列出。这意味着，如果一个资产被配置为孤立的，它就不能与其他资产同时在一个位置上被借用。这有助于降低与此类资产相关的风险，避免影响协议的整体偿付能力 
  * 详解 
    * 此功能允许具有潜在可操作的预言机的资产(例如非流动性的Uni V3对)在Aave上作为单一借款资产列出。这意味着，如果一个资产被配置为孤立的，它就不能与其他资产同时在一个位置上被借用。这有助于降低与此类资产相关的风险，避免影响协议的整体偿付能力。 
    * 孤立借贷可以被认为是孤立模式Isolation Mode对抵押品的补充特征:其中一个表明资产是否需要是头寸中唯一借入的资产(孤立)，另一个表明抵押品是否可以是头寸中唯一受健康因素影响的抵押品(孤立抵押品)。 
    * 由Aave Governance选择的风险管理或池管理可以调用setSiloedBorrowing以在Siloed Borrowing模式下设置资产。 
  * 供应孤立资产 
    * 用户可以像使用pool中的supply()方法提供任何其他资产一样提供Siloed资产。但是，资产将不能用作抵押品，即提供的金额不会添加到用户的总抵押品余额中。 
  * 借入孤立资产 
    * 借用孤立资产的用户不能在借用其他资产的同时借用处于某个位置的孤立资产。 
    * 用户可以使用池中的borrow()方法借用竖井资产。索尔，只有当: 
      * 这是首先借用代的地址 
    * 或 
      * 现有用户债务属于同样的孤立资产。 
    * 要检查用户是否处于孤岛借用状态，您可以使用AaveProtocolDataProvider.sol上的getSiloedBorrowing()方法查看用户借用的基础资产是否处于孤岛。 
  * 检查是否为单独借贷保留 
    * 代码
```js
import {AaveProtocolDataProvider} from '@aave/core-v3/contracts/misc/AaveProtocolDataProvider.sol'; 
AaveProtocolDataProvider poolDataProvider = AaveProtocolDataProvider(provider.getPoolDataProvider()); 
// address of the underlying asset 
address asset = "0x..."; 
protocolDataProvider.getSiloedBorrowing(asset);
```

* 常见问题 
  * 用户如何进入孤立借贷状态? 
    * 用户在首次成功借用孤立资产时自动进入孤立借贷状态。 
  * 用户如何退出孤立借贷状态? 
    * 用户必须偿还所有债务才能退出孤立借贷状态。 
  * 目前在Aave V3市场中是否有资产被孤立? 
    * 目前，在任何V3市场中都没有标记孤立的资产。如果需要，风险或资产池管理员可以根据市场情况将已列出的资产设置为孤岛。此功能可用于风险较高的新资产上市。 
* 相关代码 
  * [aave-v3-core/contracts/protocol/libraries/logic/ValidationLogic.sol at master · aave/aave-v3-core (github.com)](https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/ValidationLogic.sol#L292)
    * `uint256 maxLoanSizeStable = vars.availableLiquidity.percentMul(params.maxStableLoanPercent);`
