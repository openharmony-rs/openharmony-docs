# @SyncMonitor

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @zhangboren-->
<!--TSE: @TerryTsao-->

@SyncMonitor用于状态管理V2中，同步监听状态变量修改，使得状态变量具有深度监听的能力。开发指南参考：[\@SyncMonitor装饰器：状态变量修改同步监听](../../../ui/state-management/arkts-new-syncmonitor.md)。

> **说明：**
>
> 本模块仅适用于ArkTS-Dyn。
>
> 该装饰器从API version 23开始支持。

## @SyncMonitor

const SyncMonitor: MonitorDecorator

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型     | 说明                                         |
| -------- | -------------------------------------------- |
| [MonitorDecorator](./ts-state-management-watch-monitor.md#monitordecorator12) | @SyncMonitor装饰器方法类型。 |

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
          this.message += '!'; // 修改message，同步触发onStrChange回调
          this.name = 'Jack'; // 修改name，同步触发onStrChange回调
        })
    }
  }
}
```
