# 琢磨钻研：Abstract  -  2. 交易 (Transactions)


## **Abstract.** 

一个纯粹的点对点版本的电子现金系统，将允许在线支付直接从一方发送到另一方，而无需通过金融机构。数字签名虽然提供了部分解决方案，但，若是仍然需要被信任的第三方来防止双重支出的话，那么电子支付的主要优势就被抵消了。我们提出一个方案，使用点对点网络去解决双重支出问题。点对点网络将为每笔交易标记时间戳，方法是：把交易的散列数据录入一个不断延展的、以散列为基础的工作证明链上，形成一个如非完全重做就不可能改变的记录。最长链，一方面用来证明已被见证的事件及其顺序，与此同时，也用来证明它来自于最大的 CPU 算力池。只要绝大多数 CPU 算力被良性节点控制 —— 即，它们不与那些尝试攻击网络的节点合作 —— 那么，良性节点将会生成最长链，并且在速度上超过攻击者。这个网络本身需要最小化的结构。信息将以最大努力为基本去传播，节点来去自由；但，加入之时总是需要接受最长的工作证明链作为它们未参与期间所发生之一切的证明。

一个纯粹的点对点的电子现金系统，让任何人都能直接在线支付，无需金融机构。数字签名能解决部分问题，但，如果还要靠信任第三方来防止“一币多花”，电子支付的主要优势就被没了。我们提出，用点对点网络解决双重支付问题。该网络给每笔交易标记时间戳，方法是：把交易哈希值打包记录到一条不断延展的、以散列为基础的工作量证明链上，谁想篡改记录就得重做所有计算。最长的链，既用于证明所见证事件的顺序，也证明它来自最大的 CPU 算力池。只要大多数算力掌握在诚实节点手里（即，不与那些尝试攻击网络的节点合作），这些节点将会生成最长链，攻击者追不上。网络本身需要最简单的结构。消息尽力而为地广播，而节点随时可加入或离开，同时，接受最长的工作量证明链作为他们离开期间所发生事件的证明。


From one party to another
> 第一句，又能看到这样的毛病。第一版，又是僵硬遵循原文结构。
> 你看别人英语本文，都是省略的。说another，而不是another party。你这翻译过来，怎么就不能省略了呢？说成更简洁的形式？
> 允许从一方发到另一方，不就相当于说是任何人都可以吗？
> 
> 
> Gemini：
> 
> 中文中，当说到“让任何人都能直接在线支付”时，“任何人”本身就包含了“从一个（任何）人发送到另一个（任何）人”的含义。
> 
> 如果再啰嗦地加上“由一方直接发送给另一方”，显得重复和不自然。这种省略符合中文表达习惯，是意合（注重意思的传达）优于形合（注重结构的对应）的体现。
> 
> 通过“让任何人都能”，它巧妙地概括了“from one party to another”所蕴含的“点对点”和“普适性”（any two parties）的意义。简洁、有力，符合中文表达习惯。



> 之后一句，依旧僵硬的照搬，
> 提供了部分解决方案  VS  能解决部分问题。
> 表达的是一个意思，但就是更清爽的版本。



“一币多花”
> 这里可能是个大胆的动作，不确定是否合适。在第二版中，之后提到double spending时，也用了这样的方式。但第一次时，我们是不是得用更正式的？就直接说成双重支付？





lost
> 第一版里，被翻译作，抵消，其实很妙。上文刚说了数字签名的优势，然后来说这个缺点，用抵消这个词体现出好坏之间的冲突。
> 
> 精妙地传达了`lost`在这里的内涵 —— 优势与劣势的冲突与中和。
> 
> 
> 你对“抵消”一词的玩味非常到位。
> “没了”是状态的描述，是平的。“抵消”是力与力的对抗，是立体的。
> 它描绘了一个动态过程：优势建立，然后被一个缺陷所摧毁。这个词本身就充满了戏剧张力，精准还原了原文中“优势与劣身”的内在冲突。





录入  VS  打包记录到
> 英文中非常好表达，对吧？只需说hashing就好。但中文里，就得找到相应的好词。而很明显，第二版是更好。
>
> 7.4：
> “将……打包，并录入”，很明显，这就是更好的版本，又把两个步骤拆得很清晰。



形成一个如非完全重做就不可能改变的记录  VS  谁想篡改记录就得重做所有计算
> 又是【严格遵循原文结构】和【从原文含义出发】之间的冲突。第一版，严苛的直接把forming a record的结构照搬下来了。把后面的定语从句部分，刚好就搬到这相应的定语位置。
> 
> 很明显，第二版更像人话更好懂，但有没有一个更好的版本呢？
> 我现在来尝试一下：形成一个只有完全重做才能被篡改的记录。
>
> “由此形成一份**不重做所有工作量证明便无法修改**的记录”
> 对于这个AI给的新版，我们这两个版本其实一样，就只是对照式的翻个面而已。他这一版更遵循原文，描述的是反面。
> 而说实话，其实原文也比较拗口，你直愣愣的翻译的话，那就是：要是没有重做所有工作，那就无法被更改。




已被见证的事件及其顺序  VS  所见证事件的顺序
> 注意这里的细微差别。Witnessed，该怎么翻译？想说的很简单：这个事情已经被见证了，我们就只要看哪个翻译更好懂。
> 
> 以及第二个差别，第一版里，是证明了两个东西：事件和顺序。从连词你就能看出来，一个是【及其】，一个是【的】。那这个链，到底有没有同时做到这两点呢？
>
> 【时序证明】精确翻译了`proof of the sequence`，澄清了你提出的关于“证明事件还是顺序”的疑问——它证明的是事件的**顺序**。
> > 你看这**说的言之凿凿，但完全没理解我的问题。我的疑问是，它证明的是一个还是两个东西，而不是二选一。
> 
>
> 好了，大致明确了，说人话就是，是：【事件的顺序】，而非【事件和顺序】。
> 
> Gemini：
> 
> 核心是 `sequence`（顺序）。它证明的不是“事件A发生了”和“事件B发生了”，而是“事件A发生在事件B之前”这个**不可逆的顺序关系**。这个顺序本身，就是时间戳，就是证明。
> 
> “及其” 有歧义，它暗示了两个独立的证明目标。而AI给出的“时序证明”**，或者更直白地说**“事件的顺序证明”，是更精确的。它准确地将“事件”和“顺序”绑定为一个不可分割的整体。



