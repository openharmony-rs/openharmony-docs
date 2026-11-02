# IDefaultReusePool

```TypeScript
export declare interface IDefaultReusePool
```

`IDefaultReusePool`接口提供自定义组件上的默认复用池的相关功能，包括清理复用池中的节点。

**起始版本：** 26.1.0

<!--Device-unnamed-export declare interface IDefaultReusePool--><!--Device-unnamed-export declare interface IDefaultReusePool-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IDefaultReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## clearCache

```TypeScript
clearCache(reuseId?: string): void
```

清理复用池中的节点。

指定reuseId时，仅清理该reuseId对应的可复用自定义组件的节点；未指定时，清理复用池中的全部节点。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-IDefaultReusePool-clearCache(reuseId?: string): void--><!--Device-IDefaultReusePool-clearCache(reuseId?: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reuseId | string | 否 | 需要清理的复用池中可复用自定义组件的复用标识ID。 |

**示例**

以下示例中，点击Recycle A按钮或Recycle B按钮可将自定义组件回收进默认复用池，点击Clear All按钮可释放默认复用池中的所有组件，点击Clear A按钮可释放默认复用池中reuseId为A的组件。

```TypeScript
import { UIUtils } from '@kit.ArkUI';

@ReusableV2
@ComponentV2
struct ReusableChild {
  @Param label: string = '';
  aboutToAppear() {
    console.info(`ReusableChild [${this.label}] aboutToAppear`);
  }
  aboutToDisappear() {
    console.info(`ReusableChild [${this.label}] aboutToDisappear`);
  }
  aboutToRecycle() {
    console.info(`ReusableChild [${this.label}] aboutToRecycle`);
  }
  aboutToReuse() {
    console.info(`ReusableChild [${this.label}] aboutToReuse`);
  }

  build() {
    Text(`ReusableChild: ${this.label}`)
  }
}

@Entry
@ComponentV2
struct Index {
  @Local showA: boolean = true;
  @Local showB: boolean = true;

  build() {
    Column() {
      if (this.showA) {
        ReusableChild({ label: 'A' })
          .reuse({ reuseId: () => 'A' })
      }
      if (this.showB) {
        ReusableChild({ label: 'B' })
          .reuse({ reuseId: () => 'B' })
      }
      Button('Recycle A')
        .onClick(() => {
          // 切换if分支，触发子组件回收
          this.showA = false;
        })
      Button('Recycle B')
        .onClick(() => {
          // 切换if分支，触发子组件回收
          this.showB = false;
        })
      Button('Clear All')
        .onClick(() => {
          // 清理默认复用池中的全部组件
          UIUtils.getCustomComponentContext(this).getDefaultReusePool?.()?.clearCache();
        })
      Button('Clear A')
        .onClick(() => {
          // 仅清理reuseId为'A'的组件
          UIUtils.getCustomComponentContext(this).getDefaultReusePool?.()?.clearCache('A');
        })
    }
  }
}
```
