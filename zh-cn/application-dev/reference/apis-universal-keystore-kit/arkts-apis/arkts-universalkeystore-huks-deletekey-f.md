# deleteKey

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

<a id="deletekey"></a>
## deleteKey

```TypeScript
function deleteKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

删除密钥。使用callback异步回调。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [huks.deleteKeyItem<sup>9+</sup>](arkts-universalkeystore-huks-deletekeyitem-f.md#deletekeyitem-1)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [deleteKeyItem(keyAlias:](arkts-universalkeystore-huks-deletekeyitem-f.md#deletekeyitem-1)

<!--Device-huks-function deleteKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void--><!--Device-huks-function deleteKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 密钥别名，应为生成key时传入的别名。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于删除时指定密钥的属性TAG。 |
| callback | AsyncCallback&lt;HuksResult&gt; | 是 | 回调函数。当删除密钥成功时，err为undefined，data为获取到的HuksResult；否则为错误对象。 |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
huks.deleteKey(keyAlias, emptyOptions, (err, data) => {
});

```


<a id="deletekey-1"></a>
## deleteKey

```TypeScript
function deleteKey(keyAlias: string, options: HuksOptions): Promise<HuksResult>
```

删除密钥。使用Promise异步回调。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [huks.deleteKeyItem<sup>9+</sup>](arkts-universalkeystore-huks-deletekeyitem-f.md#deletekeyitem-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [deleteKeyItem(keyAlias:](arkts-universalkeystore-huks-deletekeyitem-f.md#deletekeyitem-1)

<!--Device-huks-function deleteKey(keyAlias: string, options: HuksOptions): Promise<HuksResult>--><!--Device-huks-function deleteKey(keyAlias: string, options: HuksOptions): Promise<HuksResult>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 密钥别名，应为生成key时传入的别名。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于删除时指定密钥的属性TAG。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise对象，返回HuksResult。 |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* 此处options选择emptyOptions传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.deleteKey(keyAlias, emptyOptions).then((data) => {
  console.info('delete key success');
}).catch((err: BusinessError) => {
  console.error("密钥删除失败，错误码是： " + err.code + " 错误码信息： " + err.message);
});

```