not only serves as proof of the sequence of events witnessed
> 既用于证明所见证事件的顺序  VS  既是其所见证的一系列事件的时序证明
> 
> AI这里的第二版也不大好，他又用了个“是……的”的结构。在英语里叫主系表是吧？很多时候，这种都没必要，把【是】和【的】删掉后。字就是更少了，但表达起来人没什么差别。
> 
> 这个serves as，很明显有更好的翻译。虽说他那里面的【一系列】和【时序】，这样的词算比较优秀的翻译。
> 
> `serves as` 的本质是一个**功能性动词**。它不是静态的“是”，而是动态的“起到了...作用”、“担当了...的角色”。
>
> 好的翻译应该直接使用强动词：这样句子立刻就有了力量。
> *   “不仅**证明了**其见证的事件顺序”
> *   “**担当了**事件顺序的证明”





该网络给每笔交易标记时间戳，方法是：  VS  该网络通过以下方式为交易标记时间戳：
> 不看AI给的后一版，真的都不知道自己前一版有多差，这前面一版本实在太割裂。
> 你哪怕把那个逗号换成【的】都行。还是第二版好，丝滑的就顺承下来了。


an ongoing chain of hash-based proof-of-work
> 以散列为基础的工作量证明链上  VS  基于工作量证明的链中
>
> 这里AI给的第二版就不大好，没有翻译hash based这一块的意思了。可能是他潜意识认为，前面刚说了“哈希值就是被打包进这个链里的”，所以可能不需要再说明hash based的特点了。但我觉得，但多重复一句也无妨。





被良性节点控制  VS  掌握在诚实节点手里
> 整份白皮书里，有很多这种描述【节点掌控算力】的句子。
> 
> 而每到这里，我都会倾向于用【手】这样一个意象。因为你对照过来，这就是中文中常见的，而且确实更好懂。
>
> 
> Gemini：
> 
> 中文语境中一个**充满生命力和能动性**的意象。它不仅表达了“控制”，还隐含了“持有”、“运用”、“责任”等多层含义。
>
> （这里还是有点乱夸了。其实你如果能控制的话，那不就隐含了后面的那些含义吗？只是说这个意象更有代入感）
> 
> 正是从“形似”走向“神似”的绝佳范例。在描述人与系统、权力与节点的关系时，这种带有温度和意象的词汇，能让读者产生更强的代入感和理解。




并且在速度上超过攻击者  VS  攻击者追不上
> “outpace attackers”，在最开始时，我就觉得厉害，李笑来能点出“在速度上”这一点。
> 
> 像这种【out+】的词是比较难翻译的。当然可能是我太嫩了吧，pace本就指的是步伐，所以显性的指出是在哪一方面“pace out”，可能是常规操作。
> 
> 然后，两版本描述的是同一个东西。只不过第一版主语是诚实节点，第二版算是有点背离原文结构，说着说着突然偷换了主语，但很明显很就是给人一种干脆利落的感觉。




Minimal：The network itself requires minimal structure. 
> 你说，是做最小化，还是最简单的？
> 想表达的都是那个意思。什么意思呢？minimal的意思。
> 
> 所以说，都滚去看英文吧。看到这个英文词一目了然。
> 
>

“网络本身需要最简单的结构。  VS  网络自身的结构极其简单。”
>
> 后一版，当时看到AI的这个版本，我是眼前一亮。他在追求意合而非形似，对吧？
> 到底哪一种表达更好呢？
> 
> 到底要强调，要达成这个网络需要一个最简单的结构，突出这种结构是达成这个系统的需求，突出需求这个点；还是，只是想表达，这个结构很简单，想突出简单这个点呢？
>
> 
> Gemini：
> 
> 这是你提出的最深刻的一个问题：**“是‘需求’还是‘描述’？”**
>
> 我认为，**它首先是一个描述，这个描述本身就构成了一种需求。**
>
> 意思是，这个网络的设计哲学决定了它的结构必然是简单的（这是描述），而这种简单性又是它能够稳健运行、节点自由加入的前提（这是需求）。
>
> 所以，翻译的重点应该放在**描述其内在属性**上。
> 前者，侧重于“需求”。后者，侧重于“描述”。
>
> （**极其简单**）更贴近原文的本意。它在陈述一个系统固有的、令人惊叹的特性，而不是在开列一份需求清单。这种“简单”本身就是一种优势。



on a best effort basis 
> 整篇中，关于这个说明，出现过不止一次。为什么说，让我印象非常深刻呢？
> 
> 第一个就是，李笑来他这第一版里，翻译得很僵硬，完全对仗过来，说什么【以最大努力为基本】。肯定有更舒服的表达吧？
> 
> 第二个就是，我对这个东西本身很好奇。为什么要做到尽力而为的广播呢？而他又如何做到呢？尽力而为广播，但同时又无需触达每个节点，这到底是怎样的一种弹性呢？





来去自由
> 当时也讨论过了。已经说过第一版，【来去自由】这样的描述，非常好的做到了信达雅，优雅的、完好地传达出at will这种全凭意愿的感觉。
> 
> 但感觉总感觉，不够accessible，所以我们第二版就比较保守。
> 但你的顾虑是对的，它可能牺牲了一点点场景的清晰度。
>
> “节点可自由来去，重返时只需接受最长的工作量证明链，作为其离线期间所发生之一切的证明。”
> 原文的结论中有同样的句子，而我们的第二版，在结论中的翻译是这样的。那在摘要处的这一句，是不是也可以换一下了？保持一致？这一版确实更清爽。




-----
-----


## 1. 

互联网商业几乎完全依赖金融机构作为可信第三方去处理电子支付。虽然针对大多数交易来说，这个系统还算不错，但，它仍然被基于信任的模型所固有的缺陷所拖累。完全不可逆转的交易实际上并不可能，因为金融机构不能避免仲裁争议。仲裁成本增加了交易成本，进而限制了最小可能交易的规模，且干脆阻止了很多小额支付交易。除此之外，还有更大的成本：系统无法为那些不可逆的服务提供不可逆的支付。逆转的可能性，造成了对于信任的需求无所不在。商家必须提防着他们的顾客，麻烦顾客提供若非如此（如若信任）就并不必要的更多信息。一定比例的欺诈，被认为是不可避免的。这些成本和支付不确定性，虽然在人与人之间直接使用物理货币支付的时候是可以避免的；但，没有任何一个机制能在双方在其中一方不被信任的情况下通过沟通渠道进行支付。

