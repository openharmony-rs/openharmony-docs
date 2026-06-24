# getAllShortcutInfoForSelf

## getAllShortcutInfoForSelf

```TypeScript
function getAllShortcutInfoForSelf(): Promise<Array<ShortcutInfo>>
```

��ѯ��ǰӦ��[�����ļ�](../../../../quick-start/module-configuration-file.md#shortcuts��ǩ)�ж�������п�ݷ�ʽ��Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ShortcutInfo&gt;&gt; | Promise���󣬷���Ӧ�������ļ��ж�������п�ݷ�ʽ��Ϣ�� |

**示例：**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

shortcutManager.getAllShortcutInfoForSelf()
  .then((data: shortcutManager.ShortcutInfo[]) => {
    console.info('getAllShortcutInfoForSelf shortcut data is' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
  console.error(`getAllShortcutInfoForSelf errData is errCode:${err.code}  message:${err.message}`);
});

```

