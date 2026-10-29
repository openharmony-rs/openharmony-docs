# createDataShareHelper (System API)

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## createDataShareHelper

```TypeScript
function createDataShareHelper(context: Context, uri: string, callback: AsyncCallback<DataShareHelper>): void
```

Creates a **DataShareHelper** instance. This API uses an asynchronous callback to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-dataShare-function createDataShareHelper(context: Context, uri: string, callback: AsyncCallback<DataShareHelper>): void--><!--Device-dataShare-function createDataShareHelper(context: Context, uri: string, callback: AsyncCallback<DataShareHelper>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the application. |
| uri | string | Yes | URI of the server application to connect. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataShareHelper](arkts-arkdata-datashare-datasharehelper-i-sys.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **DataShareHelper** instance created. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 19 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameters types. |
| [15700010](../errorcode-datashare.md#15700010-failed-to-create-a-datasharehelper) | The DataShareHelper fails to be initialized. |

<!--Del-->
**Examples**

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

<!--DelEnd-->


## createDataShareHelper

```TypeScript
function createDataShareHelper(
    context: Context,
    uri: string,
    options: DataShareHelperOptions,
    callback: AsyncCallback<DataShareHelper>
  ): void
```

Creates a **DataShareHelper** instance. **DataShareHelperOptions** specifies whether **DataShareHelper** is in proxy mode. This API uses an asynchronous callback to return the result.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-dataShare-function createDataShareHelper(    context: Context,    uri: string,    options: DataShareHelperOptions,    callback: AsyncCallback<DataShareHelper>  ): void--><!--Device-dataShare-function createDataShareHelper(    context: Context,    uri: string,    options: DataShareHelperOptions,    callback: AsyncCallback<DataShareHelper>  ): void-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the application. |
| uri | string | Yes | URI of the server application to connect. |
| options | [DataShareHelperOptions](arkts-arkdata-datashare-datasharehelperoptions-i-sys.md) | Yes | Specifies whether [DataShareHelper](arkts-arkdata-datashare-datasharehelper-i-sys.md) is in proxy mode, and specifies the waiting time for startup during non-silent access. If not set, [DataShareHelper](arkts-arkdata-datashare-datasharehelper-i-sys.md) is not in proxy mode, and the waiting time for startup during non-silent access is 2 seconds. If the URI starts with **datashareproxy**, the **isProxy** parameter of **options** must be set; otherwise, **DataShareHelper** creation fails and an error is returned. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataShareHelper](arkts-arkdata-datashare-datasharehelper-i-sys.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **DataShareHelper** instance created. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 19 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameters types. |
| [15700010](../errorcode-datashare.md#15700010-failed-to-create-a-datasharehelper) | The DataShareHelper fails to be initialized. |

<!--Del-->
**Examples**

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

<!--DelEnd-->


## createDataShareHelper

```TypeScript
function createDataShareHelper(
    context: Context,
    uri: string,
    options?: DataShareHelperOptions
  ): Promise<DataShareHelper>
```

Creates a **DataShareHelper** instance. **DataShareHelperOptions** specifies whether **DataShareHelper** is in proxy mode. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-dataShare-function createDataShareHelper(    context: Context,    uri: string,    options?: DataShareHelperOptions  ): Promise<DataShareHelper>--><!--Device-dataShare-function createDataShareHelper(    context: Context,    uri: string,    options?: DataShareHelperOptions  ): Promise<DataShareHelper>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the application. |
| uri | string | Yes | URI of the server application to connect. |
| options | [DataShareHelperOptions](arkts-arkdata-datashare-datasharehelperoptions-i-sys.md) | No | Optional configuration. It specifies whether the [DataShareHelper](arkts-arkdata-datashare-datasharehelper-i-sys.md) is in proxy mode and the wait time for startup during non-silent access. If this parameter is not set, the [DataShareHelper](arkts-arkdata-datashare-datasharehelper-i-sys.md) is not in proxy mode, and the wait time for startup during non-silent access is 2 seconds. If the URI starts with **datashareproxy**, the **isProxy** parameter of **options** must be set; otherwise, the **DataShareHelper** fails to be created and an error is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DataShareHelper](arkts-arkdata-datashare-datasharehelper-i-sys.md)&gt; | Promise used to return the **DataShareHelper** instance created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 19 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameters types. |
| [15700010](../errorcode-datashare.md#15700010-failed-to-create-a-datasharehelper) | The DataShareHelper fails to be initialized. |

<!--Del-->
**Examples**

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

<!--DelEnd-->
