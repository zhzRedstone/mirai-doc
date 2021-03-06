[mirai-core](../../index.md) / [net.mamoe.mirai.message.data](../index.md) / [OnlineMessageSource](./index.md)

# OnlineMessageSource

`sealed class OnlineMessageSource : `[`MessageSource`](../-message-source/index.md)

在线消息的 [MessageSource](../-message-source/index.md).
拥有对象化的 [sender](sender.md), [target](target.md), 也可以直接 [recall](../../net.mamoe.mirai.message/recall.md) 和 [quote](../../net.mamoe.mirai.message/quote.md)

### 来源

* 当 bot 主动发送消息时, 产生 (由协议模块主动构造) [OnlineMessageSource.Outgoing](-outgoing/index.md)
* 当 bot 接收消息时, 产生 (由协议模块根据服务器的提供的信息构造) [OnlineMessageSource.Incoming](-incoming/index.md)

#### 机器人主动发送消息

当机器人 [主动发出消息](../../net.mamoe.mirai.contact/-member/send-message.md), 将会得到一个 [消息回执](../../net.mamoe.mirai.message/-message-receipt/index.md).
此回执的 [消息源](../../net.mamoe.mirai.message/-message-receipt/source.md) 即为一个 [外向消息源](-outgoing/index.md), 代表着刚刚发出的那条消息的来源.

#### 机器人接受消息

当机器人接收一条消息 [MessageEvent](../../net.mamoe.mirai.message/-message-event/index.md), 这条消息包含一个 [内向消息源](-incoming/index.md), 代表着接收到的这条消息的来源.

### 实现

此类的所有子类都有协议模块实现. 不要自行实现它们, 否则将无法发送

**See Also**

[OnlineMessageSource.toOffline](../to-offline.md)

### Types

| Name | Summary |
|---|---|
| [Incoming](-incoming/index.md) | 接收到的一条消息的 [MessageSource](../-message-source/index.md)`sealed class Incoming : `[`OnlineMessageSource`](./index.md) |
| [Key](-key/index.md) | `companion object Key : Key<`[`OnlineMessageSource`](./index.md)`>` |
| [Outgoing](-outgoing/index.md) | 由 [机器人主动发送消息](../../net.mamoe.mirai.contact/-contact/send-message.md) 产生的 [MessageSource](../-message-source/index.md), 可通过 [MessageReceipt](../../net.mamoe.mirai.message/-message-receipt/index.md) 获得.`sealed class Outgoing : `[`OnlineMessageSource`](./index.md) |

### Properties

| Name | Summary |
|---|---|
| [sender](sender.md) | 消息发送人. 可能为 [机器人](../../net.mamoe.mirai/-bot/index.md) 或 [好友](../../net.mamoe.mirai.contact/-friend/index.md) 或 [群员](../../net.mamoe.mirai.contact/-member/index.md). 即类型必定为 [Bot](../../net.mamoe.mirai/-bot/index.md), [Friend](../../net.mamoe.mirai.contact/-friend/index.md) 或 [Member](../../net.mamoe.mirai.contact/-member/index.md)`abstract val sender: `[`ContactOrBot`](../../net.mamoe.mirai.contact/-contact-or-bot/index.md) |
| [subject](subject.md) | 消息主体. 群消息时为 [Group](../../net.mamoe.mirai.contact/-group/index.md). 好友消息时为 [Friend](../../net.mamoe.mirai.contact/-friend/index.md), 临时消息为 [Member](../../net.mamoe.mirai.contact/-member/index.md) 不论是机器人接收的消息还是发送的消息, 此属性都指向机器人能进行回复的目标.`abstract val subject: `[`Contact`](../../net.mamoe.mirai.contact/-contact/index.md) |
| [target](target.md) | 消息发送目标. 可能为 [机器人](../../net.mamoe.mirai/-bot/index.md) 或 [好友](../../net.mamoe.mirai.contact/-friend/index.md) 或 [群](../../net.mamoe.mirai.contact/-group/index.md). 即类型必定为 [Bot](../../net.mamoe.mirai/-bot/index.md), [Friend](../../net.mamoe.mirai.contact/-friend/index.md) 或 [Group](../../net.mamoe.mirai.contact/-group/index.md)`abstract val target: `[`ContactOrBot`](../../net.mamoe.mirai.contact/-contact-or-bot/index.md) |

### Companion Object Properties

| Name | Summary |
|---|---|
| [typeName](type-name.md) | 此 [Key](../-message/-key/index.md) 指代的 [Message](../-message/index.md) 类型名. 一般为 `class.simpleName`, 如 "QuoteReply", "PlainText"`val typeName: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html) |

### Extension Properties

| Name | Summary |
|---|---|
| [content](../content.md) | [Message.contentToString](../-message/content-to-string.md) 的捷径`val `[`Message`](../-message/index.md)`.content: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html) |

### Extension Functions