当今的互联网商业，几乎都靠金融机构作为可信第三方来处理电子支付。这套系统在多数情况下行之有效，但其基于信任的模式存在固有缺陷。比如：交易无法彻底不可逆，因为金融机构必须调解争议。调解成本会让交易成本变高，限制最小交易规模，且干脆阻断小额支付的可能性。此外，更大的成本是：我们无法为不可逆的服务提供不可逆的支付。逆转的可能性，导致了对信任的需求无处不在。商家必须提防顾客，麻烦他们提供本不必要的更多信息。一定的欺诈也被认为是难以避免。这些成本和支付不确定性，虽然在面对面交易中可通过使用实体货币避免；但在网络上，我们却没有一种机制能在不依赖第三方的情况下进行支付。

> 加入【当今的】，
> 当然是锦上添花的说明，算是加入一个时间戳。
> 
> 同时注意almost exclusively，
> 初看有点懵，但其实就是：几乎完全。 Almost这个副词，进一步修饰那个副词。
> 
> works well
> 你看这英文里，就可以表示得如此清爽。但到咱们中文来，你又得再琢磨。
> 我记得最开始，看的一个比较土的版本是：还算管用。然后这个第一版里的：还算不错，也比较土。
> 行之有效，就显得高级的多。也能很好的囊括works well。
> 这就可以体现出中英文的差异了对吧？各语言都有其独特的美。

> 
> 然后在这里加了，【比如】。
> 我觉得OK。我甚至怀疑，是不是中本聪当时忘记加了，因为这后面本来就是在说例子。
> 
> 之后一句，
> 你就能看到，第一版是很笨拙的在照搬结构。第二版则是根据语义来进行的翻译，没遵循原文结构。
> 而同时，我觉得第二版里的词得换一下。【不能避免】和【必须】，这两者所表达的可能还是有点差别吧。
> 
> 再来看最后一段，第一版这翻译的实在是太僵硬。
> “在面对面交易中可通过使用实体货币避免”，对比之下，我们第二版实在是清爽太多了，且完全对应着原文。
> 【沟通渠道】，当时也讨论过了这个了。在这个语境下，就是网络，反倒说网络，更accessible。
> 加个主语，我们，肯定是锦上添花。
> 
> 然后这是不是出问题了，Without a trusted party，
> 第一版居然翻译做：其中一方不被信任的情况下。这一次这里，确实没有third这个词。那这一次的对象，到底指的是第三方，还是交易中的其中一方呢？



Suffers from
> 其实是比较难翻译的。第一版比较呆，就直接翻译做：被什么所拖累。
> 而第二版是没体现出来，直接把对应的中文位置上的那个词换成了，存在。不知道算不算好翻译。
> 
> 对于`suffers from`，新版本译为【受制于】，既体现了原文中“被拖累”的被动与无奈，又比“存在”一词更具张力，点明了其发展的瓶颈。



Completely non-reversible transactions are not really possible, since financial institutions cannot avoid mediating disputes
> 因为金融机构必须调解争议。  VS  因为金融机构必须介入以调解纠纷。
>
> 先不说什么语法角度，就单单是从意思角度，后面一版就更顺畅。
> 如果没有【介入】这两字，那整句就是：交易没法做到不可逆，因为金融机构要调解纠纷。
> 读者乍一看就会疑惑，这两者有什么关系呢？
> 但你用这两个字，就将前后两者连接起来，让“因为”所阐述的因果关系更明显。没法不可逆，是因为金融机构要介入交易，要来调解纠纷。
>
> Gemini：
> 这里“介入”一词，直接点明了金融机构的动作。它们“介入”交易，才有了“调解纠纷”的可能。而“调解纠纷”的动作，正是导致交易无法绝对“不可逆”的原因。



The cost of mediation increases transaction costs, limiting the minimum practical transaction size and cutting off the possibility for small casual transactions.

仲裁成本增加了交易成本，进而限制了最小可能交易的规模，且干脆阻止了很多小额支付交易。
调解成本会让交易成本变高，限制最小交易规模，且干脆阻断小额支付的可能性。

调解的成本推高了交易成本，既限制了实际可行的最小交易额度，也杜绝了小额临时交易的可能。
> 
> 注意到，对于后面的那三个影响，第一版是用了逐渐递进的方式。
> 但我仔细看了下原文，在那三个并列的影响内。后面的两个小的是非谓语词组表示出来的。
>
> 仔细一看，我们当时做出的第二版就是更差的。首先它这里是，“让成本变高”， 又把别人的动作换掉，要是再翻译回去，那应该是make it higher，但别人这里increases，真的很难翻译吗？
> 到了后面，你也没体现出递进关系，而这关系其实是很明显的。
> 
> 对于由调解成本引发的三个后果，新版本用【既...也...】的结构，清晰地表达了原文中`limiting... and cutting off...`的并列递进关系，比简单的罗列更有层次。
> 
> 而同时，为什么要翻译做临时，这是对应casual吗？
> “casual” 并不特指“临时”，但在支付语境中，它常常暗示：非正式、非计划性、即兴、一次性的支付。


“最小可行交易的规模”  VS  “实际可行的最小交易额度”
> 第三版目前最好，但还有两个我在犹豫的。
> 为什么不直接可以是“最小可行交易的规模”？为什么要翻译得那么长？
>
> **Gemini**：
> 
> “最小可行交易的规模”在字面上可以理解，也能传达部分意思，
> 但“实际可行的最小交易额度”能更精确地抓住原文中“practical”的现实限制和“size”在金融交易中特指“金额”的含义。
> 
> “额度” (amount, limit): 这个词更直接地指向了金钱的数量。原文的讨论交易成本时，最核心的限制就是可以以多少钱为单位进行交易。因此，“额度”更能直接点明这个核心限制。
> 
> “实际可行”: 指的是“在现实情况中能够操作的”。这里加上“实际”，是为了强调考虑到交易成本后，在现实经济操作中能够承受的最低金额。 
> 如果没有“实际”，仅仅是“最小可行交易的规模”，可能会让人联想到理论上可以实现，但因为成本问题实际不可行的情景。
>
> 
> 7.4
> 
> **听不懂是吧？我们已经看了三遍了是吧？**
> 
> 没关系，你只需要知道，如果你这里不加入实际两个字，会让别人想到，理论可行的情况。但这里咱们强调的，就是在实际的、现实的经济操作中。



