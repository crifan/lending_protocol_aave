# 借贷协议：AAVE

* 最新版本：`v1.0.0`
* 更新时间：`20240930`

## 简介

整理介绍区块链和加密货币领域中的借贷协议龙头之一：AAVE。先是概述和核心逻辑架构；然后是借贷协议，包括deposit存款、borrow借款、repay偿还、redeem赎回、liquidation清算和借贷利率模型；清算包括健康因子；以及子模块，包括aToken及代币的作用、Governance治理、Safety Module安全模块、Flash Loan闪电贷、稳定币GHO、Credit Delegation信用委托、Debt Tokenization债务代币化；以及利率模型，包括可变利率、稳定利率、两者对比、各种参数；以及三种版本AAVE v1、v2、v3，以及相关的Gas优化、E-Mode、Isolation Mode、Portal、Risk Management的Granular borrowing power control、Price Oracle Sentinel、Siloed Borrowing、权限和角色管理、协议特性、Multiple Rewards and Claim；以及AAVE和其他的对比，比如Compound；再就是开发相关的核心类和代码、V3合约概览、审计报告、漏洞赏金；最后附录加上名字术语、AAVE资料、发展进化历史等。

## 源码+浏览+下载

本书的各种源码、在线浏览地址、多种格式文件下载如下：

### HonKit源码

* [crifan/lending_protocol_aave: 借贷协议：AAVE](https://github.com/crifan/lending_protocol_aave)

#### 如何使用此HonKit源码去生成发布为电子书

详见：[crifan/honkit_template: demo how to use crifan honkit template and demo](https://github.com/crifan/honkit_template)

### 在线浏览

* [借贷协议：AAVE book.crifan.org](https://book.crifan.org/books/lending_protocol_aave/website/)
* [借贷协议：AAVE crifan.github.io](https://crifan.github.io/lending_protocol_aave/website/)

### 离线下载阅读

* [借贷协议：AAVE PDF](https://book.crifan.org/books/lending_protocol_aave/pdf/lending_protocol_aave.pdf)
* [借贷协议：AAVE ePub](https://book.crifan.org/books/lending_protocol_aave/epub/lending_protocol_aave.epub)
* [借贷协议：AAVE Mobi](https://book.crifan.org/books/lending_protocol_aave/mobi/lending_protocol_aave.mobi)

## 版权和用途说明

此电子书教程的全部内容，如无特别说明，均为本人原创。其中部分内容参考自网络，均已备注了出处。如发现有侵权，请通过邮箱联系我 `admin 艾特 crifan.com`，我会尽快删除。谢谢合作。

各种技术类教程，仅作为学习和研究使用。请勿用于任何非法用途。如有非法用途，均与本人无关。

## 鸣谢

感谢我的老婆**陈雪**的包容理解和悉心照料，才使得我`crifan`有更多精力去专注技术专研和整理归纳出这些电子书和技术教程，特此鸣谢。

## 其他

### 作者的其他电子书

本人`crifan`还写了其他`150+`本电子书教程，感兴趣可移步至：

[crifan/crifan_ebook_readme: Crifan的电子书的使用说明](https://github.com/crifan/crifan_ebook_readme)

### 关于作者

关于作者更多介绍，详见：

[关于CrifanLi李茂 – 在路上](https://www.crifan.org/about/)
