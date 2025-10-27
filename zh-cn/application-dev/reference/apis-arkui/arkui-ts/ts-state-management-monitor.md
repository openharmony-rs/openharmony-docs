# @Monitor

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 12开始，支持该装饰器。

@Monitor用于用于状态管理V2中，监听状态变量修改，使得状态变量具有深度监听的能力。

在ArkTS-Dyn中使用时，开发指南参考：[@Monitor装饰器：状态变量修改监听（ArkTS-Dyn）](../../../ui/state-management/arkts-new-monitor.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型     | 必填 | 说明                                         |
| ------ | -------- | ---- | -------------------------------------------- |
| path   | string[] | 是   | 用于设置对象属性名，可同时监听多个对象属性。 |

**示例：**

```ts
@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello World';
  @Local name: string = 'Tom';
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
          this.message += '!';
          this.name = 'Jack';
        })
    }
  }
}
```