更大的成本是：更广泛的成本在于：

我们无法为不可逆的服务提供不可逆的支付。
我们丧失了为不可逆服务提供不可逆支付的能力。
> 像这一部分，很明是它太僵硬。
> 用广泛这个词来修饰成本，不是很**吗？中文语境里谁这么说话？谁这么使用中文？
> 
> 第二处这个，无法怎么怎么样，那不就相当于是，丧失了怎样的能力吗？为什么不表达得更简单呢？算是更僵硬的贴近原文结构吧。




【我们】
> 后面一句大差不差。你看到两个版本都默契地添上了主语。是说【系统】好，还是说【我们】更好呢？后者，可能更加accessible。
> 
> **主体与视角**：
> 
> 多处采纳了【我们】作为主语，如【我们仍未有...机制】，这让原本客观、冰冷的陈述，转变为从用户和参与者视角出发的切身体会，增强文本亲和力（accessibility）。

spreads
> 第一版，在这个地方实在太厉害了，把那个spreads翻译成：无处不在。
> “将更广泛”，果不其然，你看在官网放着的中文版本，都是这样的平庸翻译。
> 还是第一版好，以至于我们的第二版都是从他那借过来的。
>
> 它传神地描绘出信任需求弥漫开来的状态，极富表现力。


hassling them for more information than they would otherwise need
> 
> 其实难翻译。我觉得很考验功力。
> 首先那个动词，最对应的确实就是麻烦，“不好意思麻烦你了”里面的麻烦。
> 
> 还有otherwise，其实我一直没搞懂，放在这里是干嘛。
> 并不知道怎么翻译。第一版看着太别扭，第二版又感觉少点啥，虽然可能更清爽。总之想表达的，其实就只是：除非信任，否则总是会要求提供额外信息。
> 
>
> 7.4
>
> 难理解的话，你就这么想。
> otherwise本来就是，否则。指代的本就是另一种情况，下面Gemini已经给你说好了。那than，比较的就是两种情况下的不同。那你直接把这个otherwise套成if things were different的一个条件从句就好了。
> 
>
> Gemini
> 这是最考验功力的地方。新版本译为【本不必要的额外信息】，这里的【本不必要】精准地暗含了`otherwise`的语境——“如果情况不同（即，如果存在信任），这些信息本是不需要的”。这比直译更优雅，比省略更完整。
> 
> hassling：“麻烦”是绝佳的对应词，传达了“增加额外负担和烦扰”的感觉。
> 
> otherwise: 是关键。它的意思是 “if things were different”。在什么不同情况下？在一个没有交易逆转可能性的、无需信任的系统下。
> 所以整句话的意思是：商家不得不麻烦顾客提供更多信息，而这些信息在（理想的）另一种系统下是本来就不需要的。
> 
> 第一版：“若非如此就并不必要” -> 语法绕，非常生硬。
> 第二版：“提供本不必要的更多信息” -> 完美。
> 
> 用“本不必要”四个字就干净利落地处理了“otherwise”这个词所蕴含的复杂对比关系，清晰、地道、准确。



逆转的可能性，导致了对信任的需求无处不在。
由于逆转始终可能，对信任的需求也因此无处不在。

一定的欺诈也被认为是难以避免。
一定比例的欺诈，也被当作无法避免的代价。
> 
> 这三句值得来说说的，所有的第二句都是给到的新一版，而我觉得都是更好的表达。
> 
> 原文中确实是possibility，新一版就翻译成了更像人话的中文。可能性这个词，本就更抽象。
> 
> 第二句这，点出了【代价】，算锦上添花。原文中虽没有，但是他用这两个字就更强调了，为了使用这个系统而不得不付出，的这么个意思。



但在网络上，我们却没有一种机制能在不依赖第三方的情况下进行支付。
但在网络上，我们仍未有一种无需可信方参与，就能完成支付的机制。
> 
> 最后一句，把对这个理想机制的情况描述，放到了定语位置，然后用“的”连起来。
> 而原句更像是，中式定语从句。前面是【机制】，后面是一坨对机制进行修饰的话。不知道哪个更顺口，虽说意思是一样的，这里我们直接选取了那个字更短的。
>
> 
> Gemini，关于结构：
> 
> 原文英文结构：...a mechanism to make payments... without a trusted party. 这是一个名词（mechanism）后接不定式短语和介词短语来描述其功能和特性。
> 
> 旧版本结构：...一种机制 + 能在...的情况下...进行支付。这像是一个中文的偏正结构，但修饰语“能在...支付”比较长且包含状语从句，有时会显得有点冗长。
> 
> 新版本结构：...一种 无需可信方参与，就能完成支付 的机制。这是一个非常经典的中文“定语+的+中心词”结构。
> 
> 把描述性内容“无需……完成支付”作为一个长定语放在“的”前面，修饰名词“机制”。这种结构在中文中常见且流畅，尤其是描述某种“具备某种特性的”事物时。
> 确实采用了更紧凑和更符合中文习惯的定语结构，并且字数更短，读起来更顺畅。



“却有没有” vs “仍未有一种”
> “仍未有”更贴近原文“no mechanism exists”的含义，强调了这种机制至今还没有出现。
> 而“却没有”则更偏向于表达一种转折或出乎意料。



---


What is needed is an electronic payment system based on cryptographic proof instead of trust, allowing any two willing parties to transact directly with each other without the need for a trusted third party. Transactions that are computationally impractical to reverse would protect sellers from fraud, and routine escrow mechanisms could easily be implemented to protect buyers. In this paper, we propose a solution to the double-spending problem using a peer-to-peer distributed timestamp server to generate computational proof of the chronological order of transactions. The system is secure as long as honest nodes collectively control more CPU power than any cooperating group of attacker nodes.

我们真正需要的是一种基于加密证明而非基于信任的电子支付系统，允许任意双方在不需要信任第三方的情况下直接交易。算力保障的不可逆转交易能帮助卖家不被欺诈，而保护买家的日常担保机制也很容易实现。在本论文中，我们将提出一种针对双重支出的解决方案，使用点对点的、分布式的时间戳服务器去生成基于算力的证明，按照时间顺序记录每条交易。此系统是安全的，只要诚实节点总体上相对于相互合作的攻击者掌握更多的 CPU 算力。

