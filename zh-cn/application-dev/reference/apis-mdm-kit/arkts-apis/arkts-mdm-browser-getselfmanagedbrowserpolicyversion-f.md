# getSelfManagedBrowserPolicyVersion

## 导入模块

```TypeScript
import { browser } from '@kit.MDMKit';
```

<a id="getselfmanagedbrowserpolicyversion"></a>
## getSelfManagedBrowserPolicyVersion

```TypeScript
function getSelfManagedBrowserPolicyVersion(): string
```

获取指定浏览器的浏览器策略版本。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-browser-function getSelfManagedBrowserPolicyVersion(): string--><!--Device-browser-function getSelfManagedBrowserPolicyVersion(): string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 浏览器策略版本。 |

**示例：**

```TypeScript
import { browser } from '@kit.MDMKit';

try {
  let version: string = browser.getSelfManagedBrowserPolicyVersion();
  console.info(`Succeeded in getting self managed browser policy version, result : ${version}`);
} catch(err) {
  console.error(`Failed to get self managed browser policy version. Code is ${err.code}, message is ${err.message}`);
}

```

