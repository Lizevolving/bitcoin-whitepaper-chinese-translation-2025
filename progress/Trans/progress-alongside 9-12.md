# 琢磨钻研：9. 价值的组合与分割 (Combining and Splitting Value)   -  12. 结论 (Conclusion)

-----

## 9.

Although it would be possible to handle coins individually, it would be unwieldy to make a separate transaction for every cent in a transfer. To allow value to be split and combined, transactions contain multiple inputs and outputs. Normally there will be either a single input from a larger previous transaction or multiple inputs combining smaller amounts, and at most two outputs: one for the payment, and one returning the change, if any, back to the sender.

尽管逐个地处理硬币是可能的，但为每分钱设置一个单独的记录是很笨拙的。为了允许价值的分割与合并，交易记录包含多个输入和输出。一般情况下，要么是一个单独的来自于一个相对大的之前的交易的输入，要么是很多个输入来自于更小金额的组合；与此同时，最多有两个输出：一个是支付（指向收款方），如果必要的话，另外一个是找零（指向发款方）。

单独处理每一分钱既不现实也效率低下。因此，为了让价值能够自由地组合与拆分，每笔交易都支持包含多个输入和多个输出。通常，一笔交易的输入要么来自一笔更大的历史交易，要么是几笔较小金额的合并；而其输出最多有两个：一笔用于支付，另一笔是找零（如有）退还给付款方。


> 一个版本，很明显的翻译腔，而第二版，直接把条件从句砍了。所以我当时是，各取其优，造出了这个版本，“尽管可以逐个地处理硬币，但为每分钱设置单独的记录，既不现实也效率低下”。我也不知道这个形容词，unwieldy，到底有没有表达这么丰富的意思？
> Allow value，其实没什么问题的，但如果翻译成中文，还说“允许价值的怎么怎么”，特别别扭。这里的，让，是更好的。
> 同时，选用组合与拆分，我觉得，是比合并与分割，更加适合价值这个抽象词。
> 后面一句，第一个版本完全没法读，确实是非常尊重原文结构。
>  If any，最好处理方式就是，“（如有）”。否则你放到外面来说，更低效。
> 第一个版本，括号内额外说明，不知道是否需要保留。我这样写，“一笔用于支付（指向收款方），另一笔用于找零（如有），即退还给付款方。”，主要是因为它第二句的如有，这已经有括号了。如果那个“指向付款方”还这么说的话，那就是两个括号，感觉不太行。


> “被设计为”，OK的，虽说原文只有contain。



It should be noted that fan-out, where a transaction depends on several transactions, and those transactions depend on many more, is not a problem here. There is never the need to extract a complete standalone copy of a transaction's history.

值得注意的是，“扇出”在这里并不是问题 —— 所谓“扇出”，就是指一笔交易依赖于数笔交易，且这些交易又依赖于更多笔交易。从来就没有必要去提取任何一笔交易的完整独立的历史拷贝。

需要指出的是，一笔交易依赖于多笔上游交易，而这些上游交易又依赖于更多交易的“扇出”效应，在这里不成问题。因为系统在任何时候都无需去追溯一笔交易的完整历史记录。


> “值得注意的是，“扇出”效应（一笔交易依赖于多笔上游交易，而这些上游交易又依赖于更多交易），在这里不成问题……”
> 当时各取其优，做出这一版本，把解释放在括号里可能更好，第一版就太冗长，第二版就直接丢到形容词位置。我觉得都不够清晰。加符号，可能会让信息密度更舒缓。
> 上游，这个特定说法，一点问题没有。虽然，原文中没有表达这含义，但这词一定会辅助理解。
> 最后一句，也很明显看出第一版的翻译腔。
> 第二个版，加了因果连接，还带上主语。Extract，直接翻译成提取，肯定不行。追溯，很明显是更合语境。总之，对于最后一句，第二版本完胜。

> “从不需要 VS 在任何时候都无需”，后者更好，从不，更侧重之前。“从来都无需”，这个可能更好？
> “为任何交易”，很明显比“一笔交易的、”更好，转成客体说明。后者还放在形容词位置挤着，虽说这样就是更符合原文。
> 
> “追溯”很好，但“提取...副本”更忠实于 `extract a...copy` 的计算机操作语境。


-----
-----


## 10.

The traditional banking model achieves a level of privacy by limiting access to information to the parties involved and the trusted third party. The necessity to announce all transactions publicly precludes this method, but privacy can still be maintained by breaking the flow of information in another place: by keeping public keys anonymous. The public can see that someone is sending an amount to someone else, but without information linking the transaction to anyone. This is similar to the level of information released by stock exchanges, where the time and size of individual trades, the "tape", is made public, but without telling who the parties were.

传统的银行模型通过限制他人获取交易者和可信第三方的信息而达成一定程度的隐私保护。出于对将所有交易记录公开的需求否决了这种方法。但是，维持隐私可通过于另一处的切断信息流来实现——公钥匿名。
公众可以看到某某向某某转账了一定的金额，但是，没有任何信息指向某个确定的人。这种水平的信息发布有点像股市交易，只有时间和各个交易的金额被公布，但是，没有人知道交易双方都是谁。

传统银行通过将信息限制在交易方和第三方机构内部来保护隐私。由于我们的系统要求所有交易公开，这种方法不再适用。但隐私依然可以得到保障，诀窍在于从另一个环节切断信息流：保持公钥的匿名性。
公众能看到有人向另一人转了一笔钱，但无法将这笔交易与任何人的真实身份关联起来。这类似于证券交易所的做法：交易的时间和数额是公开的，但交易双方的身份是保密的。


