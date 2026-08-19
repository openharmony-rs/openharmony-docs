# requestOverflow

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## requestOverflow

```TypeScript
function requestOverflow(formId: string, overflowInfo: formInfo.OverflowInfo): Promise<void>
```

卡片提供方发起互动卡片动效请求，只针对[场景动效类型互动卡片](../../../form/arkts-ui-widget-configuration.md#sceneanimationparams标签)生效，使用Promise 异步回调。其中相关的方法为[cancelOverflow()](arkts-form-formprovider-canceloverflow-f.md)：取消互动卡片动效请求，用于取消已发起的动效。 > **说明：** > > 1. 该接口在省电模式场景下不可使用，会报16501000错误码。 > > 2. 当设备热档位进入HOT场景并且没有点击事件的场景下，该接口会报16501000错误码；当热档位进入OVERHEATED时，任何情况下都会报16501000错误码。热档位信息具体可参考 > [热档位信息](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-thermal-thermallevel-e.md)。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function requestOverflow(formId: string, overflowInfo: formInfo.OverflowInfo): Promise<void>--><!--Device-formProvider-function requestOverflow(formId: string, overflowInfo: formInfo.OverflowInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| overflowInfo | formInfo.OverflowInfo | 是 | 动效请求参数信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function requestOverflow can not work correctly due to limited device capabilities. |
| [16501001](../errorcode-form.md#16501001-卡片id不存在) | The ID of the form to be operated does not exist. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16501011](../errorcode-form.md#16501011-卡片不支持调用当前接口) | The form cannot support this operation. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // 表示卡片formId，根据实际formId调整
let overflowInfo: formInfo.OverflowInfo = {
  area: {
    left: -10,
    top: -10,
    width: 180,
    height: 180
  },
  duration: 1000,
  useDefaultAnimation: false,
};

try {
  formProvider.requestOverflow(formId, overflowInfo).then(() => {
    console.info('requestOverflow succeed.');
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // 表示卡片formId，根据实际formId调整

try {
  let rect: formInfo.Rect = {
    left: -30,
    top: -30,
    width: 200,
    height: 200
  };
  let overflowInfo: formInfo.OverflowInfo = {
    area: rect,
    duration: 3500,
    useDefaultAnimation: false
  };
  formProvider.requestOverflow(formId, overflowInfo).then(() => {
    console.info('testTag', 'requestOverflow succeed');
  }).catch((error) => {
    console.info('testTag', `requestOverflow err: code is ${error.code}, message ${error.message}`);
  })
} catch (error) {
  console.info('testTag',
    `requestOverflow err: code is ${error.code}, message ${error.message}`);
}
```

