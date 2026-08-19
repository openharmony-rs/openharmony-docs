# @ohos.atomicservice.InterstitialDialogAction

## 导入模块

```TypeScript
import { InterstitialDialogAction, IconStyle, TitlePosition, BottomOffset } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [InterstitialDialogAction](arkts-arkui-atomicservice-interstitialdialogaction-interstitialdialogaction-c.md) | InterstitialDialogAction弹框在原子化服务中用于在保持当前的上下文环境时，临时展示用户需关注的信息或待处理的操作，用户点击弹框的不同区域可以触发对应的回调动作。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DialogOptions](arkts-arkui-atomicservice-interstitialdialogaction-dialogoptions-i.md) | 设置弹框特有的属性以及提供给用户自定义的点击触发动作。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BottomOffset](arkts-arkui-atomicservice-interstitialdialogaction-bottomoffset-e.md) | 设置不同情景模式下弹框距离底部的距离，判断依据为是否存在菜单栏，默认显示为不存在菜单栏情况下的距离。 \| 名称 \| 值 \| 说明 \| \| - \| - \| - \| \| OFFSET_FOR_BAR \| 0 \| 存在菜单栏情况下与窗口底部的距离。设置后弹框距离底部88vp。 \| \| OFFSET_FOR_NONE \| 1 \| 不存在菜单栏情况下与窗口底部的距离。默认值，设置后弹框距离底部44vp。 \| |
| [IconStyle](arkts-arkui-atomicservice-interstitialdialogaction-iconstyle-e.md) | 设置关闭按钮的色调样式，默认为亮色调。 \| 名称 \| 值 \| 说明 \| \| - \| - \| - \| \| DARK \| 0 \| 设置关闭按钮为暗色调。 \| \| LIGHT \| 1 \| 设置关闭按钮为亮色调。默认值。 \| |
| [TitlePosition](arkts-arkui-atomicservice-interstitialdialogaction-titleposition-e.md) | 设置主副标题之间的上下相对位置，默认设置为主标题在副标题之上。 \| 名称 \| 值 \| 说明 \| \| - \| - \| - \| \| TOP \| 0 \| 设置主标题位于副标题之上。默认值。 \| \| BOTTOM \| 1 \| 设置主标题位于副标题之下。 \| |

