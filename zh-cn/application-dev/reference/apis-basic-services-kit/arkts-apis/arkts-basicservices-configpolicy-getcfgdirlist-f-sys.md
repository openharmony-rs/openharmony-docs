# getCfgDirList（系统接口）

## 导入模块

```TypeScript
import { configPolicy } from '@kit.BasicServicesKit';
```

## getCfgDirList

```TypeScript
function getCfgDirList(callback: AsyncCallback<Array<string>>): void
```

获取配置层级目录列表，按优先级从低到高。使用callback异步回调。

**起始版本：** 8

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数。当获取配置层级目录列表成功，err为undefined， data为获取到的配置层级目录列表；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1.Mandatory parameters are left unspecified;  2.Incorrect parameter types. |

**示例**

```TypeScript
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

configPolicy.getCfgDirList((err: BusinessError, data: Array<string>) => {
  if (err == null) {
    console.info('data is ' + data);
  } else {
    console.error('err: ' + err.code + ', ' + err.message);
  }
});
```


## getCfgDirList

```TypeScript
function getCfgDirList(): Promise<Array<string>>
```

获取配置层级目录列表，按优先级从低到高。使用Promise异步回调。

**起始版本：** 8

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;string & gt; & gt; | Promise对象，返回配置层级目录列表。 |

**示例**

```TypeScript
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

async function fetchCfgDirList() {
  try {
    let value: Array<string> = await configPolicy.getCfgDirList();
    console.info('value is ' + value);
  } catch (error) {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error('error:' + code + ', ' + message);
  }
}

fetchCfgDirList();
```
