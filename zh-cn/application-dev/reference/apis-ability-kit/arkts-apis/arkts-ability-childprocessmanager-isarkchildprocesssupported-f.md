# isArkChildProcessSupported

## 导入模块

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
```

## isArkChildProcessSupported

```TypeScript
function isArkChildProcessSupported(): boolean
```

查询是否允许调用者在此设备上创建ArkTS子进程

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否允许调用者创建ArkTS子进程。 |

**示例**

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('Click')
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            try {
              let isSupport: boolean = childProcessManager.isArkChildProcessSupported();
              console.info(`isArkChildProcessSupported: ${isSupport}`);
            } catch (err: BusinessError) {
              console.error(`isArkChildProcessSupported error, errorCode: ${err.code}, errorMsg: ${err.message}`);
            }
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
