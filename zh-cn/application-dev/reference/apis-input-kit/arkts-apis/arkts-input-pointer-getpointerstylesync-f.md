# getPointerStyleSync

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

<a id="getpointerstylesync"></a>
## getPointerStyleSync

```TypeScript
function getPointerStyleSync(windowId: number): PointerStyle
```

查询指定窗口的鼠标样式类型，如向东箭头、向西箭头、向南箭头、向北箭头等。此接口仅支持获取本应用进程内窗口的鼠标样式类型。

**起始版本：** 10

<!--Device-pointer-function getPointerStyleSync(windowId: int): PointerStyle--><!--Device-pointer-function getPointerStyleSync(windowId: int): PointerStyle-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | number | 是 | 窗口ID。取值范围为大于等于-1的整数，取值为-1时表示全局窗口。<br>窗口ID合法并且对应窗口存在时，返回窗口的鼠标光标样式。<br>窗口ID合法但窗口不存在时，默认返回全局鼠标光标样式。<br>如果通过[setPointerStyleSync](arkts-input-pointer-setpointerstylesync-f.md#setpointerstylesync-1)接口为不存在的窗口设置了鼠标光标样式，使用本接口可以正常获取到该光标样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PointerStyle](../../apis-arkui/arkts-apis/arkts-arkui-pointerstyle-t.md) | 返回鼠标样式类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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
          let windowId = -1;
          try {
            let style: pointer.PointerStyle = pointer.getPointerStyleSync(windowId);
            console.info(`Succeeded in getting pointer style, style: ${JSON.stringify(style)}.`);
          } catch (error) {
            console.error(`Failed to get pointer style, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