| Name | Summary |
|---|---|
| [copyAmend](../copy-amend.md) | 复制这个消息源, 并以 [block](../copy-amend.md#net.mamoe.mirai.message.data$copyAmend(net.mamoe.mirai.message.data.MessageSource, kotlin.Function1((net.mamoe.mirai.message.data.MessageSourceAmender, kotlin.Unit)))/block) 修改`fun `[`MessageSource`](../-message-source/index.md)`.copyAmend(block: `[`MessageSourceAmender`](../-message-source-amender/index.md)`.() -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`OfflineMessageSource`](../-offline-message-source/index.md) |
| [flatten](../flatten.md) | 扁平化 [Message](../-message/index.md)`fun `[`Message`](../-message/index.md)`.flatten(): `[`Sequence`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.sequences/-sequence/index.html)`<`[`SingleMessage`](../-single-message.md)`>` |
| [isAboutFriend](../is-about-friend.md) | 判断是否是发送给好友, 或从好友接收的消息的消息源`fun `[`MessageSource`](../-message-source/index.md)`.isAboutFriend(): `[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) |
| [isAboutGroup](../is-about-group.md) | 判断是否是发送给群, 或从群接收的消息的消息源`fun `[`MessageSource`](../-message-source/index.md)`.isAboutGroup(): `[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) |
| [isAboutTemp](../is-about-temp.md) | 判断是否是发送给临时会话, 或从临时会话接收的消息的消息源`fun `[`MessageSource`](../-message-source/index.md)`.isAboutTemp(): `[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) |
| [isContentEmpty](../is-content-empty.md) | 判断消息内容是否为空.`fun `[`Message`](../-message/index.md)`.isContentEmpty(): `[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) |
| [isContentNotEmpty](../is-content-not-empty.md) | `fun `[`Message`](../-message/index.md)`.isContentNotEmpty(): `[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) |
| [isNotPlain](../is-not-plain.md) | `fun `[`Message`](../-message/index.md)`.isNotPlain(): `[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) |
| [isPlain](../is-plain.md) | `fun `[`Message`](../-message/index.md)`.isPlain(): `[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) |
| [plus](../plus.md) | `suspend operator fun `[`Message`](../-message/index.md)`.plus(another: Flow<`[`Message`](../-message/index.md)`>): `[`MessageChain`](../-message-chain/index.md) |
| [quote](../quote.md) | 引用这条消息`fun `[`MessageSource`](../-message-source/index.md)`.quote(): `[`QuoteReply`](../-quote-reply/index.md) |
| [recall](../recall.md) | 撤回这条消息. 可撤回自己 2 分钟内发出的消息, 和任意时间的群成员的消息.`suspend fun `[`MessageSource`](../-message-source/index.md)`.recall(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html) |
| [recallIn](../recall-in.md) | 在一段时间后撤回这条消息. 可撤回自己 2 分钟内发出的消息, 和任意时间的群成员的消息.`fun `[`MessageSource`](../-message-source/index.md)`.recallIn(timeMillis: `[`Long`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-long/index.html)`, coroutineContext: `[`CoroutineContext`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.coroutines/-coroutine-context/index.html)` = EmptyCoroutineContext): Job` |
| [repeat](../repeat.md) | 将此消息元素按顺序重复 [count](../repeat.md#net.mamoe.mirai.message.data$repeat(net.mamoe.mirai.message.data.Message, kotlin.Int)/count) 次.`fun `[`Message`](../-message/index.md)`.repeat(count: `[`Int`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-int/index.html)`): `[`MessageChain`](../-message-chain/index.md) |
| [sendTo](../send-to.md) | `suspend fun <C : `[`Contact`](../../net.mamoe.mirai.contact/-contact/index.md)`> `[`Message`](../-message/index.md)`.sendTo(contact: C): `[`MessageReceipt`](../../net.mamoe.mirai.message/-message-receipt/index.md)`<C>` |
| [times](../times.md) | 将此消息元素按顺序重复 [count](../times.md#net.mamoe.mirai.message.data$times(net.mamoe.mirai.message.data.Message, kotlin.Int)/count) 次.`operator fun `[`Message`](../-message/index.md)`.times(count: `[`Int`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-int/index.html)`): `[`MessageChain`](../-message-chain/index.md) |
| [toForwardMessage](../to-forward-message.md) | 转换为 [ForwardMessage](../-forward-message/index.md)`fun `[`Message`](../-message/index.md)`.toForwardMessage(sender: `[`User`](../../net.mamoe.mirai.contact/-user/index.md)`, time: `[`Int`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-int/index.html)` = currentTimeSeconds.toInt(), displayStrategy: DisplayStrategy = DisplayStrategy): `[`ForwardMessage`](../-forward-message/index.md)<br>`fun `[`Message`](../-message/index.md)`.toForwardMessage(senderId: `[`Long`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-long/index.html)`, senderName: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, time: `[`Int`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-int/index.html)` = currentTimeSeconds.toInt(), displayStrategy: DisplayStrategy = DisplayStrategy): `[`ForwardMessage`](../-forward-message/index.md) |
| [toOffline](../to-offline.md) | 将在线消息源转换为离线消息源.`fun `[`OnlineMessageSource`](./index.md)`.toOffline(): `[`OfflineMessageSource`](../-offline-message-source/index.md) |
