# @ohos.atomicservice.NavPushPathHelper(Defines provides a push method for the target page in the routing table.)

###### 子组件
 无
 ###### 属性
 不支持通用属性。
 ###### 事件
 不支持通用事件


## 导入模块

```TypeScript
import { NavPushPathHelper } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [NavPushPathHelper(Defines provides a push method for the target page in the routing table.)](arkts-arkui-atomicservice-navpushpathhelper-navpushpathhelper-c.md) | 当跳转的目标NavDestination在不同的hsp分包且未被主包依赖时，首次运行原子化服务只会下载安装主包。此时需要使用 NavPushPathHelper先下载安装相应hsp分包，再将指定的NavDestination页面信息入栈或替换当前栈顶页面，从 而使Navigation支持动态加载hsp分包后再跳转。 |
