# IMonitor

当监听的状态变量变化时，状态管理框架侧将回调开发者注册的函数，并传入变化信息。变化信息的类型为IMonitor。

**起始版本：** 12

<!--Device-unnamed-declare interface IMonitor--><!--Device-unnamed-declare interface IMonitor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## value

```TypeScript
value<T>(path?: string): IMonitorValue<T> | undefined
```

获取指定path的变化信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-IMonitor-value<T>(path?: string): IMonitorValue<T> | undefined--><!--Device-IMonitor-value<T>(path?: string): IMonitorValue<T> | undefined-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 否 | 被监听的状态变量路径名。未指定时默认使用变化路径数组dirty中的第一个路径。从API版本26.0.0开始，默认使用dirty中第一个非通配符路径。 当指定路径为通配符路径时，返回undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IMonitorValue](arkts-arkui-imonitorvalue-i.md)&lt;T&gt; |  |

**示例**

```TypeScript
@ObservedV2
class Info {
  @Trace name: string = 'Tom';
  @Trace age: number = 25;
  @Trace height: number = 175;

  // 监听一个变量
  @Monitor('name')
  onNameChange(monitor: IMonitor) {
    // 未指定value的入参时，默认使用dirty中的第一个路径作为入参
    console.info(`path: ${monitor.value()?.path} change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }

  // 监听多个变量
  @Monitor('age','height')
  onRecordChange(monitor: IMonitor) {
    // 指定value的入参时，将返回入参路径path对应的变量变化值信息
    monitor.dirty.forEach((path: string) => {
      console.info(`path: ${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
    })
  }
}

@Entry
@ComponentV2
struct Index {
  @Local info: Info = new Info();

  build() {
    Column() {
      Text(`info.name: ${this.info.name}`)
        .onClick(() => {
          this.info.name = 'Bob'; // 输出日志：path: name change from Tom to Bob
        })
      Text(`info.age: ${this.info.age}, info.height: ${this.info.height}`)
        .onClick(() => {
          this.info.age++; // 输出日志：path: age change from 25 to 26
          this.info.height++; // 输出日志：path: height change from 175 to 176
        })
    }
  }
}
```

## dirty

```TypeScript
dirty: Array<string>
```

被监听的状态变量中发生变化的属性路径数组，路径格式与@Monitor装饰器指定的状态变量名路径一致，支持点号分隔的嵌套属性路径（如'a.b.c'）。从API版本26.0.0开始，当通配符能力开启时，该数组中可能包含通配符路径， 通过[value](#value)()方法查询通配符路径将返回undefined。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-IMonitor-dirty: Array<string>--><!--Device-IMonitor-dirty: Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

