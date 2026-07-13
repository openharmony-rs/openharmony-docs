# getRssInfo

## getRssInfo

```TypeScript
function getRssInfo(): RssInfo
```

��ȡӦ�ó�����̵������ڴ�ʹ����Ϣ����ȡ/proc/{pid}/status�ڵ�����ݡ�

> **ע��**
>
> ��ȡ/proc/{pid}/status��ʱ�̣ܶ���hidebug.getAppNativeMemInfo�ӿ��л�ȡ��`rss`ֵ��ȴ���һ�������ýӿڸ���������Ϊ����Ӧ�ö�֡�򿨶��Ƽ�ʹ�øýӿڡ�

**起始版本：** 24

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RssInfo | Ӧ�ý��̵������ڴ���Ϣ�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let rssInfo: hidebug.RssInfo = hidebug.getRssInfo();
console.info(`rss: ${rssInfo.rss}, swapRss: ${rssInfo.swapRss}`);

```

