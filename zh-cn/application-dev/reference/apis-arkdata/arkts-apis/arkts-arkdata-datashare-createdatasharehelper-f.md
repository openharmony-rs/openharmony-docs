# createDataShareHelper

## createDataShareHelper

```TypeScript
function createDataShareHelper(context: Context, uri: string, callback: AsyncCallback<DataShareHelper>): void
```

创建DataShareHelper实例。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dataShare-function createDataShareHelper(context: Context, uri: string, callback: AsyncCallback<DataShareHelper>): void--><!--Device-dataShare-function createDataShareHelper(context: Context, uri: string, callback: AsyncCallback<DataShareHelper>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 应用的上下文环境。 |
| uri | string | 是 | 要连接的服务端应用的路径。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DataShareHelper&gt; | 是 | 回调函数。当创建DataShareHelper实例成功，err为undefined，data为获取到的DataShareHelper实例；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 19+ |
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

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dataShare-function createDataShareHelper(    context: Context,    uri: string,    options: DataShareHelperOptions,    callback: AsyncCallback<DataShareHelper>  ): void--><!--Device-dataShare-function createDataShareHelper(    context: Context,    uri: string,    options: DataShareHelperOptions,    callback: AsyncCallback<DataShareHelper>  ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Indicates the application context. |
| uri | string | 是 | Indicates the path of the file to open. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Indicates the optional config. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DataShareHelper&gt; | 是 | {DataShareHelper}: The dataShareHelper for consumer. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 19+ |
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

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dataShare-function createDataShareHelper(    context: Context,    uri: string,    options?: DataShareHelperOptions  ): Promise<DataShareHelper>--><!--Device-dataShare-function createDataShareHelper(    context: Context,    uri: string,    options?: DataShareHelperOptions  ): Promise<DataShareHelper>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 应用的上下文环境。 |
| uri | string | 是 | 要连接的服务端应用的路径。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 可选配置。指定[DataShareHelper]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_是否在代理模式下，指定非静默访问时的等待拉起时间。如果不设置，则表示[DataShareHelper]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_不在代理模式下，且非静默访问时的等待拉起时间为2秒。如果uri以datashareproxy为开头，则必须设置options的isProxy参数，否则DataShareHelper创建失败返回错误。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 10 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataShareHelper&gt; | Promise对象。返回DataShareHelper实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 19+ |
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

