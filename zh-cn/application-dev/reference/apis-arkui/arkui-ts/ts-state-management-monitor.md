# @Monitor：状态变量修改监听

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@Monitor装饰器在状态管理V2中用于监听状态变量修改，使得状态变量具有深度监听的能力。适用于需要在状态变量或其嵌套属性发生变化时执行自定义逻辑（如数据同步、UI刷新、日志记录等）的场景。相比状态管理V1的@Watch，@Monitor支持深度监听嵌套对象属性的变化，并从API版本26.0.0开始支持通配符能力，可更灵活地匹配变量路径。开发指南参考：[@Monitor装饰器：状态变量修改监听](../../../ui/state-management/arkts-new-monitor.md)。

> **说明：**
>
> 从API version 12开始，支持该装饰器。

## @Monitor

Monitor: MonitorDecorator

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型     | 必填 | 说明                                         |
| ------ | -------- | ---- | -------------------------------------------- |
| value  | string \| [MonitorDecoratorOptions](./ts-state-management-watch-monitor.md#monitordecoratoroptions) | 是   | 在API版本26.0.0之前，该参数为监听的变量名路径，支持通过点号分隔的方式指定嵌套对象属性的路径（如'a.b.c'）。当开发者仅传入一个字符串时，入参为string类型。从API版本26.0.0开始，该参数也可以为MonitorDecoratorOptions类型的对象，用于配置通配符能力（即支持使用通配符匹配多个变量名路径，实现对同类型变量的批量监听）。 |
| ...args   | string[] | 否   | 用于监听的变量名路径数组，内容由开发者指定。当开发者传入多个字符串时，入参为该类型。不传入此参数时，仅监听value参数指定的变量路径。 |

**示例：**

@Monitor装饰的回调函数接收一个[IMonitor](./ts-state-management-watch-monitor.md#imonitor12)接口类型的参数，用于获取状态变量变化信息。

```ts
@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello World';
  @Local name: string = 'Tom';
  // 使用@Monitor装饰器监听message和name变量的变化
  @Monitor('message', 'name')
  onStrChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      console.info(`${path} changed from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
    });
  }
  build() {
    Column() {
      Text(`message: ${this.message}`)
      Text(`name: ${this.name}`)
      Button('change string')
        .onClick(() => {
          // 触发@Monitor回调
          this.message += '!';
          this.name = 'Jack';
        })
    }
  }
}
```

