# 核心的类和代码

* AAVE协议的核心类和代码 
  * Smart Contract - Aave v3 
    * Smart Contract - Aave v3 PoolAddressesProvider 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/configuration/PoolAddressesProvider.sol
    * Smart Contract - Aave v3 ACLManager 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/configuration/ACLManager.sol
    * Smart Contract - Aave v3 Pool 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/pool/Pool.sol
    * Smart Contract - Aave v3 L2Pool 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/pool/L2Pool.sol
    * Smart Contract - Aave v3 Pool Configurator 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/pool/PoolConfigurator.sol
    * Smart Contract - Aave v3 DefaultReserveInterestRateStrategy 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/pool/DefaultReserveInterestRateStrategy.sol
    * Smart Contract - Aave v3 Upgradability - BaseImmutableAdminUpgradeabilityProxy 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/aave-upgradeability/BaseImmutableAdminUpgradeabilityProxy.sol
    * Smart Contract - Aave v3 Upgradability - InitializableImmutableAdminUpgradabilityProxy 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/aave-upgradeability/InitializableImmutableAdminUpgradeabilityProxy.sol
    * Smart Contract - Aave v3 Upgradability - VersionedInitializable 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/aave-upgradeability/VersionedInitializable.sol
    * Smart Contract - Aave v3 Global configurations - Reserve Configuration 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/configuration/ReserveConfiguration.sol
    * Smart Contract - Aave v3 Global configurations - User Configuration 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/configuration/UserConfiguration.sol
    * Logic Libraries 
      * Smart Contract - Aave v3 Logic Libraries - Borrow Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/BorrowLogic.sol
      * Smart Contract - Aave v3 Logic Libraries - Bridge Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/BridgeLogic.sol
      * Smart Contract - Aave v3 Logic Libraries - Calldata Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/CalldataLogic.sol
      * Smart Contract - Aave v3 Logic Libraries - Configurator Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/ConfiguratorLogic.sol
      * Smart Contract - Aave v3 Logic Libraries - EMode Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/EModeLogic.sol
      * Smart Contract - Aave v3 Logic Libraries - Flash Loan Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/FlashLoanLogic.sol
      * Smart Contract - Aave v3 Logic Libraries - Generic Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/GenericLogic.sol
      * Smart Contract - Aave v3 Logic Libraries - Isolation Mode Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/IsolationModeLogic.sol
      * Smart Contract - Aave v3 Logic Libraries - Liquidation Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/LiquidationLogic.sol
      * Smart Contract - Aave v3 Logic Libraries - Pool Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/PoolLogic.sol
      * Smart Contract - Aave v3 Logic Libraries - Reserve Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/ReserveLogic.sol
      * Smart Contract - Aave v3 Logic Libraries - Supply Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/SupplyLogic.sol
      * Smart Contract - Aave v3 Logic Libraries - Validation Logic 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/logic/ValidationLogic.sol
    * Math Libraries 
      * Smart Contract - Aave v3 Math Libraries - Math Utils 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/math/MathUtils.sol
      * Smart Contract - Aave v3 Math Libraries - Percentage Math 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/math/PercentageMath.sol
      * Smart Contract - Aave v3 Math Libraries - WadRayMath 
        * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/math/WadRayMath.sol
    * Smart Contract - Aave v3 AToken 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/tokenization/AToken.sol
    * Smart Contract - Aave v3 VariableDebtToken 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/tokenization/VariableDebtToken.sol
    * Smart Contract - Aave v3 StableDebtToken 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/tokenization/StableDebtToken.sol
    * Smart Contract - Aave v3 AaveOracle 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/misc/AaveOracle.sol
    * Smart Contract - Aave v3 L2Encoder 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/misc/L2Encoder.sol
    * Smart Contract - Aave v3 Price Oracle Sentinel 
      * https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/configuration/PriceOracleSentinel.sol
    * Smart Contract - Aave v3 Periphery - Rewards Controller 
      * https://github.com/aave/aave-v3-periphery/blob/master/contracts/rewards/RewardsController.sol
    * Smart Contract - Aave v3 Emission Manager 
      * https://github.com/aave/aave-v3-periphery/blob/master/contracts/rewards/EmissionManager.sol
    * Smart Contract - Aave v3 Collector 
      * https://github.com/bgd-labs/aave-collector-unification/blob/main/src/contracts/Collector.sol
    * Smart Contract - Aave v3 GhoOracle 
      * https://github.com/aave/gho-core/blob/27a86dfe0bcbbef2a1809d2b8eaee7a7ca1a37d5/src/contracts/facilitators/aave/oracle/GhoOracle.sol
    * Smart Contract - Aave v3 GhoAToken 
      * https://github.com/aave/gho-core/blob/27a86dfe0bcbbef2a1809d2b8eaee7a7ca1a37d5/src/contracts/facilitators/aave/tokens/GhoAToken.sol
    * Smart Contract - Aave v3 GhoVariableDebtToken 
      * https://github.com/aave/gho-core/blob/main/src/contracts/facilitators/aave/tokens/GhoVariableDebtToken.sol
    * Smart Contract - Aave v3 GhoStableDebtToken 
      * https://github.com/aave/gho-core/blob/27a86dfe0bcbbef2a1809d2b8eaee7a7ca1a37d5/src/contracts/facilitators/aave/tokens/GhoStableDebtToken.sol
    * Smart Contract - Aave v3 GhoInterestRateStrategy 
      * https://github.com/aave/gho-core/blob/27a86dfe0bcbbef2a1809d2b8eaee7a7ca1a37d5/src/contracts/facilitators/aave/interestStrategy/GhoInterestRateStrategy.sol
    * Smart Contract - Aave v3 GhoDiscountRateStrategy 
      * https://github.com/aave/gho-core/blob/27a86dfe0bcbbef2a1809d2b8eaee7a7ca1a37d5/src/contracts/facilitators/aave/interestStrategy/GhoDiscountRateStrategy.sol
    * Smart Contract - Aave Safety Module Staked Aave v3 
      * https://github.com/bgd-labs/aave-stk-v1-5/blob/main/src/contracts/StakedAaveV3.sol
  * Smart Contract - Aave v2 
    * Smart Contract - Aave v2 LendingPoolAddressProvider 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/configuration/LendingPoolAddressesProvider.sol
    * Smart Contract - Aave v2 LendingPool 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/lendingpool/LendingPool.sol
    * Smart Contract - Aave v2 LendingPoolCollateralManager 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/lendingpool/LendingPoolCollateralManager.sol
    * Smart Contract - Aave v2 DefaultReserveInterestRateStrategy 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/lendingpool/DefaultReserveInterestRateStrategy.sol
    * Smart Contract - Aave v2 LendingPoolConfigurator 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/lendingpool/LendingPoolConfigurator.sol
    * Smart Contract - Aave v2 BaseImmutableAdminUpgradeabilityProxy 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/libraries/aave-upgradeability/BaseImmutableAdminUpgradeabilityProxy.sol
    * Smart Contract - Aave v2 InitializableImmutableAdminUpgradeabilityProxy 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/libraries/aave-upgradeability/InitializableImmutableAdminUpgradeabilityProxy.sol
    * Smart Contract - Aave v2 VersionedInitializable 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/libraries/aave-upgradeability/VersionedInitializable.sol
    * Smart Contract - Aave v2 Global configurations - Reserve Configuration 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/libraries/configuration/ReserveConfiguration.sol
    * Smart Contract - Aave v2 Global configurations - User Configuration 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/libraries/configuration/UserConfiguration.sol
    * Smart Contract - Aave v2 Logic libraries - GenericLogic 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/libraries/logic/GenericLogic.sol
    * Smart Contract - Aave v2 Logic libraries - ReserveLogic 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/libraries/logic/ReserveLogic.sol
    * Smart Contract - Aave v2 Logic libraries - ValidationLogic 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/libraries/logic/ValidationLogic.sol
    * Smart Contract - Aave v2 Math libraries - MathUtils 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/libraries/math/MathUtils.sol
    * Smart Contract - Aave v2 Math libraries - PercentageMath 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/libraries/math/PercentageMath.sol
    * Smart Contract - Aave v2 Math libraries - WadRayMath 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/libraries/math/WadRayMath.sol
    * Smart Contract - Aave v2 AToken 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/tokenization/AToken.sol
    * Smart Contract - Aave v2 VariableDebtToken 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/tokenization/VariableDebtToken.sol
    * Smart Contract - Aave v2 StableDebtToken 
      * https://github.com/aave/protocol-v2/blob/master/contracts/protocol/tokenization/StableDebtToken.sol
    * Smart Contract - Aave v2 Aave Oracle 
      * https://github.com/aave/protocol-v2/blob/master/contracts/misc/AaveOracle.sol
    * Smart Contract - Aave v2 Lending Rate Oracle 
      * https://etherscan.io/address/0x8A32f49FFbA88aba6EFF96F45D8BD1D4b3f35c7D
    * Smart Contract - Aave v2 WrappedTokenGatewayV2 
      * https://etherscan.io/address/0xEFFC18fC3b7eb8E676dac549E0c693ad50D1Ce31
    * Smart Contract - Aave v2 Collector 
      * https://etherscan.io/address/0x464C71f6c2F760DdA6093dCB91C24c39e5d6e18c
  * 其他 
    * Smart Contract - new Aave Safety Module (stkABPT and stkGHO) 
      * https://github.com/bgd-labs/stake-token/blob/main/src/contracts/StakeToken.sol
    * Smart Contract - GSM 
      * https://github.com/aave/gho-core/blob/c351f895b4eadde317157c4e456690689c2a4a79/src/contracts/facilitators/gsm/Gsm.sol
    * Smart Contract - FixedPriceStrategy 
      * https://github.com/aave/gho-core/blob/c351f895b4eadde317157c4e456690689c2a4a79/src/contracts/facilitators/gsm/priceStrategy/FixedPriceStrategy.sol
    * Smart Contract - FixedFeeStrategy 
      * https://github.com/aave/gho-core/blob/c351f895b4eadde317157c4e456690689c2a4a79/src/contracts/facilitators/gsm/feeStrategy/FixedFeeStrategy.sol
    * Smart Contract - TransparentUpgradeableProxy 
      * https://github.com/bgd-labs/solidity-utils/blob/7a7548c1d01f011febdb1c0d47e52c7ec6c30f9d/src/contracts/transparent-proxy/TransparentUpgradeableProxy.sol
    * Smart Contract - Governance 
      * https://github.com/bgd-labs/aave-governance-v3/blob/main/src/contracts/Governance.sol
    * Smart Contract - VotingStrategy 
      * https://github.com/bgd-labs/aave-governance-v3/blob/main/src/contracts/voting/VotingStrategy.sol
    * Smart Contract - GovernancePowerStrategy 
      * https://github.com/bgd-labs/aave-governance-v3/blob/main/src/contracts/GovernancePowerStrategy.sol
    * Smart Contract - VotingMachine 
      * https://github.com/bgd-labs/aave-governance-v3/blob/main/src/contracts/voting/VotingMachine.sol
    * Smart Contract - DataWarehouse 
      * https://github.com/bgd-labs/aave-governance-v3/blob/main/src/contracts/voting/DataWarehouse.sol
    * Smart Contract - Executor 
      * https://github.com/bgd-labs/aave-governance-v3/blob/main/src/contracts/payloads/Executor.sol
    * Smart Contract - PayloadsController 
      * https://github.com/bgd-labs/aave-governance-v3/blob/main/src/contracts/payloads/PayloadsController.sol
