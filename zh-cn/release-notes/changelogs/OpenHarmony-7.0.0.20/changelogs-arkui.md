# ArkUI子系统变更说明

## cl.arkui.1 @ReusableV2组件复用的reuse属性支持动态复用标识

**访问级别**

公共能力

**变更原因**

当前[@ReusableV2](../../../application-dev/ui/state-management/arkts-new-reusableV2.md)装饰器装饰的自定义组件的reuse属性不支持使用动态的reuseId，变更后可增强V2组件复用能力，支持动态复用标识。

**变更影响**

此变更为不兼容变更，涉及应用适配。

- 变更前：如果开发者使用了如下所示等非显式返回字符串字面量形式的reuseId，实际的复用标识ID为该可复用自定义组件的名称。

- 变更后：如果开发者使用了下述形式的reuseId，实际的复用标识ID为该回调的返回值。

```ts
const globalReuseId: string = 'globalReuseId';
@Entry
@ComponentV2
struct Index {
  getReuseIdInMethod(idNumber: number): string {
    return `reuseIdInMethod${idNumber}`;
  }
  build() {
    Column() {
      ReusableV2Component()
        // 变更前实际复用标识为自定义组件名称"ReusableV2Component"
        // 变更后实际复用标识为"globalReuseId"
        .reuse({reuseId: () => globalReuseId})
      ReusableV2Component()
        // 变更前实际复用标识为自定义组件名称"ReusableV2Component"
        // 变更后实际复用标识为"reuseIdInMethod1"
        .reuse({reuseId: () => this.getReuseIdInMethod(1)})
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  build() {
    Column() {
      Text('ReusableV2Component')
    }
  }
}
```

**起始 API Level**

18

**变更发生版本**

从OpenHarmony SDK 7.0.0.20开始。

**变更的接口/组件**

涉及接口：[ReuseOptions](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-reuse.md#reuseoptions)里的reuseId参数。

变更前后会受到影响的组件为@ReusableV2装饰器装饰的自定义组件。该变更可能导致：

- 原本可以相互复用的自定义组件无法再相互复用：
  ```ts
  @Entry
  @ComponentV2
  struct Index {
    getReuseIdInMethod(idNumber: number): string {
      return `reuseIdInMethod${idNumber}`;
    }
  
    build() {
      Column() {
        // 变更后，在API版本26.0.0及以上，下述两个ReusableComponentOne组件的实际复用标识不一致，无法相互复用。
        ReusableComponentOne()
          // 变更前实际复用标识为自定义组件名称"ReusableComponentOne"
          // 变更后实际复用标识为"reuseIdInMethod1"
          .reuse({reuseId: () => this.getReuseIdInMethod(1)})
        ReusableComponentOne()
          // 变更前实际复用标识为自定义组件名称"ReusableComponentOne"
          // 变更后实际复用标识为"reuseIdInMethod2"
          .reuse({reuseId: () => this.getReuseIdInMethod(2)})
      }
    }
  }
  @ReusableV2
  @ComponentV2
  struct ReusableComponentOne {
    build() {
      Column() {
        Text('ReusableComponentOne')
      }
    }
  }
  ```

- 原本不可以相互复用的自定义组件可以相互复用：
  ```ts
  @Entry
  @ComponentV2
  struct Index {
    getReuseIdInMethod(idNumber: number): string {
      return `reuseIdInMethod${idNumber}`;
    }

    build() {
      Column() {
        // 变更后，在API版本26.0.0及以上ReusableComponentOne和ReusableComponentTwo组件实际复用标识一致，可以相互复用
        ReusableComponentOne()
          // 变更前实际复用标识为自定义组件名称"ReusableComponentOne"
          // 变更后实际复用标识为"reuseIdInMethod1"
          .reuse({reuseId: () => this.getReuseIdInMethod(1)}) 
        ReusableComponentTwo()
          // 变更前实际复用标识为自定义组件名称"ReusableComponentTwo"
          // 变更后实际复用标识为"reuseIdInMethod1"
          .reuse({reuseId: () => this.getReuseIdInMethod(1)})
      }
    }
  }
  @ReusableV2
  @ComponentV2
  struct ReusableComponentOne {
    build() {
      Column() {
        Text('ReusableComponentOne')
      }
    }
  }
  @ReusableV2
  @ComponentV2
  struct ReusableComponentTwo {
    build() {
      Column() {
        Text('ReusableComponentTwo')
      }
    }
  }
  ```

**适配指导**

对于不希望相互复用的V2复用组件，使用不同的复用标识reuseId；对于希望相互复用的组件，使用相同的复用标识reuseId。例如，当希望如下两个组件ComponentA和ComponentB组件可以相互复用时，设置同样的复用标识。点击按钮让两个组件消失，二者进入同一复用池中，可以相互复用。再次点击任一按钮，后进入复用池的组件先显示到页面上：

```ts
const globalReuseId = 'globalReuseId';
@Entry
@ComponentV2
struct Index {
  @Local condition1: boolean = true;
  @Local condition2: boolean = true;
  build() {
    Column({ space: 10 }) {
      // 变更后，在API版本26.0.0及以上ComponentA和ComponentB组件实际复用标识一致，均为'globalReuseId'，可以相互复用。
      Button('change condition1')
        .onClick(() => { this.condition1 = !this.condition1; })
      Button('change condition2')
        .onClick(() => { this.condition2 = !this.condition2; })
      if (this.condition1) {
        ComponentA().reuse({ reuseId: () => globalReuseId })
      }
      if (this.condition2) {
        ComponentB().reuse({ reuseId: () => globalReuseId })
      }
    }
  }
}
@ReusableV2
@ComponentV2
struct ComponentA {
  build() {
    Column() {
      Text('ComponentA')
    }
  }
}
@ReusableV2
@ComponentV2
struct ComponentB {
  build() {
    Column() {
      Text('ComponentB')
    }
  }
}
```