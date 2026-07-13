# @SyncMonitor：状态变量修改同步监听

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@SyncMonitor用于状态管理V2，同步监听状态变量修改，使得状态变量支持深度监听。适用于需要精确监听对象嵌套属性变化、数组元素修改等深层状态变化的场景，解决了传统监听方式无法感知深层属性变化的问题，提升状态管理的精确性和开发效率。

在ArkTS-Dyn中使用时，开发指南参考：[@SyncMonitor装饰器：状态变量修改同步监听](../../../ui/state-management/arkts-new-syncmonitor.md)。

> **说明：**
>
> 本模块仅适用于ArkTS-Dyn。
>
> 该装饰器从API version 23开始支持。

## @SyncMonitor

const SyncMonitor: MonitorDecorator

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

| 类型     | 说明                                         |
| -------- | -------------------------------------------- |
| [MonitorDecorator](./ts-state-management-watch-monitor.md#monitordecorator12) | @SyncMonitor装饰器类型。 |

**错误码：**

以下错误码的详细介绍请参见[状态管理错误码](../errorcode-stateManagement.md)。

| 错误码ID | 错误信息             |
| -------- | -------------------- |
| 130001   | The path is invalid. |

**示例：**

```ts
@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello World';
  @Local name: string = 'Tom';

  // 使用@SyncMonitor同时监听message和name的变化
  @SyncMonitor('message', 'name')
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
          // 修改message，同步触发onStrChange回调
          this.message += '!';
          // 修改name，同步触发onStrChange回调
          this.name = 'Jack';
        })
    }
  }
}
```
