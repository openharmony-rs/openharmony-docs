# FontClientObserver

```TypeScript
interface FontClientObserver
```

字体服务状态变化监听器。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Global.FontManager

## 导入模块

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## onServiceDied

```TypeScript
onServiceDied(): void
```

字体服务异常退出时的回调函数，应用可在此回调函数中执行资源清理或重新注册等操作。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Global.FontManager
