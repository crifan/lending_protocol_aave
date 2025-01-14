# Granular borrowing power control

* AAVE协议V3：精细的借款能力控制 = Granular borrowing power control 
  * 概述 
    * 目前，各种流动性协议不允许在不最终导致清算的情况下减少资产的借款能力。当某个资产的风险轮廓发生变化时，这种限制尤其明显——例如，变得不可能在不清算先前借款人的情况下降低对该资产的暴露。 
    * 在 Aave V3 中，通过精细的借款能力控制，Aave治理可以将任何资产的借款能力降低至 0%，而不影响现有借款人（尽管如果被认为必要，仍然可以清算现有用户）。 
      * 在Aave V3中，可以将任何资产的借款能力降低到0%，而不会对现有借款人产生任何影响(如果认为有必要，仍然可以使用旧方法——清算现有用户)。 
  * 详解 
    * 粒度借贷能力控制设计包括将大多数流动性协议中通常使用的抵押品因素分为贷款价值比（LTV，定义了新借款的借贷能力）和清算阈值（定义了维持保证金，或换句话说，被视为抵押不足且因此受到清算的抵押品/债务比率）。这种能力，即独立于维持保证金设置借贷能力，允许更精细地控制与特定资产相关的风险，同时避免影响现有用户。在Aave V2中，这一功能已经实现，但主要被视为对借款人借款至维持保证金上限并因此立即被清算的一种软保护。 
  * 举例 
    * Alice希望使用具有0贷款价值比（LTV）和清算门槛大于0的资产进行借款。按常理这是不可能的，但Alice可以这样做： 
      1. 存入一个 LTV>0 的资产（例如，使用闪电贷） 
      2. 提供一个 LTV=0 的资产 
      3. 借款 
      4. 取出一个 LTV>0 的资产 
    * 这将使协议处于一个起始时担保资产LTV为0的位置 
    * Aave V3引入了更严格的LTV规则，因此现在可以实施实际的0借款能力，同时防止上述情况发生。这种保护要求使用多个资产作为抵押的借款人——其中一个或多个的LTV等于0，必须首先提取这些资产，因此不能提取LTV大于0的资产。在上述例子中，在V3中，Alice将不被允许执行最后一步。Alice将被要求首先取出LTV等于0的资产。因此，V3完全防止了这种情况。总的来说，细致的借款能力控制规定： 
      * 只要资产的LTV大于0且清算门槛大于0，用户可以借款。 
      * 如果某个资产的LTV被重设为0，用户不应再被允许对该资产进行借款。 
      * 使用多个资产作为抵押的借款人如果希望提取资产，必须在提取其他资产之前先提取所有LTV为0的资产。这适用于提取和转移。尽管如此，对于LTV不为0的资产仍然允许进行清算。 
      * 对于希望提高借款能力（接近清算门槛）的借款人，使用上述示例中解释的程序仍然是可以接受的。LTV与清算门槛之间的差值为借款人提供了一种柔性保护，是一种平均降低清算风险的方式，但清算门槛仍然被认为对协议是安全的。 
