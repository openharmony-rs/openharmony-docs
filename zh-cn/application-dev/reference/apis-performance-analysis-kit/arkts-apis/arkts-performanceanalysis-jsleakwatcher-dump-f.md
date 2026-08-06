# dump

## dump

```TypeScript
function dump(filePath: string): Array<string>
```

����й©�б���������ڴ���ա�

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为26.1.0。

<!--Device-jsLeakWatcher-function dump(filePath: string): Array<string>--><!--Device-jsLeakWatcher-function dump(filePath: string): Array<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | ������Ϣ���ɵ��ļ���ŵ�·����\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**˵��**����API version 24��ʼ���������������ڣ����������µ�һ�ݿ�����Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | ����������ֱ�Ϊ�ļ�����׺Ϊ.jsleaklist��й©�б����ļ�����׺Ϊ.heapsnapshot������ڴ�����ļ��� |

**示例：**

```TypeScript
let context = this.getUIContext().getHostContext();
let files: Array<string> = jsLeakWatcher.dump(context?.filesDir);
```

