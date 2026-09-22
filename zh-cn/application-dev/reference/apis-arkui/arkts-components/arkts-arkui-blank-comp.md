# Blank

空白填充组件，在容器主轴方向上，空白填充组件具有自动填充容器空余部分的能力。仅当父组件为Row/Column/Flex时生效。

# 子组件

不支持设置子组件。

## Blank

```TypeScript
Blank(min?: number | string)
```

创建空白填充组件。

从API version 10开始：

- Blank在父容器Row, Column 或Flex主轴方向上未设置大小时会自动拉伸、压缩，  
设置了大小或容器自适应子节点大小时不会自动拉伸、压缩。  
- Blank设置主轴方向大小（size）与min时约束关系为max(min, size)。  
- Blank在父容器交叉轴上设置大小时不会撑满父容器交叉轴，交叉轴不设置大小时alignSelf默认值为ItemAlign.Stretch，会撑满容器交叉轴。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| min | number &#124; string | 否 | 空白填充组件在容器主轴上的最小大小。<br>默认值：0，number类型单位为vp，string类型可以显式指定像素单位，如'10px'。不指定像素单位时，默认单位vp，如'10'，等同于10vp。<br>非法值：按默认值处理。<br>**说明：** <br>不支持设置百分比。负值使用默认值。当最小值大于容器可用空间时，使用最小值作为自身大小并超出容器。 |

## 汇总

## 示例

### 示例1（占满空余空间）

Blank组件在横竖屏占满空余空间效果。

竖屏状态



横屏状态



```TypeScript
// xxx.ets
@Entry
@Component
struct BlankExample {
  build() {
    Column() {
      Row() {
        Text('Bluetooth').fontSize(18)
        Blank()
        Toggle({ type: ToggleType.Switch }).margin({ top: 14, bottom: 14, left: 6, right: 6 })
      }.width('100%').backgroundColor(0xFFFFFF).borderRadius(15).padding({ left: 12 })
    }.backgroundColor(0xEFEFEF).padding(20)
  }
}
```

### 示例2（填充固定宽度）

Blank组件的父组件未设置宽度时，min参数的使用效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct BlankExample {
  build() {
    Column({ space: 20 }) {
      // Blank父组件不设置宽度时，Blank失效，可以通过设置min最小宽度填充固定宽度
      Row() {
        Text('Bluetooth').fontSize(18)
        Blank().color(Color.Yellow)
        Toggle({ type: ToggleType.Switch }).margin({ top: 14, bottom: 14, left: 6, right: 6 })
      }.backgroundColor(0xFFFFFF).borderRadius(15).padding({ left: 12 })

      Row() {
        Text('Bluetooth').fontSize(18)
        // 设置最小宽度为160
        Blank('160').color(Color.Yellow)
        Toggle({ type: ToggleType.Switch }).margin({ top: 14, bottom: 14, left: 6, right: 6 })
      }.backgroundColor(0xFFFFFF).borderRadius(15).padding({ left: 12 })

    }.backgroundColor(0xEFEFEF).padding(20).width('100%')
  }
}
```
