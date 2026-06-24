# isShortcutSupported

## isShortcutSupported

```TypeScript
function isShortcutSupported(): boolean
```

��ѯ��ǰ�豸�Ƿ�֧�ֿ�ݷ�ʽ��

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ��ʾ��ǰ�豸�Ƿ�֧�ֿ�ݷ�ʽ��<br/>����ֵΪtrue��ʾ��ǰ�豸֧�ֿ�ݷ�ʽ������ֵΪfalse��ʾ��ǰ�豸��֧�ֿ�ݷ�ʽ�� |

**示例：**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = shortcutManager.isShortcutSupported();
  console.info('isShortcutSupported data is' + JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  console.error(`isShortcutSupported errData is errCode:${err.code}  message:${err.message}`);
}

```