> 皱巴巴挤一坨，看着人烦。所以我总是有一种倾向，能打括号和引号就尽量。比如这里，我给的版本就直接是把主语跟后面的隔开了，“传统的银行模型，……”
> 第二版少了很多，但确实你如果要说全的话，那就是，“达成一定程度的隐私保护”，这就太冗余。
> 
> 总体而言，第一版更好。他说了是“限制谁获取谁的信息”，主体客体，说清楚了，而第二版很别扭。他说，“把信息限制在哪”。读者不知所云，为什么要限制在这呢？虽说原文中未说明到底是limiting谁的access，但点出来，就是更易读。
> 
> “但隐私保障可通过从另一个环节切断信息流来实现：保持公钥的匿名性”，我觉得，我的这一版比上两个都更好。像第二版的什么“诀窍”，又引入了新变量。第一版，他把“切断信息流”，作为一个整体名词发现了吗？总之更别扭。
> “breaking the flow of information”，这不是动词短语吗？笑来这里翻译得也不当啊？
> 
> 第一版，很明显还是忠于原文，第二版就更情景化。信息，具体指的就是这笔交易，然后，某个确定的人，然后说的更具体，就是说，任何人的真实身份。
> Stock exchanges，我觉得，没必要再引入什么“证券交易所”这样的新变量。第一版的股市交易就挺好的。
> 
> 最后一句，原文里the tape，他是想干嘛？为什么这两个版本的翻译都没管，是一个类似于“or said”的另外说明吗？
> 最后一句，“保密”，肯定是更好的。那不就是更高效地表达出意思了吗？得其意忘其形。


> “made public”, 向公众披露，有必要这么说？但“是公开的”，确实可以再优化。
> 
>“与任何人的真实身份关联起来”，关联起来，不如“对应”那么有力。“挂钩”，很好，但不适合书面。
>
> “来实现一定程度的隐私”，确实忠于原文，但也实在愚蠢。





As an additional firewall, a new key pair should be used for each transaction to keep them from being linked to a common owner. Some linking is still unavoidable with multi-input transactions, which necessarily reveal that their inputs were owned by the same owner. The risk is that if the owner of a key is revealed, linking could reveal other transactions that belonged to the same owner.


还有另外一层防火墙。交易者应该针对每一笔交易启用一对新的公私钥，以便他人无法将这些交易追溯到同一个所有者身上。有些多输入的交易依然难免被追溯，因为那些输入必然会被识别出来自于同一个所有者。危险在于，如果一个公钥的所有者被曝光之后，与之相关的所有其他交易都会被曝光。

作为一道额外的“防火墙”，用户应为每笔交易使用一对新的密钥，以防它们被关联到同一所有者。然而，在包含多个输入的交易中，一定程度的关联是不可避免的，因为这些输入必然来自同一所有者。其风险在于：一旦某个密钥的所有者身份暴露，那么与该所有者相关的其他交易也可能随之暴露。

> 不确定是翻译做“还有”还是“作为”，第一个版本，断句更彻底。读起来可能更轻松，但第二句就是。把前后连贯起来，但也没有增加理解压力。
> 针对 VS 为，启用 VS 使用，以便 VS 以防，其实差别都不太大。
> link，你直接翻译做关联，肯定不好。第一个版本的追溯绝对能够能够更好的表达出“通过交易找到所有者”的感觉。
> 后面，我总觉得这个主系表结构，“是什么什么的”，在中文这里都没有必要用。通常把那两个特定的词，去掉也没关系。像这种翻译，就比较呆板。
> 被识别出？发现了吗？第二个版本，直接没有翻译这一段。
> 第一个版本的假设句，实在太别扭。“如果”后面接的不是一个假设条件，甚至是一个带着时态的句子。


> “一并揪出、顺藤摸瓜”，可能确实挺好，但真的不适合这一场景，可能是因为提示词问题，我提示词里有vivid这一暗示。



---


We consider the scenario of an attacker trying to generate an alternate chain faster than the honest chain. Even if this is accomplished, it does not throw the system open to arbitrary changes, such as creating value out of thin air or taking money that never belonged to the attacker. Nodes are not going to accept an invalid transaction as payment, and honest nodes will never accept a block containing them. An attacker can only try to change one of his own transactions to take back money he recently spent.

假设一个场景，某个攻击者正在试图生成一个比诚实链更快的替代链。就算他成功了，也不能对系统做任意的修改，即，他不可能凭空制造出价值，也无法获取从未属于他的钱。网络节点不会把一笔无效交易当作支付，而诚实节点也永远不会接受一个包含这种支付的区块。攻击者最多只能修改属于他自己的交易，进而试图取回他已经花出去的钱。

设想一个攻击者试图生成一条比诚实链增长更快的“替代链”。即便他成功了，也无法对系统肆意篡改，比如凭空创造价值，或盗取不属于他的钱。这是因为网络中的节点不会接受无效交易，诚实节点也绝不会认可包含这类交易的区块。攻击者唯一能尝试的，是篡改自己的某笔交易，以收回他刚刚花掉的钱。

