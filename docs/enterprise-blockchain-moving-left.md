# 企业区块链，向左移动

> 原文：<https://blog.web3labs.com/enterprise-blockchain-moving-left>

区块链作为一项技术仍在发展，我们对这项技术在建筑领域中的位置的理解也在发展。我喜欢把这种演变称为“向左移动”。为了理解这一点，我们需要一点背景知识。

开发人员和架构师最初将区块链网络作为某种分布式数据库来对待并不罕见。但它不是一个伟大的数据库，因为它从来没有被设计成一个功能。如果您要在运行分布式 Cassandra 集群或 HBase 之间做出选择，那么这两者之间的特性和特征，比如说，在您的私有网络中运行一堆 Geth 节点，是非常不同的。Geth 将无法匹配吞吐量，存储需求也不会很好地扩展，因为没有历史修剪。但是，当你通常会发现“企业区块链”的私人财团开始使用私人区块链网络时，他们这样做是因为他们希望存储私人数据，并与少数选定的合作伙伴共享。然而，在区块链上存储私有数据并不理想，因为所有节点都存储数据的相同副本。如果一个新节点被允许进入，它也将收到该数据的副本。

正因为如此，各种各样的机制被发明出来，让我们可以在更受限的群体中存储隐私数据，然后针对不太隐私的区块链网络锚定这些数据的存在。我认为这是保持私人数据私密性的唯一方法，也就是说，不要将其存储在区块链上。

根据不同的使用案例，我们在如何锚定数据方面拥有充分的灵活性。我们可能需要给一些数据打上时间戳，例如可以选择在事务中发布一种类型的[数据指纹](https://blog.web3labs.com/digital-fingerprints)。这将证明数据在该时间点的存在。我想到了基线协议，但也想到了更广泛的第 2 层解决方案。或者，我们希望证明某些数据是由某个特定的参与者签名的，并因此在区块链上发布该实体的公钥。为此，[去中心化的身份和可验证的凭证](https://blog.web3labs.com/the-case-for-decentralised-identity)是可探索的适用标准。这两个示例都将数据锚定到区块链，但是方向不同，目的也不同。考虑到这一点，我们可以围绕我们需要采取的步骤进行对话，以确保锚定过程不会泄露我们私人活动的任何重要细节，但我将把这一点留到另一篇博客文章中。
锚定过程的好处在于，它提供了可靠的加密证据来证明某些活动已经发生，这有助于简化各种系统和参与者之间复杂的集成过程。

在我们继续从右到左的旅程之前，我觉得先画出整体的画面会比较好。下图最初是受赫苏斯·鲁伊兹在 2020 年初的一篇文章的启发，题为[公共许可的区块链作为公共资源](https://www.linkedin.com/pulse/public-permissioned-blockchains-common-pool-resources-jesus-ruiz/)。在这篇文章中，Ruiz 支持公共许可的连锁店。

![public permissioned blockchain - comp](img/b594e76c3ed6b30b5c9f48f091ca2ddb.png)

我同意很多建议，尤其是关于区块链作为某种公共利益的观点。如果我们回到前面描述的数据锚定用例，我们可以开始问自己，为什么我需要一个私有的区块链来存储这些锚定？例如，如果定位点是一个公钥，我希望我的这个公钥尽可能广泛地分发。区块链给了我这种选择，因为他们证明了公钥的完整性，并能使它广泛可用。但是，如果出于时间戳的原因，它是一个锚点，并且我可以接受该锚点中的数据是公共的，那么为什么要将其存储在私有的区块链上呢？运营一个私人许可的区块链网络并不便宜。除了运行软件的通常生产成本之外，您还需要在治理过程中涉及许多外部合作伙伴。为了使一个网络变得有用和安全，你需要让许多成员加入到这个网络中，这就增加了这个过程的压力和成本。

鲁伊斯认为，通过转向“公共许可”网络，我们可以两全其美。由于网络是公共的，原则上任何公众成员都可以连接到网络并在其上执行交易。这可能需要付费，或者是每笔交易，或者是其他会员费用。因为它是许可的，所以运行节点的成员集可以被严格控制。这应该使治理过程易于管理，例如，您可以将合作伙伴的数量限制到足够小，但仍然足够大，以平衡分散的安全性和治理开销。Ruiz 的另一个论点是，这种设置还允许更可扩展的共识算法，这将实现更主流使用所需的吞吐量。

虽然这些观点在某种程度上仍然成立，但我也认为在区块链这个快速发展的世界，以及更广泛的网络 3 中，鲁伊斯文章中的古色开始显现。如果我们意识到只有我们愿意公开的数据才应该存储在区块链上，并且私有数据通过我们所参与的流程与此相关，那么我们为什么还需要公共许可链呢？如果我们只剩下可扩展性作为“公共许可”的许可部分有用的理由，我们很快就会在维护运行或成为这样一个网络的成员的开销成本方面遇到困难。这是因为可伸缩性是一个挑战，通过使用分片和第二层可以解决这个问题。工作证明的能源效率低下，这是比特币和以太坊的主要共识机制，在撰写本文时，这也将很快成为历史。这是因为以太坊，头号智能合同区块链，今年晚些时候移动到股权证明。然后，我们只剩下比特币作为主要的工作证明区块链，但由于比特币的局限性，我们无论如何都不会将其用于上述锚定用例。

同样，这也没有考虑到使用公共许可链的风险。你，作为网络的一员，或者一个简单的用户，很容易被阻止加入任何许可链。这在 Web3 环境中重新引入了 Web2 的第三方风险。在技术升级允许我们在没有高成本和大量吞吐量的情况下使用公共无许可链之后，公共许可网络成为这些网络运营商坚持旧的过时商业模式的最后尝试。

总之，这就是我们在企业区块链世界中向左移动的原因:

*   我们习惯了将私有数据锚定到公共区块链的过程

*   公共无许可链通过利益证明变得节能

*   分片和第 2 层解决方案允许以低成本实现必要的吞吐量

*   被排除在公共许可链之外的风险太高了

*   运行和参与您自己的许可网络的治理开销和复杂性是糟糕的事情，并且没有为用例提供额外的好处

Web3 是思维的转变，上面描述的需要时间来成熟。我希望这篇博文有助于照亮我们仍在进行的从最初的私人许可方法向更被视为开放和可用的实用工具的转变之旅。当然，这并没有消除私人许可的区块链着手解决的一些要求，但是通过新的工具和技术，我们可以更优雅地解决这些问题。

有任何问题或意见吗？我们希望收到您的来信！如果你想更多地了解区块链，它的成长和最新的发展，那么看看我们的[博客](https://blog.web3labs.com/)或者听听我们启发性的 [Web3 创新者播客](https://podcast.web3labs.com/)。