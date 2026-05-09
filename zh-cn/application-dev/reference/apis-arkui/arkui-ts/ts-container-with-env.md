# WithEnv
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->

WithEnv组件用于为一段子组件树设置局部环境变量作用域。开发者可以通过该组件为后代组件提供自定义环境变量，或设置局部布局方向等系统环境变量。

> **说明：**
>
> - 该组件从API version 26.0.0开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
> - 此接口仅可在Stage模型下使用。
> - WithEnv为单子组件容器。需要在作用域内承载多个后代组件时，可使用[Column](ts-container-column.md)、[Row](ts-container-row.md)等组件再包一层。
> - 可通过[customEnv](#customenv)设置自定义环境变量，并在后代自定义组件中通过[@CustomEnv](ts-custom-env-system-property.md#customenv)读取对应值。
> - 当前正式支持通过[env](#env)设置的系统环境变量键为`SystemEnvKeys.DIRECTION`。
> - WithEnv嵌套时，同名环境变量按最近作用域生效。
> - 对于方向环境变量，优先级为：后代组件显式设置[direction](ts-universal-attributes-location.md#direction) > 最近WithEnv方向作用域 > 系统回落。

## 子组件

支持单个子组件。

## 接口

WithEnv()

设置局部环境变量作用域容器。

**原子化服务API：** 从API version 26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束**：此接口仅可在Stage模型下使用。

## 属性

不支持[通用属性](ts-component-general-attributes.md)，支持以下WithEnv专有属性：

### env

env&lt;T&gt;(key: SystemEnvKey&lt;T&gt;, value: T): WithEnvAttribute

设置作用域内的系统环境变量。当前正式支持的系统环境变量键为`SystemEnvKeys.DIRECTION`。

**原子化服务API：** 从API version 26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束**：此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ----- | ---- | ---- |
| key | [SystemEnvKey](#systemenvkey) | 是 | 系统环境变量键。当前正式支持`SystemEnvKeys.DIRECTION`。 |
| value | T | 是 | 系统环境变量值。当`key`为`SystemEnvKeys.DIRECTION`时，`value`类型为[Direction](ts-appendix-enums.md#direction)。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| WithEnvAttribute | 返回当前WithEnv属性对象，可继续链式调用其他WithEnv专有属性。 |

> **说明：**
>
> - `WithEnv.env(SystemEnvKeys.DIRECTION, value)`用于为后代组件提供局部布局方向。
> - 该方向环境变量仅对未显式设置[direction](ts-universal-attributes-location.md#direction)属性的后代组件生效。
> - `Direction.Auto`保留Auto语义；实际非Auto回落仍遵循组件现有方向解析规则。

### customEnv

customEnv(key: string, value: any): WithEnvAttribute

设置作用域内可被后代自定义组件通过[@CustomEnv](ts-custom-env-system-property.md#customenv)读取的自定义环境变量。

**原子化服务API：** 从API version 26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束**：此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ----- | ---- | ---- |
| key | string | 是 | 自定义环境变量的名称。 |
| value | any | 是 | 自定义环境变量的值。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| WithEnvAttribute | 返回当前WithEnv属性对象，可继续链式调用其他WithEnv专有属性。 |

## SystemEnvKey

SystemEnvKey&lt;T&gt;

系统环境变量键类型。开发者无需自行创建实例，可直接使用[SystemEnvKeys](#systemenvkeys)中预定义的系统环境变量键。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SystemEnvKeys

定义可与[env](#env)配合使用的系统环境变量键。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 说明 |
| ----- | ----- | ----- |
| DIRECTION | SystemEnvKey&lt;[Direction](ts-appendix-enums.md#direction)&gt; | 局部布局方向环境变量键。可通过`WithEnv.env(SystemEnvKeys.DIRECTION, value)`设置后代子树的局部方向上下文。 |

## 事件

不支持[通用事件](ts-component-general-events.md)。

## 示例

### 示例1（设置并读取自定义环境变量）

该示例通过`customEnv`设置局部自定义环境变量，并在后代自定义组件中通过[@CustomEnv](ts-custom-env-system-property.md#customenv)读取；同时展示嵌套WithEnv时最近作用域优先。

```ts
// xxx.ets
@Component
struct TitleCard {
  @CustomEnv('card.title') title: string = '默认标题';

  build() {
    Column({ space: 8 }) {
      Text(this.title)
        .fontSize(22)
        .fontWeight(FontWeight.Medium)
      Text('标题内容由 @CustomEnv 读取')
        .fontSize(14)
        .fontColor('#99182431')
    }
    .width('100%')
    .alignItems(HorizontalAlign.Start)
    .padding(12)
    .backgroundColor('#FFF3F5F7')
    .borderRadius(12)
  }
}

@Entry
@Component
struct WithEnvExample1 {
  @State outerTitle: string = '外层标题';

  build() {
    Column({ space: 16 }) {
      Button('切换外层标题')
        .onClick(() => {
          this.outerTitle = this.outerTitle === '外层标题' ? '更新后的外层标题' : '外层标题';
        })

      WithEnv() {
        Column({ space: 12 }) {
          Text('读取外层作用域值')
            .fontSize(14)
            .fontColor('#99182431')
          TitleCard()

          Text('读取内层作用域值')
            .fontSize(14)
            .fontColor('#99182431')
          WithEnv() {
            TitleCard()
          }
          .customEnv('card.title', '内层局部标题')
        }
        .width('100%')
        .alignItems(HorizontalAlign.Start)
      }
      .customEnv('card.title', this.outerTitle)
    }
    .padding(12)
    .width('100%')
  }
}
```

### 示例2（设置局部布局方向）

该示例通过`env(SystemEnvKeys.DIRECTION, value)`为作用域内组件设置局部布局方向，并展示后代组件显式设置`direction`时的优先级。

```ts
// xxx.ets
@Entry
@Component
struct WithEnvExample2 {
  private directionList: Direction[] = [Direction.Ltr, Direction.Rtl, Direction.Auto];
  @State directionIndex: number = 0;

  private getDirectionText(value: Direction): string {
    switch (value) {
      case Direction.Ltr:
        return 'Direction.Ltr';
      case Direction.Rtl:
        return 'Direction.Rtl';
      default:
        return 'Direction.Auto';
    }
  }

  build() {
    Column({ space: 12 }) {
      Button(`切换作用域方向：${this.getDirectionText(this.directionList[this.directionIndex])}`)
        .onClick(() => {
          this.directionIndex = (this.directionIndex + 1) % this.directionList.length;
        })

      WithEnv() {
        Column({ space: 12 }) {
          Text('未显式设置 direction，跟随 WithEnv 作用域')
            .fontSize(14)
            .fontColor('#99182431')
          Row() {
            Text('1').width('25%').height(48).textAlign(TextAlign.Center).backgroundColor(0xF5DEB3)
            Text('2').width('25%').height(48).textAlign(TextAlign.Center).backgroundColor(0xD2B48C)
            Text('3').width('25%').height(48).textAlign(TextAlign.Center).backgroundColor(0xF5DEB3)
            Text('4').width('25%').height(48).textAlign(TextAlign.Center).backgroundColor(0xD2B48C)
          }
          .width('100%')

          Text('显式设置 direction(Direction.Ltr)，优先于 WithEnv 作用域')
            .fontSize(14)
            .fontColor('#99182431')
          Row() {
            Text('1').width('25%').height(48).textAlign(TextAlign.Center).backgroundColor(0xF5DEB3)
            Text('2').width('25%').height(48).textAlign(TextAlign.Center).backgroundColor(0xD2B48C)
            Text('3').width('25%').height(48).textAlign(TextAlign.Center).backgroundColor(0xF5DEB3)
            Text('4').width('25%').height(48).textAlign(TextAlign.Center).backgroundColor(0xD2B48C)
          }
          .width('100%')
          .direction(Direction.Ltr)
        }
        .width('100%')
        .alignItems(HorizontalAlign.Start)
      }
      .env(SystemEnvKeys.DIRECTION, this.directionList[this.directionIndex])
    }
    .padding(12)
    .width('100%')
  }
}
```
