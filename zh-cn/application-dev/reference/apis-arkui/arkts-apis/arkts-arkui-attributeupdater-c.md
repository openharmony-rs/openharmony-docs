# AttributeUpdater

将属性直接设置给组件，无需标记为状态变量即可直接触发UI更新。适用于需要在不定义状态变量的情况下动态更新组件属性的场景，如动态修改组件构造参数、避免为一次性属性更新定义状态变量等。

**继承/实现关系：** AttributeUpdater implements AttributeModifier<T>

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## applyNormalAttribute

```TypeScript
applyNormalAttribute?(instance: T): void
```

定义正常态更新属性函数，在AttributeUpdater后续更新属性时触发。不建议在同一组件上同时用属性直通更新和属性方法设置相同属性，否则易出现混淆。当与属性方法同时设置时，属性生效的原则为后设置的生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类实例，开发者通过调用该实例的属性方法来设置或更新组件的正常态属性，比如Button组件的ButtonAttribute，Text组件的TextAttribute等。 |

## initializeModifier

```TypeScript
initializeModifier(instance: T): void
```

AttributeUpdater首次设置给组件时提供的样式。不建议在同一组件上同时用属性直通更新和属性方法设置相同属性，否则易出现混淆。当与属性方法同时设置时，属性生效的原则为后设置的生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类实例，开发者通过调用该实例的属性方法来初始化设置组件的样式属性，比如Button组件的ButtonAttribute，Text组件的TextAttribute等。 |

**示例**

通过initializeModifier方法初始化设置属性值。

```TypeScript
// xxx.ets
import { AttributeUpdater } from '@kit.ArkUI';

class MyButtonModifier extends AttributeUpdater<ButtonAttribute> {
  // 该AttributeUpdater对象第一次使用的时候触发的回调
  initializeModifier(instance: ButtonAttribute): void {
    instance.backgroundColor('#ffd5d5d5')
      .labelStyle({ maxLines: 3 })
      .width('80%');
  }

  // 该AttributeUpdater对象后续使用或者更新的时候触发的回调
  applyNormalAttribute(instance: ButtonAttribute): void {
    instance.borderWidth(1);
  }
}

@Entry
@Component
struct Index {
  modifier: MyButtonModifier = new MyButtonModifier();
  @State flushTheButton: string = 'Button';

  build() {
    Row() {
      Column() {
        Button(this.flushTheButton)
          .attributeModifier(this.modifier)
          .onClick(() => {
            // 通过AttributeUpdater的attribute对属性进行修改
            // 需要注意先通过组件的attributeModifier属性方法建立组件与AttributeUpdater绑定关系
            this.modifier.attribute?.backgroundColor('#ff2787d9').labelStyle({ maxLines: 5 });
          })
          .margin('10%')
        Button('Trigger Button Update')
          .width('80%')
          .labelStyle({ maxLines: 2 })
          .onClick(() => {
            this.flushTheButton = this.flushTheButton + ' Updated';
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## onComponentChanged

```TypeScript
onComponentChanged(component: T): void
```

当多个组件绑定同一个自定义AttributeUpdater对象，且绑定的组件发生切换时，通过该接口通知应用。需注意一个AttributeUpdater对象只能同时关联一个组件，否则将出现设置的属性只在一个组件上生效的现象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| component | T | 是 | 组件的属性类实例，开发者通过调用该实例的属性方法来设置切换后组件的属性，比如Button组件的ButtonAttribute，Text组件的TextAttribute等。 |

**示例**

```TypeScript
// xxx.ets
import { AttributeUpdater } from '@kit.ArkUI';

class MyButtonModifier extends AttributeUpdater<ButtonAttribute> {
  initializeModifier(instance: ButtonAttribute): void {
    instance.backgroundColor('#ff2787d9')
      .width('50%')
      .height(30);
  }

  onComponentChanged(component: ButtonAttribute): void {
    component.backgroundColor('#ff519db4')
      .width('50%')
      .height(30);
  }
}

@Entry
@Component
struct UpdaterDemo4 {
  @State btnState: boolean = false;
  modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Button('Test')
          .onClick(() => {
            this.btnState = !this.btnState;
          }).margin({ bottom: 20 })

        if (this.btnState) {
          Button('Button')
            .attributeModifier(this.modifier)
        } else {
          Button('Button')
            .attributeModifier(this.modifier)
        }
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## attribute

```TypeScript
get attribute(): T | undefined
```

获取AttributeUpdater中组件对应的属性类实例，通过该实例实现属性直通更新。需先通过组件的attributeModifier属性方法建立组件与AttributeUpdater的绑定关系，绑定后方可获取到属性类实例。不建 议在同一组件上同时用属性直通更新和属性方法设置相同属性；当与属性方法同时设置时，属性生效的原则为后设置的生效。

**类型：** T

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

通过属性直通设置方式更新属性值。

```TypeScript
// xxx.ets
import { AttributeUpdater } from '@kit.ArkUI';

class MyButtonModifier extends AttributeUpdater<ButtonAttribute> {
  initializeModifier(instance: ButtonAttribute): void {
    instance.backgroundColor('#ffd5d5d5')
      .width('50%')
      .height(30);
  }
}

@Entry
@Component
struct UpdaterDemo2 {
  modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Button('Button')
          .attributeModifier(this.modifier)
          .onClick(() => {
            this.modifier.attribute?.backgroundColor('#ff2787d9').width('30%');
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## updateConstructorParams

```TypeScript
updateConstructorParams: C
```

C代表组件的构造函数类型，比如Text组件的TextInterface，Image组件的ImageInterface等。用于更改组件的构造函数入参。需先通过组件的attributeModifier属性方法建立组件与 AttributeUpdater的绑定关系，绑定后方可使用。当前仅支持Button、Image、Text、Span、SymbolSpan和ImageSpan组件，使用前需确保T和C类型匹配，否则可能导致功能异常。

**类型：** C

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
