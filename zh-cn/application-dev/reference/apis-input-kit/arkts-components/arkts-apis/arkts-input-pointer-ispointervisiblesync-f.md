# isPointerVisibleSync

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## isPointerVisibleSync

```TypeScript
function isPointerVisibleSync(): boolean
```

获取当前窗口的显示/隐藏状态，此状态反映的是多模进程对此窗口所在进程的光标显示/隐藏状态，并非真实的光标显示/隐藏情况，光标是否正确显示/隐藏还受渲染服务进程影响，函数调用使用同步方式。

**起始版本：** 10

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回鼠标光标显示或隐藏状态。true代表显示状态，false代表隐藏状态。 |

**示例**

```TypeScript
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let visible: boolean = pointer.isPointerVisibleSync();
            console.info(`Succeeded in getting pointer visible, visible: ${JSON.stringify(visible)}.`);
          } catch (error) {
            console.error(`Failed to get pointer visible, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
