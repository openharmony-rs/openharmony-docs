# offChangeSceneAnimationState（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## offChangeSceneAnimationState

```TypeScript
function offChangeSceneAnimationState(callback?: Callback<formInfo.ChangeSceneAnimationStateRequest>): void
```

Cancels listening to the event of change scene animation state. You can use this method to cancel listening to the event of change scene animation state.

**起始版本：** 23

<!--Device-formHost-function offChangeSceneAnimationState(callback?: Callback<formInfo.ChangeSceneAnimationStateRequest>): void--><!--Device-formHost-function offChangeSceneAnimationState(callback?: Callback<formInfo.ChangeSceneAnimationStateRequest>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;formInfo.ChangeSceneAnimationStateRequest&gt; | 否 | The callback of change scene animation state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

**示例**

```TypeScript
'use static'

import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callback = (data: formInfo.ChangeSceneAnimationStateRequest) => {
  console.info( 'testTag', `offChangeSceneAnimationState ChangeSceneAnimationStateRequest, data.formId: ${data.formId}`);
}
try {
  formHost.offChangeSceneAnimationState(callback);
  console.info( 'testTag EntryFormAbility', 'changeSceneAnimationState off success');
} catch (error) {
  console.info( 'testTag EntryFormAbility', `changeSceneAnimationState off catch error ${error.code}, ${error.message}`);
}
```

