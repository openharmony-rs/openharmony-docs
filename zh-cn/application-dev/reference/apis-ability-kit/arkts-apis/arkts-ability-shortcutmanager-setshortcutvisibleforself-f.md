# setShortcutVisibleForSelf

## setShortcutVisibleForSelf

```TypeScript
function setShortcutVisibleForSelf(id: string, visible: boolean): Promise<void>
```

���õ�ǰӦ��ָ���Ŀ�ݷ�ʽ�Ƿ���ʾ��ʹ��Promise�첽�ص���

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | ��ݷ�ʽ��ID��ͨ��[module.json5�����ļ�](../../../../quick-start/module-configuration-file.md)�е�shortcuts��<br/>ǩ�µ�shortcutId�ֶλ�ȡ��ȡֵΪ���Ȳ�����63�ֽڵ��ַ����� |
| visible | boolean | 是 | ��ݷ�ʽ�Ƿ���ʾ��true����ݷ�ʽ��ʾ��false����ݷ�ʽ����ʾ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17700070](../../errorcode-universal.md#17700070-The) | The specified shortcut id is not exist. |

**示例：**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 请替换为module.json5配置文件中的shortcuts标签下实际配置的shortcutId字段
shortcutManager.setShortcutVisibleForSelf("shortcut_id", false)
  .then(() => {
    console.info('setShortcutVisibleForSelf success');
  }).catch((err: BusinessError) => {
  console.error(`setShortcutVisibleForSelf errData is errCode:${err.code}  message:${err.message}`);
});

```

