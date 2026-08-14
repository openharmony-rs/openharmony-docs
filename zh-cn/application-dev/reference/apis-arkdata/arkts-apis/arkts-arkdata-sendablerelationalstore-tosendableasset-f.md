# toSendableAsset

## toSendableAsset

```TypeScript
function toSendableAsset(asset: NonSendableAsset): Asset
```

将不可跨线程传递的附件数据，转换为可跨线程传递的附件数据。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-sendableRelationalStore-function toSendableAsset(asset: NonSendableAsset): Asset--><!--Device-sendableRelationalStore-function toSendableAsset(asset: NonSendableAsset): Asset-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| asset | [NonSendableAsset](arkts-arkdata-sendablerelationalstore-nonsendableasset-t.md) | 是 | 不可跨线程传递的Asset数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Asset | 可跨线程传递的Asset数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; &lt;br&gt;3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |

## 示例

```TypeScript
const asset1: sendableRelationalStore.NonSendableAsset = {
  name: 'hangman',
  uri: '//path/example',
  path: '//path/example',
  createTime: 'createTime1',
  modifyTime: 'modifyTime1',
  size: 'size1'
};
const sendableAsset = sendableRelationalStore.toSendableAsset(asset1);
```

