# Repeat

Repeat基于数组类型数据来进行循环渲染，一般与滚动容器组件配合使用。

本文档仅为API参数说明。组件描述和使用说明见[Repeat开发者指南](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)。

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RepeatItem](arkts-arkui-repeat-comp-repeatitem-i.md) | 数据项类型。 |
| [RepeatOptions](arkts-arkui-repeat-comp-repeatoptions-i.md) | 创建Repeat组件时的配置项。 |
| [TemplateOptions](arkts-arkui-repeat-comp-templateoptions-i.md) | 当cachedCount值被设置为当前template在容器组件显示区域的最大节点数量时，Repeat会做到最大程度的复用。当容器组件显示区域内没有当前template的节点时，缓存池不会释放，同时应用内存增大。开发者需要根据应用对内存占用和组件复用效率的需求自行调整，推荐cachedCount值设置为容器组件显示区域内节点个数。需要注意，不建议设置cachedCount小于2，这会导致在快速滑动场景下频繁创建新的节点，从而造成性能劣化。 |
| [VirtualScrollOptions](arkts-arkui-repeat-comp-virtualscrolloptions-i.md) | 配置懒加载模式下期望加载的数据项总数、复用能力、数据精准懒加载能力。从API版本26.0.0开始，支持配置内存优化策略。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [RepeatArray](arkts-arkui-repeat-comp-repeatarray-t.md) | Repeat数据源参数联合类型。 |
| [RepeatItemBuilder](arkts-arkui-repeat-comp-repeatitembuilder-t.md) | Repeat子组件构建器。 |
| [TemplateTypedFunc](arkts-arkui-repeat-comp-templatetypedfunc-t.md) | 模板类型生成函数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RepeatMemOptStrategy](arkts-arkui-repeat-comp-repeatmemoptstrategy-e.md) | Repeat内存优化策略枚举。 |

## 示例

### 示例1（使用自动内存优化策略）

以下示例中，通过[VirtualScrollOptions](arkts-arkui-repeat-comp-virtualscrolloptions-i.md)的memoryOptimizationStrategy属性使用了自动内存优化策略。点击Scroll按钮，使列表跳转，旧节点进入缓存池。应用退后台时，清理缓存。应用恢复前台时，恢复缓存。

从API版本26.0.0开始，VirtualScrollOptions新增memoryOptimizationStrategy属性。

```TypeScript
@ComponentV2
struct ChildComponent {
  aboutToAppear() {
    console.info('ChildComponent aboutToAppear');
  }
  aboutToDisappear() {
    console.info('ChildComponent aboutToDisappear');
  }
  build() {
    Text('ChildComponent')
  }
}

@Entry
@ComponentV2
struct MemoryOptimizeDemo {
  @Local data: Array<number> = [];
  private scroller: Scroller = new Scroller();
  aboutToAppear() {
    for (let i = 0; i < 100; i++) {
      this.data.push(i);
    }
  }
  build() {
    Column() {
      Button('Scroll').onClick(() => { // 点击按钮触发列表跳转，旧组件进入缓存池
        this.scroller.scrollToIndex(30);
      })
      List({ scroller: this.scroller }) {
        Repeat<number>(this.data)
          .each((repeatItem: RepeatItem<number>) => {
            ListItem() {
              ChildComponent()
            }
          })
          .virtualScroll({ memoryOptimizationStrategy: RepeatMemOptStrategy.ENABLE_AUTO_CACHE_OPTIMIZATION }) // 使用自动内存优化策略
      }
      .cachedCount(5)
    }
  }
}
```

### 示例2（主动清理缓存池）

以下示例中，通过[RepeatOptions](arkts-arkui-repeat-comp-repeatoptions-i.md)的controller属性绑定了[RepeatController](#repeatcontroller)。点击Scroll按钮，使列表跳转，旧组件进入缓存池。然后点击Clear按钮，主动清理Repeat缓存池中的组件。

从API版本26.1.0开始，Repeat接口新增options参数。

```TypeScript
@ComponentV2
struct ChildComponent {
  aboutToAppear() {
    console.info('ChildComponent aboutToAppear');
  }
  aboutToDisappear() {
    console.info('ChildComponent aboutToDisappear');
  }
  build() {
    Text('ChildComponent')
  }
}

@Entry
@ComponentV2
struct ClearCacheDemo {
  @Local data: Array<number> = [];
  // 创建RepeatController对象
  private controller: RepeatController = new RepeatController();
  private scroller: Scroller = new Scroller();

  aboutToAppear(): void {
    for (let i = 0; i < 100; i++) {
      this.data.push(i);
    }
  }

  build() {
    Column() {
      List({ scroller: this.scroller }) {
        // 通过RepeatOptions的controller字段绑定控制器
        Repeat<number>(this.data, { controller: this.controller })
          .each((repeatItem: RepeatItem<number>) => {
            ListItem() {
              ChildComponent()
            }
          })
          .virtualScroll()
      }
      .cachedCount(5)
      .height('80%')

      Button('Scroll')
        .onClick(() => {
          // 点击按钮触发列表跳转，旧组件进入缓存池
          this.scroller.scrollToIndex(30);
        })

      Button('Clear')
        .onClick(() => {
          // 主动清理Repeat缓存池中的组件
          this.controller.clearCache();
        })
    }
  }
}
```
