# @ohos.arkui.Parallelize (UI并行化创建)

提供声明式的并行化创建方法ParallelizeUI。ParallelizeUI方法内部的UI在子线程中创建，创建完成后，回到主线程完成树的挂载，后续更新、事件等操作都在主线程中进行。

> **说明：**
> - 本模块接口从API version 20开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
> - 本模块仅适用于ArkTS1.2。

## 导入模块

```ts
import { ParallelOption, ParallelizeUI } from '@ohos.arkui.Parallelize';
```

## ParallelOption

使用ParallelizeUI并行化创建UI时的可选参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**参数：**

| 名称      | 类型     | 只读 | 可选 | 说明                |
| -------- | -------- | --- |-----|--------------------- |
| enable   | boolean  | 否   | 是| 是否开启UI创建并行化。其中，false表示不开启并行化创建，true表示开启并行化创建。<br/>默认值：true  |



## ParallelizeUI
声明式的并行化创建UI方法。

ParallelizeUI(options?: ParallelOption | undefined, content?: CustomBuilder)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**参数：**

| 参数名  | 类型     | 必填 | 说明                                                           |
| ------ | -------- | ---- | ------------------------------------------------------------ |
| options  | ParallelOption \| undefined | 否   | 使用ParallelizeUI方法创建组件时的可选参数。<br/>默认值：undefined |
| content  | CustomBuilder | 否   | 自定义UI描述，通过尾随闭包的形式传入。 |

## 示例

```ts
import { ParallelOption, ParallelizeUI } from '@ohos.arkui.Parallelize';

@Component
struct Index {
  @State count1:number = 0
  build() {
    Column() {
      ParallelizeUI() {
        Text("并行执行")
      }
      ParallelizeUI({enable:false}) {
        Text("串行执行")
      }
      Text("串行执行")
      ParallelizeUI({}) {
        Button("并行执行")
      }
    }.height('100%').width('100%')
  }
}

```