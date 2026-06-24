# cancelRetentionState

## cancelRetentionState

```TypeScript
function cancelRetentionState(docUris: Array<string>): Promise<void>
```

取消沙箱保留状态即恢复DLP文件关闭时自动卸载沙箱策略。使用Promise异步回调。

该接口用于取消沙箱保留状态，恢复默认行为以释放系统资源，适用于不再频繁访问DLP文件的场景。

**起始版本：** 10

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| docUris | Array&lt;string&gt; | 是 | 表示需要取消保留状态的文件uri列表。不对Array长度进行限制，每个string长度范围[0, 4095]字节，超出此范围抛出错误码19100001。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
dlpPermission.cancelRetentionState([uri]).then(() => { // 取消沙箱保留。
  console.info('success!');
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});

```


## cancelRetentionState

```TypeScript
function cancelRetentionState(docUris: Array<string>, callback: AsyncCallback<void>): void
```

取消沙箱保留状态即恢复DLP文件关闭时自动卸载沙箱策略。使用callback异步回调。

该接口用于取消沙箱保留状态，恢复默认行为以释放系统资源，适用于不再频繁访问DLP文件的场景。

**起始版本：** 10

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| docUris | Array&lt;string&gt; | 是 | 表示需要取消保留状态的文件uri列表。不对Array长度进行限制，每个string不超过4095字节，超出此范围抛出错误码19100001。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。err为undefined时表示设置成功；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
dlpPermission.cancelRetentionState([uri], (err, res) => {
  if (err != undefined) {
    console.error('cancelRetentionState error,', err.code, err.message);
  } else {
    console.info('cancelRetentionState success');
  }
}); // 取消沙箱保留。

```