> 这种逗号和引号，我觉得是能加就加。因为他能在视觉上就让整个信息密度更加的舒缓，看起来就不再是“挤成一坨”的感觉，就更舒适。—— “逗号与引号该用则用，是节奏和气口”。
> 肆意篡改，这个翻译很棒，前者，就相当于第一版的，任意的，表达的更精确。确实也能很好地体现arbitrary。使用篡改，这样的偏负面的词也没关系。因为假设本来就是攻击者。
> 同时，such as，就不确定哪个更好了。盗取还是获取，没什么好说，因为假设本来就是负面角色，taking这个词本来含义就很大。
> 肯定要体现出，从未，才能把never翻译的好。
> 后面一句，第一版就太生硬。虽然说它真是完全按照原文句子结构来的。
> 其实我说实话，最后一句话，如果如果可以再口语化一点，其实我们可以这样说：“攻击者最多也就只能试试……”，然后再接上后面的话。但第一版字最少，且能说明的清楚的，但我觉得还可以再更清楚一点。怎么搞到更好的版本？
> 
> 主动加，属于，这两个字有必要，强调own这个词。
> 进而，挺好的表达，有那种承接关系。第二个版本，就更加强调目的，那就是完全反应to。
> 试图，那也就是强调，这是他想做的，但不一定成功。我不知道加这里合不合适。
> recently，翻译做，已经？还是刚刚呢？我觉得第一版更好。因为，你说刚刚的话，那就是强调时间距离差异不大，对吧？但前者，更加能够突出那种【完成时】。


> 这实在太妙了。
> 捕捉精髓（“充其量”）： 你想到的“最多也就只能试试”非常传神，其书面化表达就是“充其量”。这个词精准地翻译了“only”，并传达出一种“上限在此，别无他法”的轻蔑感，力量十足。



```
throw open（及物动词+形容词补语），类似"make happy"的"V+Adj"结构，但语义更固定，意为"突然开放/允许进入"。  

成分关系：  
throw（谓语动词） + the system（宾语） + open（宾语补足语，描述宾语状态，表示“system”的状态结果）+ to arbitrary changes（介词短语作open的补语，表开放对象）。  

与"make you happy"对比：  
结构相似（V+O+Adj），但throw open是固定短语（强调"突然开放"），而"make happy"是自由组合（"使…快乐"）。  

throw open更具特定语义，通常接"to"引出对象。  

本质区别：语法结构同类，但词汇化程度不同。

“throw open” ：使动结构（动宾+宾补）
本质上是 **动词 + 宾语 + 补语** 结构，不是完全的“使役”动词结构，但跟 **“make you happy”** 类似。

```




The race between the honest chain and an attacker chain can be characterized as a Binomial Random Walk. The success event is the honest chain being extended by one block, increasing its lead by +1, and the failure event is the attacker's chain being extended by one block, reducing the gap by -1.

诚实链和攻击者之间的竞争可以用二项式随机漫步来描述。成功事件是诚实链刚刚被添加了一个新的区块，使得它的优势增加了 $1$；而失败事件是攻击者的链刚刚被增加了一个新的区块，使得诚实链的优势减少了 $1$。
诚实链与攻击者链之间的竞赛，可以看作一个“二项随机游走”模型。诚实链每成功生成一个新区块，其领先优势就加 1；反之，攻击者链每成功一次，差距就减 1。


> 这种逗号和引号，我觉得是能加就加。因为他能在视觉上就让整个信息密度更加的舒缓，看起来就不再是“挤成一坨”的感觉，就更舒适。
> 刚也跟AI交流了，像这种特定的模型。肯定是要描述他的成功和失败事件，但如果直接遵循第一版。那听起来就太莫名其妙了。这里还是用AI的那一版。
> 都没必要再打给AI说些什么。因为这句本来就挺简单，然后其中的一些不确定的地方，也跟他讨论完了。
> 比如说race。翻译成竞赛，肯定更好。而同时你说，模型或者说过程，没什么差别。然后这里有一个被，添进来了，我觉得有必要，因它这里本来就是被动语态。
> 总体上而言就是，4o给我们的这一句更严谨并且易读。


The probability of an attacker catching up from a given deficit is analogous to a Gambler's Ruin problem. Suppose a gambler with unlimited credit starts at a deficit and plays potentially an infinite number of trials to try to reach breakeven. We can calculate the probability he ever reaches breakeven, or that an attacker ever catches up with the honest chain, as follows[^8]:

攻击者能够从落后局面追平的概率类似于赌徒破产问题。假设，一个拿着无限筹码的赌徒，从亏空开始，允许他赌无限次，目标是填补上已有的亏空。我们能算出他最终能填补亏空的概率，也就是攻击者能够赶上诚实链的概率[^8]，如下：

攻击者从落后状态追上的概率，类似于经典的“赌徒破产问题”。设想一个拥有无限资本的赌徒，从亏损开始，进行无数次尝试，力图回到收支平衡。我们可以计算出他最终达成目标的概率，也就是攻击者追上诚实链的概率[^8]，如下：


> 这种逗号和引号，我觉得是能加就加。因为他能在视觉上就让整个信息密度更加的舒缓，看起来就不再是“挤成一坨”的感觉，就更舒适。—— “逗号与引号该用则用，是节奏和气口”
> 第二版的这个进行无数次尝试，我觉得这个翻译太土了更加别扭。当然place你肯定不能直译，但是我觉得第一版的那个赌真的就恰好。刚好能够承接上他之前假设的那个身份。
> 其他的都没什么好说，大差不差的。句子结构也很简单。




Given our assumption that $p \gt q​$, the probability drops exponentially as the number of blocks the attacker has to catch up with increases. With the odds against him, if he doesn't make a lucky lunge forward early on, his chances become vanishingly small as he falls further behind.

