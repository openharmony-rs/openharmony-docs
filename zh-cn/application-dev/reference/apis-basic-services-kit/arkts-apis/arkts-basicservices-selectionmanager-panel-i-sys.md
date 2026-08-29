# Panel

划词面板对象，通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f.md)创建，提供面板内容设置、显示、隐藏、移动及事件订阅等管理能力，适用于在划词完成后向用户展示自定义操作界面的场景。

**起始版本：** 24

**系统能力：** SystemCapability.SelectionInput.Selection

## 导入模块

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

## moveTo

```TypeScript
moveTo(x: number, y: number): Promise<void>
```

移动划词面板至屏幕全局坐标系下的指定位置，支持移动到扩展屏上。需通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f.md)获取到Panel实例后调用。使用Promise异步回调。

> **说明：**
> 
> 从API version 20开始支持，从API version 24开始废弃。

**起始版本：** 20

**废弃版本：** 24

**替代接口：** [moveToGlobalDisplay](arkts-basicservices-selectionmanager-panel-i.md#movetoglobaldisplay)

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 目标位置在屏幕全局坐标系下的x轴坐标，单位为px。全局坐标系以主屏幕左上角为原点，x轴正方向向右；扩展屏的x坐标视屏幕布局可能为负值。 |
| y | number | 是 | 目标位置在屏幕全局坐标系下的y轴坐标，单位为px。全局坐标系以主屏幕左上角为原点，y轴正方向向下；扩展屏的y坐标视屏幕布局可能为负值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../errorcode-selection.md#33600001-划词服务调用异常) | Selection service exception. |
| [33600002](../errorcode-selection.md#33600002-划词面板已被销毁) | This selection window has been destroyed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 移动划词面板至屏幕指定位置。selectionPanel为createPanel创建出的panel实例
  selectionPanel.moveTo(200, 200).then(() => {
    console.info('Succeeded in moving the panel.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
}
```
