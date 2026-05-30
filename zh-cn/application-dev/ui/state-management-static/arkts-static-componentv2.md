# \@ComponentV2装饰器：自定义组件

为了在自定义组件中使用V2版本状态变量装饰器的能力，开发者可以使用\@ComponentV2装饰器装饰自定义组件。

\@ComponentV2主要配合状态管理V2使用。

>**说明：**
>
>从API版本26.0.0开始，\@ComponentV2装饰的自定义组件支持跨[Ability](../../reference/apis-ability-kit/js-apis-app-ability-ability.md)迁移。因为自定义组件提供的是UI能力，所以这里的Ability也特指[UIAbility](../../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)。具体示例参考[自定义组件支持跨Ability迁移](#自定义组件支持跨ability迁移)。\@Component装饰的自定义组件同样支持该能力，详见[\@Component装饰器：自定义组件](./arkts-static-create-component.md#自定义组件支持跨ability迁移)。

## 概述

### \@ComponentV2

\@ComponentV2装饰器用于装饰自定义组件：

- 在\@ComponentV2装饰的自定义组件中，开发者仅可以使用全新的状态变量装饰器，包括[\@Local](./arkts-static-new-local.md)、[\@Param](./arkts-static-new-param.md)、[\@Once](./arkts-static-new-once.md)、[\@Event](./arkts-static-new-event.md)、[\@Provider、\@Consumer](./arkts-static-new-provider-and-consumer.md)。



- 一个简单的\@ComponentV2装饰的自定义组件应具有以下部分：

    ```ts
    'use static'
    
    import { ComponentV2, Entry, Local } from '@kit.ArkUI';
    
    @ComponentV2 // 装饰器
    struct Index { // struct声明的数据结构
      @Local local: number = 1; // 声明为@Local的装饰器变量
      build() { // build定义的UI
      }
    }
    ```

除非特别说明，\@ComponentV2装饰的自定义组件将与\@Component装饰的自定义组件保持相同的行为。

## 支持自定义组件扩展

从API version 23开始，开发者可以在自定义组件中重写通用属性的方法，并使用[`super`](../../quick-start/introduction-to-arkts.md)关键字调用基类的通用属性的方法。当使用“.”链式调用自定义组件方法时，需注意以下事项：
1. 实现链式调用的关键是：每个方法必须返回[`this`](../../quick-start/introduction-to-arkts.md#this)，以允许连续调用。如果某个方法未返回`this`，则无法作为链式调用的中间步骤，导致后续调用无法解析，从而引发编译错误。
2. 通过链式调用的方法，其调用时机是在创建自定义组件时，所以在方法内，不能改变关联其他组件或方法的状态变量，否则会有运行时报错。

示例如下。

```typescript
'use static'

import { Color, ColorMetrics, Column, ComponentV2, Consumer, Entry, Local, Provider, ResourceColor, Text } from '@kit.ArkUI';
import hilog from '@ohos.hilog';

@ComponentV2
struct ChildComponent {
  @Consumer() message: string = 'default';
  @Local info: string = 'default';

  // override关键字可缺省
  override backgroundColor(value: ResourceColor | ColorMetrics | undefined): this {
    hilog.info(0X0000, 'testTag', `override backgroundColor`);
    // this.message = 'Change'; // 运行时报错，禁止在构建组件树的过程中修改有依赖的状态变量
    this.info = 'Change'; // 正常运行，可以在构建组件树的过程中修改没有依赖的状态变量
    super.backgroundColor(Color.Pink); // 背景颜色显示为粉色，开发者可以选择不调用基类的backgroundColor方法，即不设置背景颜色
    return this;
  }

  // overload
  backgroundColor(value: Array<number>): this {
    hilog.info(0X0000, 'testTag', `overload backgroundColor`);
    return this;
  }

  // myStyle没有返回this，仅可以在链式调用的最后一项被调用
  myStyle(): void {
    hilog.info(0X0000, 'testTag', `myStyle`);
  }

  build() {
    Column() {
      Text(`ChildComponent info ${this.info}`)
      Text(`ChildComponent message ${this.message}`)
    }
  }
}

@Entry
@ComponentV2
struct MyComponent {
  @Provider() message: string = 'Hello World';

  build() {
    Column() {
      Text(`MyComponent message ${this.message}`)

      ChildComponent()
        .width(300)
        .height(300)
        .backgroundColor(Color.Red)
        .backgroundColor([0])
        .myStyle()
    }
    .height(500)
    .width(300)
  }
}
```

## 限制

- \@ComponentV2装饰的自定义组件不支持[LocalStorage](./arkts-static-localstorage.md)。
- 无法同时使用\@ComponentV2与\@Component装饰同一个struct结构。
- [\@Entry](./arkts-static-create-component.md#entry)搭配自定义组件装饰器\@ComponentV2使用时，仅接受routeName作为参数。如果\@Entry传入storage或useSharedStorage参数，会编译报错。

## 自定义组件支持跨Ability迁移

API版本26.0.0前，\@ComponentV2装饰的自定义组件不支持跨Ability迁移，自定义组件实例在跨Ability后，改变自定义组件的状态变量将无法触发UI组件刷新。

API版本26.0.0开始，\@ComponentV2装饰的自定义组件支持跨Ability迁移。

需要注意：
仅支持组件树上的自定义组件迁移。对于未挂载在组件树上的自定义组件将不支持迁移。

在下面的示例中：
1. 点击```Button('add node to tree')```，创建BuilderNode节点挂载到`NodeContainer`下。
2. 点击```Button('remove node from tree')```，将BuilderNode节点从`NodeContainer`上移除。
3. 点击```Button('start new ability')```，拉起`ExtraAbility`。
4. 点击`ExtraIndex`内的```Button('add node to tree')```，将BuilderNode节点重新挂载到`ExtraIndex`内的`NodeContainer`下。
   - 自定义组件`ComponentUnderBuilderNode`在被挂载到新的Ability下时，会通知切换Ability的自定义组件更新其所属的Ability实例ID。
   - 点击自定义组件`ComponentUnderBuilderNode`内```Button('change message')```，改变状态变量`message`的值，触发```@Monitor('message') ```回调和UI刷新。

下面的示例包含了创建新的Ability流程，具体示例可参考[starAbility](../../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability)。

``` TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

const DOMAIN = 0x0000;

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        hilog.error(DOMAIN, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      hilog.info(DOMAIN, 'testTag', 'Succeeded in loading the content.');
    });
  }
}
```

``` TypeScript
import { MyNodeController } from './MyNodeController';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const DOMAIN = 0x0000;

@Entry
@ComponentV2
struct Index {
  private nodeController: MyNodeController = new MyNodeController();

  startNewAbility() {
    const want: Want = {
      bundleName: 'com.example.enablecustomcomponentcrossability',
      abilityName: 'ExtraAbility'
    };

    try {
      const context = this.getUIContext()?.getHostContext() as common.UIAbilityContext;
      context.startAbility(want, (err: BusinessError) => {
        if (err.code) {
          hilog.error(DOMAIN, 'testTag', `startAbility failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        hilog.info(DOMAIN, 'testTag', 'startAbility succeed');
      });
    } catch (err) {
      hilog.error(DOMAIN, 'testTag',
        `startAbility failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
    }
  }

  build() {
    Column({ space: 10 }) {
      Text('Index')
      // 创建globalBuilderNode，并将globalBuilderNode下的节点挂在NodeContainer的占位节点下
      Button('add node to tree').width(200).onClick(() => {
        this.nodeController.addBuilderNode();
      })
      // 从NodeContainer的占位节点下移除globalBuilderNode下的节点
      Button('remove node from tree').width(200).onClick(() => {
        this.nodeController.removeBuilderNode();
      })
      // 拉起新的Ability
      Button('start new ability').width(200).onClick(() => {
        this.startNewAbility();
      })
      NodeContainer(this.nodeController).backgroundColor('#FFEEF0')
    }
    .width('100%')
    .height('100%')
  }
}
```

``` TypeScript
import { BuilderNode, FrameNode, NodeController } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Monitor } from '@kit.ArkUI';

const DOMAIN = 0x0000;

let globalBuilderNode: BuilderNode<[]> | undefined = undefined;

export class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.uiContext = uiContext;
    return this.rootNode;
  }

  addBuilderNode(): void {
    if (!globalBuilderNode && this.uiContext) {
      globalBuilderNode = new BuilderNode(this.uiContext);
      globalBuilderNode.build(wrapBuilder<[]>(buildComponent), undefined);
    }
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.appendChild(globalBuilderNode.getFrameNode());
    }
  }

  removeBuilderNode(): void {
    if (this.rootNode && globalBuilderNode) {
      this.rootNode.removeChild(globalBuilderNode.getFrameNode());
    }
  }

  disposeNode(): void {
    if (this.rootNode && globalBuilderNode) {
      globalBuilderNode.dispose();
      globalBuilderNode = undefined;
    }
  }
}

@Builder
function buildComponent() {
  Column() {
    ComponentUnderBuilderNode()
  }
}

@ComponentV2
struct ComponentUnderBuilderNode {
  @Local message: string = 'hello';

  @Monitor('message')
  messageUpdate() {
    hilog.info(DOMAIN, 'testTag', `ComponentUnderBuilderNode message change ${this.message}`);
  }

  build() {
    Column() {
      Text(`message: ${this.message}`)
      // 改变message的值，触发@Monitor('message')回调和Text组件的刷新
      Button('change message').onClick(() => {
        this.message += ' world';
      })
    }
  }
}
```

``` TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

const DOMAIN = 0x0000;

export default class ExtraAbility extends UIAbility {

  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/ExtraIndex', (err) => {
      if (err.code) {
        hilog.error(DOMAIN, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      hilog.info(DOMAIN, 'testTag', 'Succeeded in loading the content.');
    });
  }
}
```

``` TypeScript
import { MyNodeController } from './MyNodeController';

@Entry
@ComponentV2
struct ExtraIndex {
  private nodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 10 }) {
      Text('ExtraIndex')
      // 将globalBuilderNode下的节点挂在NodeContainer的占位节点下
      Button('add node to tree').width(200).onClick(() => {
        this.nodeController.addBuilderNode();
      })
      // 从NodeContainer的占位节点下移除globalBuilderNode下的节点
      Button('remove node from tree').width(200).onClick(() => {
        this.nodeController.removeBuilderNode();
      })
      // 销毁globalBuilderNode下的节点
      Button('dispose node').width(200).onClick(() => {
        this.nodeController.disposeNode();
      })
      NodeContainer(this.nodeController).backgroundColor('#FFEEF0')
    }
    .width('100%')
    .height('100%')
  }
}
```