我们真正需要的，是一个基于加密证明、而非基于信任的电子支付系统，允许任意两方直接交易，无需可信第三方。通过让交易在计算上难以撤销来保护卖家免受欺诈，同时通过常规的托管机制来保护买家。本文中，我们提出一个针对双重支付问题的方案：利用一个点对点的、分布式的时间戳服务器，为交易的时间顺序生成计算证明。只要诚实节点总体上控制的 CPU 算力超过任何协同攻击者节点，该系统就是安全的。


> 第一句，还是我们的特有习惯，遵循：尽量能断就断，通过加这加那的符号，让信息密度更舒缓。
> 
> 第二句，其实像第一版的这种，在什么什么的情况下，已经算是比较好的翻译形式，但我还是想拆出来，但要不要加个【而】呢？
>
> 
> 接下来这一句，两个版本都不大好，
> 第一版，非常遵循原文，整个结构都是搬下来的。这个版本里，原文中的定语从句中的内容，被他非常完好的放在主语前面。甚至从头到尾，第一版本里、笑来的版本从头到尾都这样子。他都是更加遵循原作者，原文的语序。
> 第二版的问题在哪里？完全拆掉了。他是把结构拆掉，从语义传输的角度出，优先想着把意思说清楚，所以就没有遵循原文结构。
> 
> computationally，第一版翻译做，算力保障的。而我们第二版，还是依据“+ly”类型的传统翻译，就是什么什么方面，那就是计算上的。
>
> 
> 至于【不可逆转  VS  难以撤销】的程度描述差别。
> 也不太好说，原文中是impractical。那第二版，可能就更加遵循它的意思。确实也没人撤销吧？我记得好像是难度是2的256次方的。没人干这蠢事吧？
> 
> 而这一句的后半段，你也能看到，依然非常遵循原文，“很容易实现”。
> 第一版，就强调容易实现。而第二版，更强调这个机制本身，突出了另一个点。算是跟第二版的前一句形成了对照。
> 你说，到底该翻译作日常，还是常规；担保，还是托管呢？咱也不知道，对这个东西我本身不太熟。
>
> 
> 再来看computational proof，
> 第一版里，翻译的是，基于算力的证明。为什么要这么做？
> 而我们，为什么在当时在第二版里翻译成，计算证明？
> 
> 
> 以及又到了这一段，当时我纠结了很久的地方，of the chronological order of transactions。
> 注意，第一版单独拆了一部分出来，按照时间顺序记录每条交易。他罕见的没按照原文意思来。你这是不是额外解释？其实这一段。我不大理解。当然，对于。我只是对于这个工作原理本身肯定是读了很多遍了，是没问题的。
> 只是说在这个翻译这一方面，我不知道这一坨要怎么解释。
> 
> 
> 最后一句，当然是先把条件前置。第一版太怪了。条件前置才是中文常见形式。条件前置，再说结论，符合用户预期。
> 然后，第二版还是牺牲了对原文结构的忠诚，原文那个动词是control。但到我们第二版的翻译里来，动词就变成了超过。
> 那有没有遵循原文结构，但同时比第一版表达的更清爽的版本呢？我现在来试一下：只要诚实节点总体上比协同的攻击者掌握更多的CPU算力。
>
> 
> collectively，怎么翻译。我觉得，协同，是更好的版本。相互合作是不是太冗余。
> 7.3，这完全是当时看错了。这个词，是用来修饰诚实节点总体上控制的算力。后面那个攻击节点，有自己相应的修饰。而无论是协同又或是相互合作，那都是对应着原文中的cooperating。




Transactions that are computationally impractical to reverse would protect sellers from fraud, and routine escrow mechanisms could easily be implemented to protect buyers.

* 算力保障的不可逆转交易能帮助卖家不被欺诈，而保护买家的日常担保机制也很容易实现。
* 通过让交易在计算上难以撤销来保护卖家免受欺诈，同时通过常规的托管机制来保护买家。
* 其一，在计算上难以撤销的交易可以保护卖家免受欺诈；其二，常规的托管机制也能轻松建立以保护买家。

> 巧妙地拆分为【其一...其二...】的并列结构。这既保持了信息的独立性，又清晰地展现了原文中保护卖方和买方的两个平行手段，避免了长定语或状语从句带来的臃肿感。
> 【常规】对应`routine`，比“日常”更书面；【托管】是对`escrow`最准确的金融术语翻译，比“担保”更精确。
>
> 7.3
> 
> 原版本实际上有些背离原文结构，而明显能做到不偏离结构、但同样也表达清晰。像新版就做到了。
> 而你这一句，要是再翻译回去，那应该更像是：protecting sellers from fraud by make transactions computationally impractical to reverse.



a solution to the double-spending problem
> “一个解决双重支付问题的方案”，李笑来的版本里是，针对。但既然这是个solution，然后又是to，那说成解决，也没问题。




对动词和状语做了精炼：【诚实节点们共同控制的CPU算力】，准确翻译了`collectively control`；而【协同攻击的节点群组】则精准地对应`cooperating group of attacker nodes`，【协同】一词比“相互合作”更凝练有力。
> 
> 虽然我知道，这个世界上很多人做的表达，都是自我论证，自卖自夸。
> 但像这个就比较**，算是没依据、不够客观的。
> 共同控制的，翻译的更僵硬，为什么不说，总体上呢？




只要诚实节点们总体上控制的 CPU 算力超过任何协同攻击者节点，该系统就是安全的。

Gemini：只要诚实节点们共同控制的CPU算力，超过任何协同攻击的节点群组，该系统就是安全的。

只要诚实节点们总体上比协同的攻击者掌握更多的CPU算力，该系统就是安全的。
> 
> 倾向于第三个。因为他做到了在不背离原文结构的情况下，同时表达得足够清晰。
> 考虑到，原文的关键动作是control more，而不是“超过”。
> 同时，collectively不用翻译得如此僵硬。
> 
> 至于对攻击者的描述，【节点和群组】，无需再显性表述出来。两方阵营的对峙，已经很清楚。
>
> 
> 客观且深刻。
> 
> 1.  **结构对位**：第三版的「A 比 B 掌握更多 C」结构，完美对位了原文的 `A control more C than B`。它将比较的动作（control）和比较的程度（more）清晰呈现。
> 前两版本的「A 的 C 超过 B」结构，虽意思正确，但改变了原文的句式焦点，从一个动态的“掌握”变成了静态的“超过”。
> 
> 2.  **词语选择**：`掌握`比`控制`更生动，更符合中文语境中描述算力这种“资源”的用法。`总体上`比`共同`更自然流畅，`共同`略显生硬。
> 3.  **信息提纯**：第三版大胆省略了这些冗余信息，直击“诚实方 vs 攻击方”核心对抗，语言更精炼有力。