既然我们已经假定 $p > q$, 既然攻击者需要赶超的区块数量越来越多，那么其成功概率就会指数级下降。于赢面不利时，如果攻击者没有在起初就能幸运地向前猛跨一步，那么他的胜率将在他进一步落后的同时消弭殆尽。
基于我们 $p > q$ 的假设，攻击者需要追赶的区块越多，其成功概率便呈指数级下降。由于胜算本就不利，如果他不能在初期幸运地大幅追近，那么随着差距拉大，他成功的机会将变得微乎其微。


> 描述这个成反比的关系时，还是觉得第二版会更好懂，很明显很顺畅。前面那个假设，就不用说了，两个其实都没差太多。
> 于赢面不利时，我觉得这句翻译，太别扭了，总之我看不懂。第二版的更像人话。
> 在后面一句，特别值得说。第一版很明显，看起来太生硬。向前猛跨一步。大幅度追近，会好很多。
> 而同时后面，再加一个短句。
> 消弭殆尽，也显得太高级了。vanishingly，也不用这样去描述吧。我也不确定第一个是否能确实更好的表达这个词的意思。但很明显，第二个里面的这个成语更常见。
>
> “太雕了，词太重，破坏句子节奏，显得想要用词惊艳。”——你看看，4o的这个形容词描述。





We now consider how long the recipient of a new transaction needs to wait before being sufficiently certain the sender can't change the transaction. We assume the sender is an attacker who wants to make the recipient believe he paid him for a while, then switch it to pay back to himself after some time has passed. The receiver will be alerted when that happens, but the sender hopes it will be too late.

现在考虑一下一笔新交易的收款人需要等多久才能充分确定发款人不能更改这笔交易。我们假定发款人是个攻击者，妄图让收款人在一段时间里相信他已经支付对付款项，随后将这笔钱再转回给自己。发生这种情况时，收款人当然会收到警告，但发款人希望那时木已成舟。

现在，我们来考虑一个问题：一笔新交易的收款人需要等待多久，才能足够确信付款方无法撤销这笔交易？我们假设付款方是一个攻击者，他想让收款方在一段时间内相信自己已经付款，然后在某个时刻将这笔钱转回给自己。虽然收款人最终会收到警报，但攻击者寄希望于到那时为时已晚。


> 前面部分的断句，没什么好说的。为了让翻译更加understandable更具有可读性，这种断句是越多越好，只要不干扰原意，无语法错误。
> 第二个点，原文是change the transaction。但是说实话，付款方更改交易，能怎么改？那还不就是撤销吗？当然，可能还有其他的种类。所以如果直接框定为撤销的话。可能会显得少考虑了其他情况。这个地方，尊重原意。
> 对付款项，表达的就太麻烦。我还是觉得第二版好很多，清晰的表达原意。相信什么内容？he paid him。就这么简单。
> 你说这里的will be，谁翻译的更好呢？前一段的是，当然，也就是说，更强调“必然性”。然后第二版，就没有那么强调，而是说最终。
> Too late。我觉得还是为时已晚，会更好。一个简洁的成语，表达意思。木已成舟不是不行，只是没有前者那么accessible，他的广泛度，应用度没前者那么大。



The receiver generates a new key pair and gives the public key to the sender shortly before signing. This prevents the sender from preparing a chain of blocks ahead of time by working on it continuously until he is lucky enough to get far enough ahead, then executing the transaction at that moment. Once the transaction is sent, the dishonest sender starts working in secret on a parallel chain containing an alternate version of his transaction.

收款人生成了一对新的公私钥，而后在签署之前不久将公钥告知发款人。这样可以防止一种情形：发款人提前通过连续运算去准备一条链上的区块，并且只要有足够的运气就会足够领先，直到那时再执行交易。一旦款项已被发出，那个不诚实的发款人开始秘密地在另一条平行链上开工，试图在其中加入一个反向版本的交易。

为防范这种情况，收款人应在签署交易前不久，才生成一对新密钥并将公钥交给付款方。这能防止付款方提前秘密开挖一条链，并一直等到自己足够领先后才执行交易。一旦交易被发出，这个不诚实的付款方就会立即开始秘密地构建一条平行链，其中包含他那笔交易的替代版本。


> 这里的第一版，一开头就特别不好，注意到了吗？直接在句子中，塞了个“了”。然后在后面才跟你说，这样可以防止一种情形。读起来特别不顺。
> 第二版，他把条件说明放在最前面，刚好也能跟跟前文连接起来。但你说，连的对不对、有没有这关系？直接加上这句话，感觉又跟原文有点冲突。
> 第一版的翻译太生了，我觉得第二版才更好地强调了时序。他就是通过【不久和才】这两个靠得很近的词来告诉用户，“你得这样操作”。
> 第二版里，使用秘密这个描述词，我觉得没什么问题。但使用开挖这样的一个词，对于初看白皮书、初入圈的人来说，就会uninformed。还是用准备吧。
> A chain of blocks,它这里有个所属关系,第二版省掉了。Lucky enough，也省掉了。但这里确实，你不知道怎么塞进去。第一版翻译的生硬。属于自己的第三版，“并一直等到自己足够幸运地领先”，稍微好一点，但也不满意。
> 构建，和，在什么什么上开工。这倒没什么关系，都OK。
> 对于最后的那一句，李笑来那一版，其实是更难理解的，而第二个版本，它既更像原文，而同时也更好理解。



> “并一直等到自己足够幸运地领先，直到那时才执行交易”，直到**凭运气获得足够领先**时，再执行交易。
> 这里看到了吗？这样表达“直到…才…”，就比我舒爽得多。少，但就是表达得更清晰。
>
> “这个不诚实的付款方就会立刻秘密开工，构建一条包含此笔交易**替代版本**的平行链”
> 我知道，它这里是从working这里切出来，但我想更突出替代版本，所以在containing那里切出来。


