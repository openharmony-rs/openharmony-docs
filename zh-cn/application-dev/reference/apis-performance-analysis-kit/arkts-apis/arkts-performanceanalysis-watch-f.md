# watch

## watch

```TypeScript
function watch(obj: object, msg: string): void
```

ע������й©�Ķ���

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | object | 是 | ��Ҫ���Ķ���<br>**˵��**���ɴ����κη�null��ArkTS���󣬲�֧��undefined�ͻ������͡� |
| msg | string | 是 | �Զ��������Ϣ�� |

**示例：**

```TypeScript
let obj:Object = new Object();
jsLeakWatcher.watch(obj, "Trace Object");

```

