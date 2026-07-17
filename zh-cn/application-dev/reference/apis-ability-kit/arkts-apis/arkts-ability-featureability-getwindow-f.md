# getWindow

## 导入模块

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## getWindow

```TypeScript
function getWindow(callback: AsyncCallback<window.Window>): void
```

获取当前Ability对应的窗口。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function getWindow(callback: AsyncCallback<window.Window>): void--><!--Device-featureAbility-function getWindow(callback: AsyncCallback<window.Window>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<window.Window> | 是 | 回调函数，返回当前Ability对应的窗口。 |

**示例：**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// 获取当前Ability对应的窗口
featureAbility.getWindow((error: BusinessError, data: window.Window) => {
  if (error && error.code !== 0) {
    console.error(`getWindow fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`getWindow success, data: ${typeof(data)}`);
  }
});

```


## getWindow

```TypeScript
function getWindow(): Promise<window.Window>
```

获取当前Ability对应的窗口。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-featureAbility-function getWindow(): Promise<window.Window>--><!--Device-featureAbility-function getWindow(): Promise<window.Window>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<window.Window> | Promise对象，返回当前Ability对应的窗口。 |

**示例：**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// 获取当前Ability对应的窗口
featureAbility.getWindow().then((data: window.Window) => {
  console.info(`getWindow success, data: ${typeof(data)}`);
}).catch((error: BusinessError)=>{
  console.error(`getWindow fail, error: ${JSON.stringify(error)}`);
});

```

