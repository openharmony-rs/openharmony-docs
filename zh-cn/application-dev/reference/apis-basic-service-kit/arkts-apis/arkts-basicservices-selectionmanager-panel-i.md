# Panel（系统接口）

划词面板。

**起始版本：** 24

<!--Device-selectionManager-interface Panel--><!--Device-selectionManager-interface Panel-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

## moveToGlobalDisplay

```TypeScript
moveToGlobalDisplay(x: number, y: number): Promise<void>
```

移动划词面板至屏幕指定位置。使用Promise异步回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-moveToGlobalDisplay(x: int, y: int): Promise<void>--><!--Device-Panel-moveToGlobalDisplay(x: int, y: int): Promise<void>-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | x轴方向移动的值，单位为px。 |
| y | number | 是 | y轴方向移动的值，单位为px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务异常) | Selection service exception. |
| [33600002](../../apis-basic-services-kit/errorcode-selection.md#33600002-划词面板已被销毁) | This selection window has been destroyed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 移动划词面板至屏幕指定位置。selectionPanel为createPanel创建出的panel实例
  selectionPanel.moveToGlobalDisplay(200, 200).then(() => {
    console.info('Succeeded in moving the panel.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
}

```

