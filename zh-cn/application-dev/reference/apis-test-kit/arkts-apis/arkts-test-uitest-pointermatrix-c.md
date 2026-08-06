# PointerMatrix

存储多指操作中每根手指每一步动作的坐标点及其行为的二维数组。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare class PointerMatrix--><!--Device-unnamed-declare class PointerMatrix-End-->

**系统能力：** SystemCapability.Test.UiTest

## create

ArkTS-Dyn:
```TypeScript
static create(fingers: number, steps: number): PointerMatrix
```

ArkTS-Sta:
```TypeScript
static create(fingers: int, steps: int): PointerMatrix
```

静态方法，构造一个PointerMatrix对象，并返回该对象。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PointerMatrix-static create(fingers: int, steps: int): PointerMatrix--><!--Device-PointerMatrix-static create(fingers: int, steps: int): PointerMatrix-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fingers | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 多指操作中注入的手指数，取值范围：[1,10]的整数。 |
| steps | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 每根手指操作的步骤数，取值范围：[1,1000]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | - 返回构造的PointerMatrix对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
// xxx.test.ets
import { PointerMatrix } from '@kit.TestKit';

async function demo() {
  let pointerMatrix: PointerMatrix = PointerMatrix.create(2, 3);
}
```

## setPoint

ArkTS-Dyn:
```TypeScript
setPoint(finger: number, step: number, point: Point): void
```

ArkTS-Sta:
```TypeScript
setPoint(finger: int, step: int, point: Point): void
```

设置PointerMatrix对象中指定手指和步骤对应动作的坐标点。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PointerMatrix-setPoint(finger: int, step: int, point: Point): void--><!--Device-PointerMatrix-setPoint(finger: int, step: int, point: Point): void-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| finger | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 手指的序号，取值大于等于0的整数，且不超过构造PointerMatrix对象时设置的手指数。 |
| step | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 步骤的序号，取值大于等于0的整数，且不超过构造PointerMatrix对象时设置的操作的步骤数。 |
| point | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 该行为的坐标点。建议相邻的坐标点距离在10px至80px范围内。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
// xxx.test.ets
import { PointerMatrix } from '@kit.TestKit';

async function demo() {
  let pointers: PointerMatrix = PointerMatrix.create(2, 5);
  pointers.setPoint(0, 0, { x: 250, y: 480 });
  pointers.setPoint(0, 1, { x: 250, y: 440 });
  pointers.setPoint(0, 2, { x: 250, y: 400 });
  pointers.setPoint(0, 3, { x: 250, y: 360 });
  pointers.setPoint(0, 4, { x: 250, y: 320 });
  pointers.setPoint(1, 0, { x: 250, y: 480 });
  pointers.setPoint(1, 1, { x: 250, y: 440 });
  pointers.setPoint(1, 2, { x: 250, y: 400 });
  pointers.setPoint(1, 3, { x: 250, y: 360 });
  pointers.setPoint(1, 4, { x: 250, y: 320 });
}
```

