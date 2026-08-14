# generateRandomBinaryUUID

## generateRandomBinaryUUID

```TypeScript
function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array
```

使用加密安全随机数生成器生成随机的RFC 4122版本4的Uint8Array类型UUID。为了提升性能，此接口会默认使用缓存，即入参为true， 最多可缓存128个随机的UUID。当缓存中128个UUID用尽后，会重新生成，以保证UUID的随机性。如需禁用缓存，请将入参设置为false。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-util-function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array--><!--Device-util-function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entropyCache | boolean | 否 | 是否使用已缓存的UUID，true表示使用缓存的UUID以提升性能（最多缓存128个UUID，缓存用尽后会重新生成以保证随机性）， false表示不使用缓存的UUID，默认true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 表示此UUID的Uint8Array值。 |

## 示例

```TypeScript
let uuid = util.generateRandomBinaryUUID(true);
console.info(JSON.stringify(uuid));
// 输出随机生成的UUID
```

