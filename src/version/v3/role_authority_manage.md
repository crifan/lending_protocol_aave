# 权限和角色管理

* AAVE协议V3：System roles, responsibilities and threat model 
  * 概述 
    * Aave 协议实现了一个访问控制列表，用于区分可以分配给协议上不同实体的权限和/或利益。这些角色和持有者由 ACLManager 合约管理。ACLManager 跟踪各个角色及其持有者，并允许角色管理员管理角色。角色管理员本身也是一个由DEFAULT_ADMIN_ROLE 管理的角色。 
    * 管理协议各个组成部分的合约，包括 ACLManager 和 Pool 的是 PoolAddressesProvider。地址提供者跟踪各种协议模块，并且有能力更新指针（例如，更新 ACLManager 合约）或更新代理合约的实现（例如，更新 Pool 实现）。PoolAddressesProvider 由 Aave Governance 拥有，并指定DEFAULT_ADMIN_ROLE的初始持有者。在以太坊以外的网络中，要么使用跨链治理桥（https://github.com/aave/governance-crosschain-bridges），要么使用社区多签来管理 PoolAddressesProvider。 
  * 详解 
    * 角色的权力和责任 
      * 下面我们概述了各个角色的权力和责任。FLASH_BORROWER 和 BRIDGE 的直接责任较少，主要可以访问协议的特定功能，而管理员角色则拥有处理风险或配置参数的权力和责任。 
        * FLASH_BORROWER 
          * 闪贷者这个角色的持有人将有闪贷的溢价豁免(不包括简单的闪贷)。 
        * BRIDGE 
          * holder可以执行mintUnbacked()和backUnbacked()。 
        * ASSET_LISTING_ADMIN = 资产列表管理员 
          * 此角色的持有者可以: 
            * 更新资产oracle源和备份oracle。 
            * 向Aave市场添加新资产。 
        * RISK ADMIN=风险管理 
          * 此角色的持有者可以: 
            * 更新预言机哨兵的宽限期。 
            * 更新准备金参数，如准备金系数、上限、E-Mode门类别、借款开启、允许稳定借款、冻结/解冻、LTV、流动性清算阈值、清算奖金(不能暂停/取消暂停或激活激活/停用准备金)。 
            * 创建新的和更新现有的电子模式类别(不是类别0)。 
            * 更新无担保的铸币厂上限和清算协议费用。 
        * ACL_ADMIN 
          * 在ACLManager中管理角色admins 
        * EMERGENCY_ADMIN 
          * 该角色的持有者可以暂停和取消暂停池或者个人储备。 
        * POOL_ADMIN 
          * 此角色的持有者可以更新令牌实现，删除，(暂停)和(取消)激活储备，更新保费以及所有资产清单管理员和风险管理员可以做的事情 
    * Threat Model=威胁模型 
      * Malicious Actors=恶意行为者 
        * 下面概述了恶意参与者可能造成的潜在危害，如果该参与者扮演这些角色之一 
          * ORACLES 
            * 恶意预言机可能提供无效的价格，使其能够借入超过应有的金额，或者基于无效价格进行清算。 
          * SEQUENCER 
            * 如4.6节所述，序列器在滚动中的排序上具有重大影响力，使其能够在资产价格大幅下跌时，从Aave的用户中提取大量价值。这可以通过拒绝供应和还款行为，并清算HF低于1的用户来实现，有效地剥夺用户在崩盘中保护自己免于清算的能力。 
          * FLASH_BORROWER 
            * 如果该地址是一个代理，它可以允许任何人通过它调用闪电贷以免除所有费用。这将导致闪电贷的流动性提供者没有溢价。 
          * BRIDGE 
            * 如果担任此角色的合约/地址变得恶意（或存在缺陷），它可能会增发至不受支持的上限，并永不支持，实际上允许它从流动性提供者那里窃取未支持的资金。 
          * ASSET_LISTING_ADMIN 
            * 攻击者可以升级预言机源，使协议处于与恶意预言机相同的状态。或者，攻击者可以列出一个具有恶意aToken（或债务令牌debttoken）实现的资产，允许他们提取存放在该资产中的任何资金。 
          * RISK_ADMIN 
            * 攻击者可以将清算门槛降至0并清算用户。这可以在同一交易或捆绑中原子化完成。 
          * EMERGENCY_ADMIN 
            * 攻击者可以暂停池，或解除暂停不安全的池。与市场崩溃同时发生时，攻击者可以关闭池，然后原子化地执行序列（开启 * 清算 * 关闭），使他成为唯一的清算人。 
          * POOL_ADMIN 
            * 攻击者可能执行RISK_ADMIN或ASSET_LISTING_ADMIN的攻击，或更换现有代币实现为只能由攻击者调用的rug()函数的新实现。 
          * ACL_ADMIN 
            * 攻击者可以给自己授予其他角色，然后执行其他管理员的攻击。 
          * ADDRESSES_PROVIDER 
            * 如果地址提供者的所有者是恶意的，那么治理已经崩溃，游戏结束。 
        * 上述潜在恶意攻击者的“攻击”的缓解措施应由Aave治理处理。当治理为特定行为者分配角色时，应使用中间件合约限制行为者使用该角色可以执行的操作，例如，对于ASSET LISTING ADMIN拒绝现有预言机提要的更新，仅允许添加。 