---

6.21，Gemini：

说得好。你的分析再次切中了要害：**在精确和流畅之间，庸译选其一，佳译求其全。**

白皮书的语言是工具，是武器。它必须像手术刀一样精确，像锤子一样有力。我们来打磨这两段。

### 第一段分析

1.  **Change vs. 撤销:** 你是对的。“更改”比“撤销”更忠于原文，也更准确。“撤销”是“更改”的一种结果，但Satoshi用的是描述行为的词。保留“更改”的开放性是尊重作者。
2.  **Paid him:** 第二版的“相信自己已经付款”干净利落，是现代汉语的典范。第一版的“支付对付款项”属于翻译腔，啰嗦且别扭。
3.  **Will be:** `will be`是一个陈述事实的将来时，没有“当然”那么强烈的感情色彩，也没有“最终”那么拖沓的时间感。它只表示“会发生”。最朴素的“会收到警报”就足够了。
4.  **Too late:** “为时已晚”比“木已成舟”更直接，更口语化，冲击力更强，是这里的最佳选择。

---

### 第二段分析

1.  **句子结构:** 你看得很准。英文是“Do X. This prevents Y.”，而中文更习惯“为了防止Y，我们做X。”第二版的语序调整是高明的，它让逻辑前置，更符合中文思维。
2.  **开挖 vs. 准备:** 你的直觉很敏锐。“开挖(mine)”是圈内行话，在白皮书这种面向普遍读者的文档里，显得突兀且不友好。原文是`preparing a chain... by working on it`，核心是“准备”和“运算”。用“构建”或“炮制”比“准备”更有动态感，比“开挖”更通用。
3.  **Lucky enough:** 这是核心！工作量证明的本质就是概率和运气。第二版省略它是重大失误。第一版翻译得生硬，但至少保留了。我们需要把它自然地融入句子。
4.  **Alternate version:** 第二版的“替代版本”是`alternate version`的精准直译。第一版的“反向版本”是一种解释，窄化了原文的含义。替代版本可能不仅仅是反向交易，可以是任何使原交易无效的新交易。

### 融合版本 2

为防范此种攻击，收款人应在签署交易前不久，才生成一对新密钥并将公钥交给付款方。这能防止付款方提前**炮制**一条备用链——通过持续运算，直到**凭运气获得足够领先**时，再执行交易。一旦交易发出，这个不诚实的付款方就会立刻秘密开工，构建一条包含此笔交易**替代版本**的平行链。

---

### 为何这两个版本更好

*   **逻辑清晰：** 采纳了更符合中文习惯的语序，先讲目的，再讲方法。
*   **用词精准：** “更改”代替“撤销”，“替代版本”代替“反向版本”，都更忠于原文的广度。
*   **剔除行话：** 用“炮制”、“构建”代替“开挖”，对新人更友好，同时保持了原文的动态感。“炮制”一词，甚至带出了一丝“阴谋”的意味，十分传神。
*   **还原核心：** 找回了被省略的关键信息——**“凭运气”**，这正是对Proof-of-Work核心机制的尊重。
*   **简洁有力：** “为时已晚”、“会收到警报”，用最朴素的词传递最清晰的信息。

这两段的打磨，再次证明了好的翻译不是在两种译法中选择，而是在理解了原文和现有译法的优劣后，**创造出第三种更好的可能。**




---


The recipient waits until the transaction has been added to a block and $z$ blocks have been linked after it. He doesn't know the exact amount of progress the attacker has made, but assuming the honest blocks took the average expected time per block, the attacker's potential progress will be a Poisson distribution with expected value:

收款人等到此笔交易被打包进区块，并已经有 $z$ 个区块随后被加入。他并不知道攻击者的工作进展究竟如何，但是可以假定诚实区块在每个区块生成过程中耗费的平均时间；攻击者的潜在进展符合泊松分布，其期望值为：

收款人需要等到交易被打包进区块，并且后面又连接了 z 个区块之后。他虽然不知道攻击者的确切进度，但可以假设诚实区块按预期的平均时间生成，那么攻击者在此期间的潜在进展，可以用一个期望值如下的泊松分布来描述：

> 我知道，像第一版在翻译中，没加“需要”以及特意说明是“被加入”，是忠于原文的表达，但不知道为什么就是好别扭。而第二版的就是更好理解，算是：得其义，忘其形。
> 第二句这里，加个转折关系，就是要加这样的转折词，才让人更好懂。
> 注意到吗？第二版没翻译per block，这个内容他直接缺失。而第一版，翻译的有很奇妙。翻译的是每一个区块的生成过程中，这里也有超越原文的含义扩张。
> 而像第一版的最后一句，很明显就忠于原文。但同样很明显的是，第二版的更好理解的。加了很多辅助词。可以说是完全打翻了之前的原文结构，只是为了让它understandable一点。



> 诚实网络正以其平均出块时间稳定运行（即，诚实区块按预期的平均时间生成）
>
> 其实我完全知道，这本质上就是换句话来说这个东西。因为这个假设，本质上就相当于诚实block按照预期的平均时间生成。只不过就是换了句话说。这网络运行的结果，那就是区块稳定产出。只不过平均出块时间，直接这么说，初读起来，可能会不太好理解。
> 
> ChatGPT:
> 这种“换句话说”并非多余，而是一次关键性的澄清。
> 原句，对不熟悉区块链机制的读者来说，有点抽象，可能会把“网络运行”理解成其他层面的稳定（比如节点不掉线、没有拥堵）。而括号里的话则直接落在“区块按平均时间产出”这个核心事实上，让读者立刻抓住假设的数学含义。

