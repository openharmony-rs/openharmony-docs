# create

## create

```TypeScript
function create(config: FloatingBallConfiguration): Promise<FloatingBallController>
```

创建闪控球控制器，使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | FloatingBallConfiguration | 是 | 创建闪控球控制器的参数。该参数不能为空，并且构造该参数的context不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FloatingBallController&gt; | Promise对象。返回当前创建的闪控球控制器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |
| [1300019](../errorcode-window.md#1300019-闪控球参数校验错误) | Wrong parameters for operating the floating ball. |
| [1300023](../errorcode-window.md#1300023-闪控球内部错误) | Floating ball internal error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 声明闪控球控制器实例
let floatingBallController: floatingBall.FloatingBallController | undefined = undefined;
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回的结果为UIAbilityContext
let ctx = this.getUIContext().getHostContext() as common.UIAbilityContext; 
// 配置闪控球控制器参数
let config: floatingBall.FloatingBallConfiguration = {
  context: ctx,
};
try {
  // 创建闪控球控制器
  floatingBall.create(config).then((data: floatingBall.FloatingBallController) => {
    // 保存控制器实例
    floatingBallController = data;
    console.info(`Succeeded in creating floating ball controller. Data: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to create floating ball controller. Cause:${err.code}, message:${err.message}`);
  });
} catch (e) {
  console.error(`Failed to create floating ball controller. Cause:${e.code}, message:${e.message}`);
}

```

