# scanFile

## scanFile

```TypeScript
function scanFile(filePath: string, identifyPolicies: Array<Policy>): Promise<Array<MatchResult>>
```

根据设置的策略，识别指定文件中的敏感内容，返回识别的结果数组，包含匹配的敏感标签、匹配内容及匹配数量。使用Promise异步回调。

**起始版本：** 21

**需要权限：** ohos.permission.ENTERPRISE_DATA_IDENTIFY_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 识别的文件路径，需使用物理路径，路径指向的文件必须存在且支持访问。 |
| identifyPolicies | Array&lt;Policy&gt; | 是 | 用于识别敏感内容的策略数组。每个Policy定义识别规则（标签、关键字、正则表达式），系统将根据这些规则扫描文件内容并返回匹配结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;MatchResult&gt;&gt; | Promise对象，返回敏感内容识别的结果。成功时返回匹配结果数组，异常返回错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission) | permission denied. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [19110001](../../errorcode-universal.md#19110001-Parameter) | Parameter error. Possible causes:<br/>1. Incorrect policy format.<br/>2. Invalid parameter range. |
| [19110002](../../errorcode-universal.md#19110002-Sensitive) | Sensitive file content identification timed out. |
| [19110003](../../errorcode-universal.md#19110003-The) | The file is not supported. Possible causes:<br/>1. The file path does not exist.<br/>2. The file type is not supported.<br/>3. The file permission is not supported. |
| [19110004](../../errorcode-universal.md#19110004-A) | A system error has occurred. |

**示例：**

```TypeScript
// 导入敏感内容识别模块
import { identifySensitiveContent } from '@kit.DataProtectionKit';

// 定义待扫描的文件物理路径
let filepath = "/data/app/el1/bundle/public/bundleName/test.txt";

// 配置敏感内容识别策略
let policies: Array<identifySensitiveContent.Policy> = [
  {"sensitiveLabel":"1", "keywords":[], "regex":""}
];
try {
  // 调用scanFile接口识别文件中的敏感内容
  identifySensitiveContent.scanFile(filepath, policies).then(records => {
    // 处理识别结果
    console.info('scanFile finish');
  }).catch((err:Error) => {
    // 处理识别失败
    console.error('error message', err.message);
  })
} catch (err) {
  // 捕获异常
  console.error('error message', err.message);
}

```