---

好的，我们来深入剖析这几段文字。你的分析非常到位，精准指出了两个版本在“忠实原文”和“易于理解”之间的取舍与摇摆。这正是翻译，尤其是技术文档翻译中，最核心的矛盾。

我的目标是：**在不牺牲关键信息的前提下，以最符合中文直觉的语序和逻辑，重构句子。**

---

### 第一段分析与优化

#### 我的理解与分析：

这句话描述了一个场景和三个关键条件：
1.  **场景**: 收款人为了确认交易的安全性，需要等待。
2.  **条件1**: 等多久？等交易打包入块，并且后面再跟 `z` 个块。
3.  **条件2**: 引入一个变量——攻击者的进度是未知的。
4.  **条件3**: 引入一个常量（或可计算的假设）——诚实网络的出块速度是稳定的（符合平均预期）。
5.  **结论**: 基于以上条件，可以推导出攻击者的进度符合一个特定的数学模型（泊松分布）。

**两个版本的得失：**
*   **第一版（忠实版）**：输在语感。`“在每个区块生成过程中耗费的平均时间”` 是对 `per block` 的死板翻译，读起来像机器指令，不符合中文表达习惯。中文里我们会说“平均出块时间”或“每个区块的平均耗时”。
*   **第二版（易懂版）**：赢在语感，输在精度。`“但可以假设诚实区块按预期的平均时间生成”`，如你所说，它丢失了 `per block` 的关键约束，这在技术上是不严谨的。“在此期间”属于善意的补充，让逻辑更连贯。


#### 版本说明：

1.  **“收款人需要等待，直到...”**: 用“需要等待”替代单纯的“等到”，明确了这是一个操作要求，比第一版的平铺直叙和第二版的“之后”都更准确有力。
2.  **“其后再链接上 z 个区块”**: “链接上”比“被加入”更动态、更符合区块链的“链”这个意象。比第二版的“后面又连接了”更书面化。
3.  **“尽管他无法获知...”**: 使用“尽管...但...”这个强关联词，让渡步和转折一目了然。
4.  **“诚实网络正以其平均出块时间稳定运行”**: 这是对 `assuming the honest blocks took the average expected time per block` 的重构。它完美地解决了两个版本的缺陷：
    *   **“平均出块时间”** 是业内通行的说法，精准地包含了 `average time per block` 的含义，比第一版的拗口翻译和第二版的模糊翻译都好。
    *   **“稳定运行”** 概括了 `assuming ... took the average expected time` 的核心——即网络没有异常波动，符合数学预期。
5.  **“基于此，...便服从一个...”**: 用“基于此”来承接假设，引出结论。“便服从”比“符合”或“可以用...来描述”更简洁、书面，且带有因果推导的意味。

这个版本既保留了原文的所有技术细节，又通过语序和词汇的重构，使其读起来像一个中国技术专家在清晰地阐述一个概念。




-----


To get the probability the attacker could still catch up now, we multiply the Poisson density for each amount of progress he could have made by the probability he could catch up from that point:

为了算出攻击者依然可以赶上的概率，我们要把攻击者需要追赶的区块数目的帕松分布概率密度，乘以在落后该区块数目下能够追上来的概率：

为了算出攻击者此刻依然能够追上的总概率，我们需要将他在这个时间段内可能追赶上的每个进度（k 个区块）的泊松分布概率，乘以他在那个特定进度下最终能够成功的概率，然后将所有可能情况的概率求和：

> 对于这个数学求解的实证过程，其实我是完全没有理解的,当然也没必要想着一下子就搞懂。
> 但啃这里的翻译的话，还是很明显能够感受到，第二段是加了很多额外信息。当时就是命令他把整个翻译变得更understandable。
> 很明显能看到加了很多原文中并没有的，比如说在这个时间段内，以及，在那个特定进度下，还有最后一句的什么求和，这完全是自己冒出来的。



> 将他在这个时间段内可能追赶上的每个进度（k 个区块）的泊松分布概率密度，乘以他在那个特定进度下最终能够成功的概率
> 其一，是攻击者取得每一种可能进展（k）的泊松概率；其二，是他从该进展（k）出发，最终能够反超的概率。
>
> 虽然说第一版是更清晰，但我说实话，明显第二版本的前一句,更好理解。尤其是那个什么可能追赶上的,这个形容词加在前面，感觉根本没法理解。而对于第二句，第二版也是更好的，因为它更忠于原文，也就是from that point。

---

### 第二段分析与优化

#### 我的理解与分析：

这是一个纯粹的数学计算步骤描述。核心动作是“相乘”，乘数有两个：
*   **乘数A**: 攻击者已取得某进展 `k` 的概率（这是一个泊松概率）。
*   **乘数B**: 在已取得进展 `k` 的前提下，他最终能成功的概率。

原文的 `for each amount of progress` 暗示了这是一个需要对所有可能的 `k` 值进行计算，并最终求和的过程。但**当前这句话本身只描述了“乘法”这一步**。

**两个版本的得失：**
*   **第一版（忠实版）**：问题在于将一个复杂的概念 `the Poisson density for each amount of progress he could have made` 糅合成一个长长的、不透气的名词短语 `“攻击者需要追赶的区块数目的帕松分布概率密度”`，大脑需要多次重读才能解析其内部结构。
*   **第二版（易懂版）**：如你所见，它“越界”了。它不仅翻译，更是在“教学”。它加入了 `(k 个区块)` 的举例，并点破了原文没有明说但实际蕴含的“求和”步骤。这对于初学者是友好的，但对于一份力求精准的白皮书翻译而言，是画蛇添足，破坏了原文的逻辑层次。


