# getCfgDirListSync（系统接口）

## 导入模块

```TypeScript
import { configPolicy } from '@kit.BasicServicesKit';
```

<a id="getcfgdirlistsync"></a>
## getCfgDirListSync

```TypeScript
function getCfgDirListSync(): Array<string>
```

获取配置层级目录列表，按优先级从低到高。

**起始版本：** 11

<!--Device-configPolicy-function getCfgDirListSync(): Array<string>--><!--Device-configPolicy-function getCfgDirListSync(): Array<string>-End-->

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回配置层级目录列表。 |