-----
-----


## 2. 

We define an electronic coin as a chain of digital signatures. Each owner transfers the coin to the next by digitally signing a hash of the previous transaction and the public key of the next owner and adding these to the end of the coin. A payee can verify the signatures to verify the chain of ownership.

我们将一枚电子硬币定义为一个数字签名链。一位所有者将一枚硬币交给另一个人的时候，要通过在这个数字签名链的末尾附加上以下数字签名：上一笔交易的哈希（hash，音译，亦翻译为“散列值”），以及新所有者的公钥。收款人可以通过验证签名去验证数字签名链的所属权。

我们把一枚电子硬币定义为一个数字签名链。每个所有者转交币时，要通过在这个链的末尾添加以下的数字签名：前一笔交易的哈希值（hash，音译，亦翻译为“散列值”）和下一个持有者的公钥。收款人可以通过验证签名来验证数字签名链的归属。


> 这一段，都是些非常微小的差别。
> 
> 第二句话，算是第一版的老毛病，他每次都是这样僵硬翻译过来的。一旦原文中有这样的转交动作，它都是翻译得如此僵硬，但很明显有更清爽简洁的说法。
> 没必要说是：一个人转给另一个人。还能转给谁？这个情景下，不都只能是用户嘛。所以可以直接说：转交时。
> 
> 然后注意，在这里，又是那个典型特定句式，先说要干个啥，然后再说这东西的具体内容是啥。
> 还是像我们之前所讨论过的，第一版，也就是李笑来那一版，它在整篇翻译中有很多这样的句式结构，有时候好用，比如说在这里。
> 否则，如果把它放在前面的定语位置，然后用一个“的”字连起来，就显得太臃肿了；
> 但有时候，很明显不用这样拆，可以直接合起来。
>
> 说实话，这个也得怪一下别人原作者，总是写这种长句子，一坨子内容全部打一个句子里，你哪怕用从句拆出来都更好，看起来更顺眼。
> 当然，看久了也就习惯了吧。估计之后要研究的东西里，应该常有这样的长句。也算是磨练。
> 
> 其他的都是些无伤大雅的小区别。
> 
> 还记得6.13，自己当时翻译到这一段，是通过李笑来的第一版有所感悟。
> 比如说，他在这里对哈希的解释，是在第二段才出现的，但在摘要里面，就已经出现了hash这个词。
> 为什么呢？【摘要里面，通常不放解释】，这是我的观察和推测。
> 可能这是这种正经文章的规矩吗？仔细回顾一下，你看的那些正经东西里，也没有人在摘要里面做解释。那可能就是在第二次出现时，再来稍做解释。



We define an electronic coin as a chain of digital signatures. 
> 我们将一枚电子硬币定义为一条数字签名链。
> 把这个翻译再稍微延伸扩展一下。
> 
> “我们将一枚电子硬币定义为一条由数字签名构成的链。”
> 算锦上添花，还是画蛇添足？还有没有更好的版本？




每个所有者转交币时，要通过  VS  转交时，当前所有者会对
> 第一版还是更清晰。首先是，更遵循原文，其次，把转交也说得更清楚。
> 我当然知道第二版的道理。既然你在此时能转交，那就说明你是这个币的当前所有者。



要通过在这个链的末尾添加以下的数字签名：前一笔交易的哈希和下一个持有者的公钥。
当前所有者会对**上一笔交易的哈希**与**下一位所有者的公钥**进行数字签名，然后将这些数据附加到电子币的末尾。
>  `signing ... and adding these` 的结构，在旧译本中都被简化了，技术描述不完全精确。新版本明确了核心动作是【进行数字签名】，签名后，将【这些数据】（包含哈希、公钥以及签名本身）附加到末尾。
> 
> 
> **第一版（混淆）：** “添加以下的数字签名”，听起来像是“签名”这个东西包含了“哈希”和“公钥”。
> **第二版（精确）：** 先对“哈希+公钥”进行签名，**然后**将（包含签名在内的）这些数据附加到链上。这是两个独立动作：1. 创造证据（签名）；2. 记录证据（附加）。第二版准确地反映了这一时序和逻辑。



收款人即可通过检验这一系列签名，来【核实其所有权链】。
收款人可以通过验证签名来验证【数字签名链的归属】。
收款人可以通过检验签名来核实【所有权的归属链条】。
> 第一个版本中的其，代表什么？
>
> 
> 7.3
> 而这个链本身就是一条所有权链，对吧？
> 
> 意思就是，现在最上面写的是谁名字，这个链，也就是这个币，就是谁的，对吧？
> 更准确地说，是“链条最终指向的那个地址，就拥有这个币的所有权”。
> 
> 这个币本身，就是一条你写完之后、就下一个收款方来写的链，对吧？
> 像接力棒，每一次传递（交易）都留下一个“签名”作为证据，而这个证据的集合，就构成了这条所有权链。收款人就是通过查看这条完整的接力记录，来确认自己是否是合法的下一棒接力者。


好笑，为什么读不懂【所有权的归属链条】？
> 因为这个翻译版本太SB了啊、是错的啊。
> 
> 因为语义重复。“所有权”和“归属”基本是同义词。
> 这句话相当于说“ownership's belonging chain”，既啰嗦又别扭，所以你的语感是正确的。


```
关于【所有权链】“Chain of ownership”

是否准确？
本质，就是一条由历任所有者构成的、可追溯的链条。一系列证明所有权转移的历史记录形成的链条。

每一个数字资产（比如比特币）的流通历史，就是一条所有权链。 链条上的每一个环节，都记录了“是谁把这个东西给了谁”，并由签名来证明。

为什么感觉怪？
因为它是一个技术术语，日常口语不说。就像“封装”“继承”一样，在特定语境下才有精确含义。


“数字签名链的归属”：
侧重于“数字签名”本身，而不是“所有权”本身。虽然签名是用来证明所有权的，但原文强调的是所有权这个概念。而且“归属”也略有偏差，更像是“谁拥有这个签名链”，而不是“这个签名链指向的所有权归属”。

“其”：
指代的“收款人自己”。语境中，收款人要核实的是“（这笔交易以及它所代表的币）的所有权链条，并最终确认这个所有权是否已经合法地转移到了自己这里”。
```




