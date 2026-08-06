# watch

## watch

```TypeScript
function watch(obj: object, msg: string): void
```

ע������й©�Ķ���

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为26.1.0。

<!--Device-jsLeakWatcher-function watch(obj: object, msg: string): void--><!--Device-jsLeakWatcher-function watch(obj: object, msg: string): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | object | 是 | ��Ҫ���Ķ���\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**˵��**���ɴ����κη�null��ArkTS���󣬲�֧��undefined�ͻ������͡� |
| msg | string | 是 | �Զ��������Ϣ�� |

**示例：**

```TypeScript
let obj:Object = new Object();
jsLeakWatcher.watch(obj, "Trace Object");
```

