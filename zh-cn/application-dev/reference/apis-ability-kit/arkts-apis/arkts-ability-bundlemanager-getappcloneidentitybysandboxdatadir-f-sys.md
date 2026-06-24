# getAppCloneIdentityBySandboxDataDir（系统接口）

## getAppCloneIdentityBySandboxDataDir

```TypeScript
function getAppCloneIdentityBySandboxDataDir(sandboxDataDir: string): AppCloneIdentity
```

����Ӧ�õ�ɳ��Ŀ¼���ƻ�ȡӦ�õ�������Ϣ������Ӧ�ð����ͷ���������Ϣ��

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sandboxDataDir | string | 是 | ��ʾ[Ӧ�õ�ɳ��Ŀ¼](../../../../file-management/app-sandbox-directory.md)���ơ�<br/>**˵����** ������У��Ϸ��ԣ�������sandboxDataDir�����Ϸ���Ӧ�û�Ԫ�����Ŀ¼���Ƹ�ʽ����sandboxDataDir����Ϊ������Ϣ�е�AppCloneIdentity.bundleName���أ���ʱ<br/>AppCloneIdentity.appIndexΪ0��<br/>1.����Ӧ��Ŀ¼���Ƹ�ʽҪ��`+clone-{appIndex}+{bundleName}`��appIndex��bundleName�Ǳ�������Ӧ��������<br/>��Ӧ�ð��������磺 `+clone-1+com.example.myapplication`��<br/>2.Ԫ����Ŀ¼���Ƹ�ʽ��ʽҪ��`+auid-{uid}+{bundleName}`��uid��bundleName�Ǳ�<br/>������ӦӦ�ó����UID��Ӧ�ð��������磺 `+auid-20000000+com.example.myapplication`�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AppCloneIdentity | ����Ӧ�ð����ͷ���������Ϣ�� |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 主应用
let dataDir = 'com.example.myapplication';
try {
  let res = bundleManager.getAppCloneIdentityBySandboxDataDir(dataDir);
  hilog.info(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir successfully. res:%{public}s',
    JSON.stringify(res));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir failed. Cause: %{public}s',
    message);
}

// 分身应用
let cloneDataDir = '+clone-1+com.example.myapplication';
try {
  let res = bundleManager.getAppCloneIdentityBySandboxDataDir(cloneDataDir);
  hilog.info(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir successfully. res:%{public}s',
    JSON.stringify(res));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir failed. Cause: %{public}s',
    message);
}

// 原子化服务
let atomicDataDir = '+auid-20000000+com.example.myapplication';
try {
  let res = bundleManager.getAppCloneIdentityBySandboxDataDir(atomicDataDir);
  hilog.info(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir successfully. res:%{public}s',
    JSON.stringify(res));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneIdentityBySandboxDataDir failed. Cause: %{public}s',
    message);
}

```