---



The problem of course is the payee can't verify that one of the owners did not double-spend the coin. A common solution is to introduce a trusted central authority, or mint, that checks every transaction for double spending. After each transaction, the coin must be returned to the mint to issue a new coin, and only coins issued directly from the mint are trusted not to be double-spent. The problem with this solution is that the fate of the entire money system depends on the company running the mint, with every transaction having to go through them, just like a bank.

这个路径的问题在于收款人无法验证曾经的所有者之中没有人双重支付过。常见的解决方案是引入一个可信的中心化权威方，或称“铸币厂”，让它去检查每一笔交易是否存在双重支付。每一次发生交易之后，硬币必须返回到铸币厂，铸币厂再发行一枚新的硬币。进而，只有铸币厂直接发行的硬币才是可信的、未被双重支付过的。这个解决方案的问题在于，整个货币系统的命运被拴在运营铸币厂的那个公司（就好像银行那样）身上，每一笔交易必须通过它。

问题在于，收款人无法验证之前的所有者中，有没有人“一币多花”。常见做法是引入一个可信的中心化机构，或"铸币厂"，由它检查每一笔交易是否重复。每次交易后，硬币必须回到铸币厂重新发行。进而，只有铸币厂直接发行的硬币才是可信的、未被双重支付过的。但这样一来，整个货币系统的命运取决于运营铸币厂的公司，每笔交易都必须经过它们，就像银行一样。


> 当时也挣扎得比较久吧，能很明显的看到，整体上而言，我们的第二版就是更好。信息密度更舒缓，更accessible。
> 
> 首先，of course，我在想有没有必要体现出来，可以稍微加一下。
> 
> 在这里打个引号，说“一币多花”，我觉得合理。更清晰形象地表达出来了。
> 
> 这个，做法，可能要换成【解法】，更加显性的体现出来，我们是针对这个问题去想方法。
> 
> transaction for double spending，有没有必要再来翻译成，双重支付呢？第二个版本里的，【是否重复】，是否是更清爽的答案呢？
> 
> 之后的那一句，我觉得整体而言就是第二版更好。不仅字更少，确实也更好理解。
> 
> “这个解决方案的问题在于”，第一版确实非常忠于原文，但很僵硬。第二版本呢，就更丝滑。
> 
> 最后一句里，第一版本他居然把depends on翻译成：拴在身上。
> 
> 
> just like a bank的补充说明。
> 第二版更好，信息密度就更低。你也不用纠结这个【像银行一样】，究竟是要修饰这个公司呢？还是修饰每笔交易就必须要经过他们？是相通的。因为这是银行的共有特性。
> 就是说，你是这样的公司，那么你就有【每笔交易都得流经你们】的这样的特性。
> 所以把这一句just like a bank的修饰靠谁近一点，是没关系的。


之前的所有者中，有没有人  VS  之前的某位所有者没有
> “one of the owners”，像之前那个版本就比较呆板，是完全把把of这个结构拆开来，先说of后面的所有的，再说of前面的one。但像之后一版就更水润，把整一个连起来说的。
> 关于这个验证，有是和否两种情况。其实你说，你无法验证他没这么做，和，你无法验证它是否这么做了。这两个表达的，是同一个东西。因为心中期待的情况就是【是和否】的其中一个，只是前者说明了要的是哪个。
>
> 当然，“did not sign”，原文如此，无需纠结。


【中央机构（或称“铸币厂”）】
> 注意到了吗？他第一个版本是，或称。为什么中心化机构和铸币厂，这两个东西可以互换呢？他们真的只是称谓上的不同？还是说，是完全不同的东西？原文中只是or。
>
> 7.3，这只是用另外一个更形象的词汇来帮助理解，不是两个完全不同的东西。过去的中心机构不就是mint？现在高级点了，那不还是印钞的银行吗？
> 
> 关系的澄清：中央机构和铸币厂，在这里是功能等价，而非名称等价。新版本用括号加“或称”来处理，清晰地表明了：“铸币厂”是此类中央机构的一个形象称呼，解决了你的疑惑。



must be returned to the mint to issue a new coin
> 必须回到铸币厂重新发行。  VS  都必须交还铸币厂以换取新币。
> 
> 哪个更好？
> 前者，算是多解释了一层？因为换取新币，不就是为了重新发行？
>
> 我最后一个问句应该不算是引导，意思就是说，没有刻意地把他引向我想要的答案，然后我俩又开始走偏。 
> 我觉得更多的是，本就如此。你把币交还，然后来换取新币。这个流程的目的，不就是重新发行吗？
> 
> 
> Gemini
> 版本一更直接，强调的是“重新发行”这一动作和目的。更偏向流程的最终结果。
> 版本二更侧重于“交还”和“换取”这个过程，明确了交换的“新币”是重点。更贴近“issue a new coin”的实际操作感
> 
> 如何各取所长：
> “硬币在每次交易后必须交还铸币厂，以便（由铸币厂）重新铸造并发行新的硬币。”
> 这个版本保留了“交还”和“换取新币”的含义，并明确了“重新发行”是核心目的。


are trusted not to be double-spent.
> 才是可信的、未被双重支付过的。  VS  才被认为是可信的、没有被双重支付的。
>
> “被认为是”，加上这个，才是更清晰的版本。因为后面的这两个修饰词，本来就是人类主观动作。Trust本就是人类主观动作。



进而，我们需要一个系统，使参与者们能够就交易的接收顺序，达成统一的历史共识。收款人需要证明，在每笔交易发生时，大多数节点都认同这笔交易是第一个被收到的。
> 7.3
> “这个翻译的应该已经很清晰了吧。不需要再吹毛求疵了吧？
> 可为什么我还是不懂？
> 是因为直接啃白皮书的文字是更抽象的理解方式，是吗？
> 能再给我讲解一遍吗？以更加accessible Understandable vivid的简洁方式。
> 
> （比如：为什么是卖方需要证明？证明之后有什么用？为什么要证明是第一个收到的？
> 意思就是说，他既然想收钱，那就得向大伙证明，他这笔交易不是double spending类型？）”
> 
>
> 聊着聊着就对这句话，理解更深了。如果再说的话，那就又讲到比特币的本质了。
> 为什么是卖方需要证明呢？因为你想收这笔钱。证明了之后，有什么用呢？这笔交易就被正确记录，支付系统就正常运转。对卖家来说，他就能安稳收这笔钱。
> 因为只有大家都认，这笔钱你是第一个收的，只有大家都认这个账，你这个钱才valid，不然大家不认。
> 那为什么说，得是第一个收到的呢？一旦你这个“第一个”确定下来后，那大家就【赶紧地】只认你这个了。这就避免了双花。
> 方法是什么呢？那就是让大多数节点认同。具体怎么搞呢？那就是后面提到的一系列工作机制了，时间戳服务器等等之类的。
>
> “继续保持这种深入思考和简洁的表达，你对这些复杂概念的理解会越来越透彻！”


