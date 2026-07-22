# enableSilentProxy（系统接口）

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## enableSilentProxy

```TypeScript
function enableSilentProxy(context: Context, uri?: string): Promise<void>
```

开启静默访问。使用Promise异步回调。

使用规则：

- 数据提供方调用此接口，来开启静默访问功能。  
- 此接口设置的开启结果在校验的时候是搭配data_share_config.json文件中isSilentProxyEnable字段进行工作的。支持的配置可参考[data_share_config.json配置](../../../database/share-data-by-datashareextensionability-sys.md)。  
- 此接口生效在调用datashareHelper相关接口过程中，如果此接口有开启过相关uri，那么会按照此接口的配置来开启静默访问。如果此接口未调用过，则会读取data_share_config.json中的配置来校验Datashare的开启状态。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dataShare-function enableSilentProxy(context: Context, uri?: string): Promise<void>--><!--Device-dataShare-function enableSilentProxy(context: Context, uri?: string): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用的上下文环境。 |
| uri | string | 否 | 要开启的数据提供方的数据路径。<br />1、全局开关状态：入参不带uri、uri为undefined、uri为null，会清空掉之前设置的所有uri开关状态，开启数据提供方静默访问。<br />2、精准开关状态：uri的入参为固定的值，仅开启该uri对应的静默访问。<br />在调用datashareHelper相关接口时，优先精准匹配uri的开关状态。如果匹配不到，继续匹配全局的开关状态。<br/>uri格式：datashare:///{bundleName}/{moduleName}/{storeName}/{tableName} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 19+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700011](../errorcode-datashare.md#15700011-uri不存在) | The URI does not exist. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let uri = "datashare:///com.acts.datasharetest/entry/DB00/TBL00?Proxy=true";
    let context = this.context;
    dataShare.enableSilentProxy(context, uri).then(() => {
      console.info("enableSilentProxy succeed");
    }).catch((err: BusinessError) => {
      console.error(`Failed to enable silent proxy. Code: ${err.code}, message: ${err.message}`);
    });
  }
}

```

