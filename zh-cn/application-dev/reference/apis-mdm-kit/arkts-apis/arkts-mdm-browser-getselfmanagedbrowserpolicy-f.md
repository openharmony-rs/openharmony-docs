# getSelfManagedBrowserPolicy

## 导入模块

```TypeScript
import { browser } from '@kit.MDMKit';
```

## getSelfManagedBrowserPolicy

```TypeScript
function getSelfManagedBrowserPolicy(): ArrayBuffer
```

获取当前设备浏览器策略。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-browser-function getSelfManagedBrowserPolicy(): ArrayBuffer--><!--Device-browser-function getSelfManagedBrowserPolicy(): ArrayBuffer-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 浏览器策略。 |

**示例：**

```TypeScript
import { browser } from '@kit.MDMKit';
import { util } from '@kit.ArkTS';

try {
  let buffer: ArrayBuffer = browser.getSelfManagedBrowserPolicy();
  let intBuffer: Uint8Array = new Uint8Array(buffer);
  let decoder: util.TextDecoder = util.TextDecoder.create('utf-8');
  let stringData: string = decoder.decodeToString(intBuffer);
  console.info(`Succeeded in getting self managed browser policy, result : ${stringData}`);
} catch(err) {
  console.error(`Failed to get self managed browser policy. Code is ${err.code}, message is ${err.message}`);
}

```

