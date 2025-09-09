# @ohos.multimodalInput.inputConsumer (全局快捷键)(系统接口)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

全局快捷键订阅模块，用于处理组合按键的订阅。

> **说明：**
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口为系统接口。
>
> - 本模块接口仅对系统快捷键生效，系统快捷键指系统定义的全局快捷键。


## 导入模块

```js
import { inputConsumer } from '@kit.InputKit';
```

## inputConsumer.on

on(type: 'key', keyOptions: KeyOptions, callback: Callback&lt;KeyOptions&gt;): void

订阅系统快捷键，当满足条件的组合按键输入事件发生时，使用Callback异步方式上报组合按键数据。

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：** 

| 参数名         | 类型                         | 必填   | 说明                                       |
| ---------- | -------------------------- | ---- | ---------------------------------------- |
| type       | string                     | 是    | 事件类型，目前仅支持'key'。                       |
| keyOptions | [KeyOptions](#keyoptions)  | 是    | 组合键选项。                 |
| callback   | Callback&lt;KeyOptions&gt; | 是    | 回调函数，当满足条件的组合按键输入事件发生时，异步上报组合按键数据。 |

**示例：** 

```js
import { inputConsumer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let leftAltKey = 2045;
          let tabKey = 2049;
          let keyOptions: inputConsumer.KeyOptions = {
            preKeys: [ leftAltKey ],
            finalKey: tabKey,
            isFinalKeyDown: true,
            finalKeyDownDuration: 0
          };
          let callback = (keyOptions: inputConsumer.KeyOptions) => {
            console.log(`keyOptions: ${JSON.stringify(keyOptions)}`);
          }
          try {
            inputConsumer.on("key", keyOptions, callback);
          } catch (error) {
            console.error(`Subscribe failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```


## inputConsumer.off

off(type: 'key', keyOptions: KeyOptions, callback?: Callback&lt;KeyOptions&gt;): void

取消订阅系统快捷键。

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：** 

| 参数名         | 类型                         | 必填   | 说明                              |
| ---------- | -------------------------- | ---- | ------------------------------- |
| type       | string                     | 是    | 事件类型，当前仅支持 'key'。              |
| keyOptions | [KeyOptions](#keyoptions)  | 是    | 组合键选项。             |
| callback   | Callback&lt;KeyOptions&gt; | 否    | 需要取消订阅的回调函数。若不填，则取消当前应用组合键选项已订阅的所有回调函数。 |

**示例：** 

```js
import { inputConsumer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let leftAltKey = 2045;
          let tabKey = 2049;
          // 取消订阅单个回调函数
          let callback = (keyOptions: inputConsumer.KeyOptions) => {
            console.log(`keyOptions: ${JSON.stringify(keyOptions)}`);
          }
          let keyOption: inputConsumer.KeyOptions = {preKeys: [leftAltKey], finalKey: tabKey, isFinalKeyDown: true, finalKeyDownDuration: 0};
          try {
            inputConsumer.on("key", keyOption, callback);
            inputConsumer.off("key", keyOption, callback);
            console.log(`Unsubscribe success`);
          } catch (error) {
            console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```
```js
import { inputConsumer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let leftAltKey = 2045;
          let tabKey = 2049;
          // 取消订阅所有回调函数
          let callback = (keyOptions: inputConsumer.KeyOptions) => {
            console.log(`keyOptions: ${JSON.stringify(keyOptions)}`);
          }
          let keyOption: inputConsumer.KeyOptions = {preKeys: [leftAltKey], finalKey: tabKey, isFinalKeyDown: true, finalKeyDownDuration: 0};
          try {
            inputConsumer.on("key", keyOption, callback);
            inputConsumer.off("key", keyOption);
            console.log(`Unsubscribe success`);
          } catch (error) {
            console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputConsumer.setShieldStatus<sup>11+</sup>

setShieldStatus(shieldMode: ShieldMode, isShield: boolean): void

设置系统快捷键屏蔽类型。

**需要权限**: ohos.permission.INPUT_CONTROL_DISPATCHING

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：** 

| 参数名         | 类型                         | 必填   | 说明                                       |
| ---------- | -------------------------- | ---- | ---------------------------------------- |
| shieldMode       | [ShieldMode](js-apis-inputconsumer-sys.md#shieldmode11)                     | 是    | 系统快捷键屏蔽类型，目前仅支持取值为'FACTORY_MODE'，表示屏蔽所有系统快捷键。                       |
| isShield | boolean  | 是    | 屏蔽类型生效状态，true代表屏蔽类型生效，flase代表不生效。              |

**示例：** 

```js
import { inputConsumer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let FACTORY_MODE = 0;
          try {
            inputConsumer.setShieldStatus(FACTORY_MODE,true);
            console.log(`set shield status success`);
          } catch (error) {
            console.error(`set shield status failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputConsumer.getShieldStatus<sup>11+</sup>

getShieldStatus(shieldMode: ShieldMode): boolean

获取系统快捷键屏蔽类型。

**需要权限**: ohos.permission.INPUT_CONTROL_DISPATCHING

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：** 

| 参数名         | 类型                         | 必填   | 说明                                       |
| ---------- | -------------------------- | ---- | ---------------------------------------- |
| shieldMode       | [ShieldMode](js-apis-inputconsumer-sys.md#shieldmode11)                    | 是    | 系统快捷键屏蔽类型，目前仅支持取值为'FACTORY_MODE'，表示屏蔽所有系统快捷键。                       |

**返回值：** 

| 类型         |  说明                                       |
| ---------- |  ---------------------------------------- |
| boolean                    | 屏蔽类型生效状态，true代表屏蔽类型生效，flase代表不生效。                       |

**示例：** 

```js
import { inputConsumer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let FACTORY_MODE = 0;
            let shieldstatusResult:Boolean =  inputConsumer.getShieldStatus(FACTORY_MODE);
            console.log(` get shield status result:${JSON.stringify(shieldstatusResult)}`);
          } catch (error) {
            console.error(`Failed to get shield status, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## KeyOptions

组合键选项。

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

| 名称        | 类型   | 只读   | 可选   | 说明      |
| --------- | ------ | ---- | ---- | ------- |
| preKeys    | Array\<number>   | 否    | 否 | 前置按键集合，数量范围[0, 4]，前置按键无顺序要求。<br>如组合按键Ctrl+Alt+A中，Ctrl+Alt称为前置按键。 |
| finalKey             | number  | 否    |  否 | 最终按键，此项必填，最终按键触发上报回调函数。<br>如组合按键Ctrl+Alt+A中，A称为最终按键按键。 |
| isFinalKeyDown       | boolean | 否    |  否 | 最终按键状态。<br>ture表示按键按下，false表示按键抬起。 |
| finalKeyDownDuration | number  | 否    |  否 | 最终按键保持按下持续时间，单位：μs。<br>当finalKeyDownDuration为0时，立即触发回调函数。<br>当finalKeyDownDuration大于0时，isFinalKeyDown为true，则最终按键按下超过设置时长后触发回调函数；isFinalKeyDown为false，则最终按键按下到抬起时间小于设置时长时触发回调函数。   |
| isRepeat<sup>18+</sup> | boolean  | 否      | 否      | 是否上报重复的按键事件。true表示上报，false表示不上报，若不填默认为true。 |

## shieldMode<sup>11+</sup>

系统快捷键屏蔽类型。

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

| 名称                        | 值 | 说明           |
| ------------------------------ | ----------- | ---------------- |
| UNSET_MODE | -1 | 值为-1，表示不屏蔽系统快捷键。 |
| FACTORY_MODE | 0 | 值为0，表示屏蔽所有系统快捷键。 |
| OOBE_MODE | 1 | 值为1，表示OOBE阶段屏蔽所有系统快捷键，暂不支持该能力。 |