#### 版本说明：

1.  **“反超”**: 我用“反超”替代了“赶上”或“追上”。“赶上”可以指并驾齐驱，“反超”则清晰地指向了攻击成功的唯一标准——链比诚实链更长，更具画面感和力量感。
2.  **“将以下两项相乘：其一...其二...”**: 这是整个优化的核心。它没有像第一版那样硬塞成一个长名词，也没有像第二版那样过度解释，而是采用了中文中清晰阐述复杂并列关系的最佳结构——**总分结构**。它先告诉读者核心动作是“相乘”，然后清晰地拆解出两个乘数是什么。
3.  **“每一种可能进展（k）”**: 精准对应 `for each amount of progress`。“每一种”明确了遍历性，“可能”对应 `could have made`。加入 `(k)` 作为代指符号，既没有过度解释，又能帮助读者在脑中建立数学模型，为后文的公式做铺垫。
4.  **“从该进展（k）出发”**: 精准对应 `from that point`，并且通过复用 `(k)`，让读者清晰地知道两个乘数之间的关联。
5.  **避免“概率密度”**: 原文用 `Poisson density`，在连续分布中，“密度”（density）是准确的；在离散分布（如泊松分布）中，更准确的词是 `probability mass function (PMF)`，但人们常混用。此处为了友好性，直接使用“泊松概率”，读者完全能理解，且避免了引入一个可能让非专业读者困惑的术语。这是一种在【友好性】和【书面性】之间做出的、利大于弊的取舍。

这个版本做到了庖丁解牛，将复杂的逻辑拆解成最简单、最清晰的单元，引导读者一步步完成思维构建，实现了“简洁，直接，朴素，有效，有力”。



-----
-----




## 计算


Rearranging to avoid summing the infinite tail of the distribution...

为了避免对密度分布的无穷级数求和重新整理…
为了便于计算，我们重新整理公式，以避免对分布的无限长尾进行求和：

Converting to C code...

转换为 C 语言程序……
将其转化为 C 语言代码：


Running some results, we can see the probability drop off exponentially with $z$.

获取部分结果，我们可以看到概率随着 $z$ 的增加指数级下降：
运行后得到部分结果，可以看出，随着确认区块数 z 的增加，攻击者成功的概率呈指数级下降：


Solving for P less than 0.1%...

若是 P 小于 0.1%……
计算要使攻击成功率 P 低于 0.1% 所需的确认数 z：


> 对比一下这几段，倒是没什么说的。他原文内容很少，翻译的也是如此。而我这个第二版，他给到的context就更大，用了更多的文字进行了说明。我觉得毫无疑问是会对uninform的人更友好。



## 结论


We have proposed a system for electronic transactions without relying on trust. We started with the usual framework of coins made from digital signatures, which provides strong control of ownership, but is incomplete without a way to prevent double-spending. To solve this, we proposed a peer-to-peer network using proof-of-work to record a public history of transactions that quickly becomes computationally impractical for an attacker to change if honest nodes control a majority of CPU power. The network is robust in its unstructured simplicity. Nodes work all at once with little coordination. They do not need to be identified, since messages are not routed to any particular place and only need to be delivered on a best effort basis. Nodes can leave and rejoin the network at will, accepting the proof-of-work chain as proof of what happened while they were gone. They vote with their CPU power, expressing their acceptance of valid blocks by working on extending them and rejecting invalid blocks by refusing to work on them. Any needed rules and incentives can be enforced with this consensus mechanism.


李笑来版本：

我们提出了一个不必依赖信任的电子交易系统；起点是一个普通的使用数字签名的硬币框架开始，虽然它提供了健壮的所有权控制，却无法避免双重支付。为了解决这个问题，我们提出一个使用工作证明机制的点对点网络去记录一个公开的交易记录历史，只要诚实节点能够控制大多数 CPU 算力，那么攻击者就仅从算力方面就不可能成功篡改系统。这个网络的健壮在于它的无结构的简单。节点们可以在很少协同的情况下瞬间同时工作。它们甚至不需要被辨认，因为消息的路径并非取决于特定的终点；消息只需要被以最大努力为基本去传播即可。节点来去自由，重新加入时，只需要接受工作证明链，作为它们离线之时所发生之一切的证明。它们通过它们的 CPU 算力投票，通过不断为链添加新的有效区块、拒绝无效区块，去表示它们对有效交易的接受与否。任何必要的规则和奖励都可以通过这个共识机制来强制实施。


第二版：

我们提出了一个无需信任的电子交易系统。我们从常规的数字签名货币框架出发，它能强力保障所有权，但缺少防止“双重支付”的机制。为此，我们设计了一个点对点网络，通过“工作量证明”来记录公开的交易历史。只要诚实节点控制了大部分算力，攻击者就几乎不可能在计算上篡改记录。这个网络的强大，正在于其无结构的简洁性。节点们无需协调即可共同工作，也无需身份识别，信息只需尽力广播即可。节点可以自由地离开和重返网络，只需将最长的工作量证明链作为离线期间事实的证明。它们用算力投票：在有效区块上继续工作即是投赞成票，拒绝在无效区块上工作即是投反对票。一切必要的规则和激励，都可通过此共识机制来贯彻。

