# isKeyExist

## isKeyExist

```TypeScript
function isKeyExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>): void
```

判断密钥是否存在。使用callback异步回调。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用 > [huks.isKeyItemExist&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-iskeyitemexist-f.md#isKeyItemExist) > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [isKeyItemExist](arkts-universalkeystore-huks-iskeyitemexist-f.md#isKeyItemExist)(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;boolean&gt;)

<!--Device-huks-function isKeyExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>): void--><!--Device-huks-function isKeyExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 所需查找的密钥的别名。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于查询时指定密钥的属性TAG。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。false代表密钥不存在，true代表密钥存在。 |

## 示例

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
huks.isKeyExist(keyAlias, emptyOptions, (err, data) => {
});
```


## isKeyExist

```TypeScript
function isKeyExist(keyAlias: string, options: HuksOptions): Promise<boolean>
```

判断密钥是否存在。使用Promise异步回调。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用 > [huks.isKeyItemExist&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-iskeyitemexist-f.md#isKeyItemExist)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [isKeyItemExist](arkts-universalkeystore-huks-iskeyitemexist-f.md#isKeyItemExist)(keyAlias: string, options: HuksOptions)

<!--Device-huks-function isKeyExist(keyAlias: string, options: HuksOptions): Promise<boolean>--><!--Device-huks-function isKeyExist(keyAlias: string, options: HuksOptions): Promise<boolean>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 所需查找的密钥的别名。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于查询时指定密钥的属性TAG。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。false代表密钥不存在，true代表密钥存在。 |

## 示例

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.isKeyExist(keyAlias, emptyOptions);
```