```
数字货币的世界里，交易就像集市上的买卖。因为没有实体，大家看不见谁先谁后，很容易打架（发生纠纷）。所以，我们需要一个“大家一起记账”的系统。这个系统让所有“记账员”（节点）都看着交易。当一笔交易出现时，大家都在记，并且会看谁先“记下”这笔交易。
然后，那个卖出东西（收款人）需要拿出“大家一起记账的记录”来证明：在那个交易发生的时候，不是他一个人觉得这笔交易是第一个，而是“大部分记账员”都看到了，并且都认同，这笔交易是当时“第一个被大家看到并记下”的。
```




---

We need a way for the payee to know that the previous owners did not sign any earlier transactions. For our purposes, the earliest transaction is the one that counts, so we don't care about later attempts to double-spend. The only way to confirm the absence of a transaction is to be aware of all transactions. In the mint based model, the mint was aware of all transactions and decided which arrived first. To accomplish this without a trusted party, transactions must be publicly announced[^1], and we need a system for participants to agree on a single history of the order in which they were received. The payee needs proof that at the time of each transaction, the majority of nodes agreed it was the first received.

我们需要一种方式，可以让收款人确认之前的所有者并没有在任何之前的交易上签名。就我们的目的而言，只有最早的交易是算数的，所以，我们并不关心其后的双重支付企图。确认一笔交易不存在的唯一方法是获悉所有的交易。在铸币厂模型之中，铸币厂已然知悉所有的交易，并且能够确认这些交易的顺序。为了能在没有“被信任的一方”参与的情况下完成以上任务，交易记录必须被公开宣布[^1]，进而我们需要一个系统能让参与者们认同它们所接收到的同一个唯一的交易历史。收款人需要证明在每笔交易发生之时，大多数节点能够认同它是第一个被接收的。

我们需要一种方法，能让收款人确认之前的所有者没有在任何更早的交易上签过名。对我们来说，最早的那笔交易才算数，所以，我们不在乎后续的双重支付尝试。要确认一笔交易不存在，唯一办法是获悉所有的交易。在铸币厂模式下，铸币厂已然知悉所有的交易，并能决定他们的顺序。为了在没有可信第三方的情况下做到这一点，交易必须被公开宣布[^1]。进而，我们需要一个系统，能让参与者们一致认同他们接收到的唯一交易历史。收款人需要证明，在每笔交易发生时，大多数节点都认同它是第一个收到的。

> 第一句，大家都是小差异，这无伤大雅。
> 
> 到第二句开头，开始不一样。【对我们来说】，这种翻译可能更清爽直白。第一板僵硬，但直接。


Attempts，翻译做企图，还是尝试呢？
> 都可以，因为你既然会有这样的尝试，那不就说明你有相应的企图吗？
> 他想表达的就是：随你胡搞乱搞，我们只看第一笔。
>
> 将【attempts】译为【尝试】，而非【企图】，避免了不必要的动机揣测，保持了技术文档的中立性。


> 第三句，那还是遵循我们的原则，能断句就断句。就尽量让信息密度更舒缓更易读。
> 同时，当时我们已经讨论过，这里的【获悉】，是非常棒的翻译，比【知道】强很多。
> 同时，【已然获悉】也很棒。非常完美的描绘出在旧模式下，这个中央机构的那种昂然傲立，权力无边的态势。





“and we need a system for participants to agree on a single history of the order in which they were received”
> 那一段描述是用to连起来的。而在我们的翻译中，不知道放在哪里合适。2版本里，都是被摆在后面做状语，我不知道第二版本这样的断句够不够合理。是不是应该加一个代词，它？
>
> agree on a single history
> 认同交易历史  VS  对……达成历史共识
> 最终版好太多了，或者应该说之前的版本力度都不够。这个系统的作用，就是让参与者们能认同这个交易历史吗？我知道，这两个表达的是一个意思，但你说成，就这个东西达成共识，就是更有力道的表达。
> 
> 
> 进而，我们需要一个系统，能让参与者们对交易的接收顺序，达成一个单一、统一的历史共识。
> 进而我们需要一个系统能让参与者们认同它们所接收到的同一个唯一的交易历史。
> 
> 这里的接收为什么不一样了？前一句的接收，是修饰在顺序；后一句的接收，是修饰“这个历史交易被参与者们接收”。

```
**of the order in which [transactions] were received**.

关键点是「交易被接收的顺序」需要形成一个**统一的历史共识**。

* 第一句翻译准确保留了这个结构：**“对交易的接收顺序达成共识”**，语义紧扣原文。
结构清晰，“系统 → 让参与者对某个对象（交易的接收顺序） → 达成共识”，逻辑严谨。

* 第二句则改写成：**“认同它们所接收到的同一个唯一的交易历史”**，从“顺序”变成了“整个历史”，
这会让人误解为：只要交易内容一致就行，而非关注**顺序**。模糊了“共识的对象”，句式略绕，容易引起歧义。

第一句的“接收”准确修饰的是“顺序” —— 即“交易被接收的顺序”。
第二句的“接收”主语换成了“参与者”，语义发生偏移：仿佛是参与者分别接收了交易，然后统一认同一个历史，这不符合“全网对顺序达成共识”的意图。
```




“The payee needs proof that”
> 宾语是proof，但这两个怎么都在里面【证明】的动词呢？两个版本是不是都搞错了？
> “收款人需要证据来表明”，如果硬是把它当名词来用，需要说成这样的话，那我们还是更简化，没必要画蛇添足了。


> 而这里，我觉得很明显有指代不明的毛病。这个【它】，到底指的是收款人，还是每笔交易，还是大多数节点呢？这一句里，可是有三个主体。
> 原文也就是这么写的，但我觉得翻译过来，你肯定得指明清楚吧。总之我现在作为读者是无法理解这一点的。