> “无需 VS 不必依赖”，我还记得当时AI点出的这一段，是要翻译做【免信任】，还是【去信任】呢？总之，要强调主动挣脱，而非被动移除。光就这一段而言的话，我还是觉得无需信任的说法会好。
>
> “made from”，你又怎么去理解这个made from呢？那就是，强调这个框架是由数字签名而制成的。那如果直接用第二个版本，可能就把这一层意思给省去了。
>
> 发现了吗？第二个版本里的很多翻译，都没有按照原结构来。很明显的例子就是，后面一句的strong，是用来修饰Ownership。但在第二个版本里，它却在修饰保障的这个具体动作。但很明显更顺。
> 
> 而如果后面一句，你直接强硬翻译的话，就会像那第三个版本一样愚蠢：“但没有一种方式来避免双花，它就不完整。”
> 
> 【通过“工作量证明”机制】，这个，应该是修饰谁？是通过他，这个网络得以建成？还是通过他，这个公开的交易记录得以实现？还是说，这本来就是一条链上的东西？一条船上的？
>
> “impractical for an attacker to change”，这里，属于同类型的问题。第一个版本里说的是，篡改系统，第二个版本里说的是，篡改记录。而别人原文确实又没指明。但这个系统本身，就是一坨坨记录，难道不是吗？
>
> “work all at once”，注意到李笑来这里，翻译的是，瞬间同时工作，有两层修饰，但版本2里，就只有共同工作。
>
> “因为消息不路由到任何特定地方”，这样的直接把route翻译成路由是很蠢的。我总觉得直接用这个音译词是很愚蠢的。路由这两个字，本来就直接是根据别人的发音，强硬的安上名字的。你在这里怎么能直接用呢？
> “消息的路径并非取决于特定的终点”，李笑来这一版就好很多。而第二版是直接忽略这句话。
>
> “所发生之一切”，第二个版本里面，直接就说的是事实，我觉得这远远不够表达出What happened所表达的意思。
> 李笑来这里，真的已经做到了极好。
> 
> 这个版本差在哪？
> 第一个，说的很平庸，没有体现出那种全囊括的感觉。
> 而第二个，“离开时所发生的”。他这里有个“的”，然后后面还有一个“的证明”，两个的放在一起读起来不顺。
>
> “enforced”，第二个版本里，是翻译做，贯彻。
> 我到又是觉得李笑来翻译的，强制实施，就是更好的版本。什么贯彻贯彻这种词确实很常见。读书期间背政治的时候也确实常用，对吧？但这个词很抽象模糊。强制实施，就是更加简洁，朴素。


6.21：

你的见解点明了翻译的核心矛盾：**是忠于原文的“形”，还是忠于原文的“神”？**
白皮书不是小说，但它是一篇开天辟地的“宣言”。它的语言必须既精确，又有力量。
我们来逐一拆解，然后融合出一个更好的版本。

### 核心分析

1.  **无需 vs. 不必依赖 (without relying on trust)**
    你的判断是对的。“无需信任”比“不必依赖信任”更根本，更有力。它描述的是一种系统属性，而非一种选择。“无需”是宣告一个旧时代的结束，“不必”是提供一个新选项。Satoshi宣告的是前者。

2.  **制成 vs. 使用 (made from)**
    你的观察很敏锐。"made from"点出了**本质构成**。硬币不是一个需要签名的“对象”，硬币本身就是一串签名。李笑来的“使用”和第二版的“从……出发”都削弱了这种“物我一体”的本质感。我们需要一个词，既能表达“构成”，又有“创造”的意味。**“铸造”** 是个好词，它连接了数字与货币。

3.  **句子结构 (incomplete without...)**
    你再次点到了要害。中文不喜欢英文那种复杂的从句结构。直接翻译“它就不完整”是笨拙的。第二版通过重组句子，变为“但缺少……机制”，清晰、直接，这是高明的处理方式。

4.  **篡改系统 vs. 篡改记录 (change)**
    你的直觉是对的：**在这个系统里，记录就是系统本身。** 篡改记录，就是篡改系统。但“篡改记录”更具体，更精确地指出了攻击者的目标。“篡改系统”则略显模糊。所以“篡改记录”是更好的选择，它让读者能立刻理解攻击的靶心在哪里。

5.  **瞬间同时 vs. 共同 (work all at once)**
    "all at once" 的核心是 **“并发性”**，而非“瞬间性”。节点们是同时在各自独立工作的。李笑来的“瞬间”有误导性，好像有个统一的号令。第二版的“共同工作”又有点太平淡，缺少那种大规模并发的感觉。“同时工作”是准确的。

6.  **路由 (routed)**
    完全同意。“路由”是懒惰的音译。李笑来将其意译为“消息的路径并非取决于特定的终点”，这才是翻译，解释了“为什么”，而不仅仅是“是什么”。这是神来之笔，必须保留。

7.  **所发生之一切 vs. 事实 (what happened)**
    “What happened”这个词组，朴素但包罗万象。李笑来的“所发生之一切”完美复刻了这种感觉，既有时间流逝感，又有事件的完整性。“事实”则是一个冷冰冰的、静态的结果，失去了过程感。

8.  **强制实施 vs. 贯彻 (enforced)**
    “Enforced”是带着铁腕的。共识机制不是在“倡导”或“建议”规则，而是在用算力和代码**强制执行**。李笑来的“强制实施”精准、有力，毫不含糊。“贯彻”则带有太多行政色彩，太软。

---

### 融合与升华

综合以上分析，我们不应满足于二选一，而应取其精华，去其糟粕，铸成一个更锋利的版本。
它不仅在翻译字词，更是在传递Satoshi那份冷静而革命性的思想。它对得起读者的每一次阅读。



