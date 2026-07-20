# createDataShareHelper（系统接口）

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

<a id="createdatasharehelper"></a>
## createDataShareHelper

```TypeScript
function createDataShareHelper(context: Context, uri: string, callback: AsyncCallback<DataShareHelper>): void
```

创建DataShareHelper实例。使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dataShare-function createDataShareHelper(context: Context, uri: string, callback: AsyncCallback<DataShareHelper>): void--><!--Device-dataShare-function createDataShareHelper(context: Context, uri: string, callback: AsyncCallback<DataShareHelper>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用的上下文环境。 |
| uri | string | 是 | 要连接的服务端应用的路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DataShareHelper&gt; | 是 | 回调函数。当创建DataShareHelper实例成功，err为undefined，data为获取到的DataShareHelper实例；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 19+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700010](../errorcode-datashare.md#15700010-创建datasharehelper异常) | The DataShareHelper fails to be initialized. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let uri = "datashare:///com.samples.datasharetest.DataShare";
    let dataShareHelper: dataShare.DataShareHelper | undefined = undefined;
    let context = this.context;
    try {
      dataShare.createDataShareHelper(context, uri, (err:BusinessError, data:dataShare.DataShareHelper) => {
        if (err !== undefined) {
          console.error(`Failed to create DataShareHelper. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info("createDataShareHelper succeed, data : " + data);
        dataShareHelper = data;
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`Failed to create DataShareHelper. Code: ${code}, message: ${message}`);
    };
  }
}

```


<a id="createdatasharehelper-1"></a>
## createDataShareHelper

```TypeScript
function createDataShareHelper(
    context: Context,
    uri: string,
    options: DataShareHelperOptions,
    callback: AsyncCallback<DataShareHelper>
  ): void
```

创建DataShareHelper实例，通过DataShareHelperOptions指定是否通过代理访问。使用callback异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dataShare-function createDataShareHelper(
    context: Context,
    uri: string,
    options: DataShareHelperOptions,
    callback: AsyncCallback<DataShareHelper>
  ): void--><!--Device-dataShare-function createDataShareHelper(
    context: Context,
    uri: string,
    options: DataShareHelperOptions,
    callback: AsyncCallback<DataShareHelper>
  ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | Indicates the application context. |
| uri | string | 是 | Indicates the path of the file to open. |
| options | [DataShareHelperOptions](arkts-arkdata-datashare-datasharehelperoptions-i-sys.md) | 是 | Indicates the optional config. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DataShareHelper&gt; | 是 | {DataShareHelper}: The dataShareHelper for consumer. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 19+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700010](../errorcode-datashare.md#15700010-创建datasharehelper异常) | The DataShareHelper fails to be initialized. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let uri = "datashareproxy://com.samples.datasharetest.DataShare";
    let dataShareHelper: dataShare.DataShareHelper | undefined = undefined;
    let context = this.context;
    try {
      dataShare.createDataShareHelper(context, uri, {isProxy : true}, (err:BusinessError, data:dataShare.DataShareHelper) => {
        if (err !== undefined) {
          console.error(`Failed to create DataShareHelper. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info("createDataShareHelper succeed, data : " + data);
        dataShareHelper = data;
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`Failed to create DataShareHelper. Code: ${code}, message: ${message}`);
    };
  }
}

```


<a id="createdatasharehelper-2"></a>
## createDataShareHelper

```TypeScript
function createDataShareHelper(
    context: Context,
    uri: string,
    options?: DataShareHelperOptions
  ): Promise<DataShareHelper>
```

创建DataShareHelper实例，通过DataShareHelperOptions指定是否通过代理访问。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dataShare-function createDataShareHelper(
    context: Context,
    uri: string,
    options?: DataShareHelperOptions
  ): Promise<DataShareHelper>--><!--Device-dataShare-function createDataShareHelper(
    context: Context,
    uri: string,
    options?: DataShareHelperOptions
  ): Promise<DataShareHelper>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用的上下文环境。 |
| uri | string | 是 | 要连接的服务端应用的路径。 |
| options | [DataShareHelperOptions](arkts-arkdata-datashare-datasharehelperoptions-i-sys.md) | 否 | 可选配置。指定[DataShareHelper](arkts-arkdata-datashare-datasharehelperoptions-i-sys.md)是否在代理模式下，指定非静默访问时的等待拉起时间。如果不设置，则表示[DataShareHelper](arkts-arkdata-datashare-datasharehelperoptions-i-sys.md)不在代理模式下，且非静默访问时的等待拉起时间为2秒。如果uri以datashareproxy为开头，则必须设置options的isProxy参数，否则DataShareHelper创建失败返回错误。<br>**起始版本：** 10 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataShareHelper&gt; | Promise对象。返回DataShareHelper实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 19+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [15700010](../errorcode-datashare.md#15700010-创建datasharehelper异常) | The DataShareHelper fails to be initialized. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let uri = "datashareproxy://com.samples.datasharetest.DataShare";
    let dataShareHelper: dataShare.DataShareHelper | undefined = undefined;
    let context = this.context;
    try {
      dataShare.createDataShareHelper(context, uri, {isProxy : true}).then((data: dataShare.DataShareHelper) => {
        console.info("createDataShareHelper succeed, data : " + data);
        dataShareHelper = data;
      }).catch((err: BusinessError) => {
        console.error(`Failed to create DataShareHelper. Code: ${err.code}, message: ${err.message}`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`Failed to create DataShareHelper. Code: ${code}, message: ${message}`);
    };
  }
}

```

