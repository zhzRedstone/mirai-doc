[mirai-core](../index.md) / [net.mamoe.mirai.message.data](index.md) / [firstIsInstance](./first-is-instance.md)

# firstIsInstance

`fun <reified M : `[`Message`](-message/index.md)`> `[`MessageChain`](-message-chain/index.md)`.firstIsInstance(): M`

获取第一个 [M](first-is-instance.md#M) 类型的 [Message](-message/index.md) 实例

### Exceptions

`NoSuchElementException` - 如果找不到该类型的实例