# enable

## enable

```TypeScript
function enable(isEnable: boolean): void
```

使能ArkTS对象泄漏检测，默认关闭。开启后会收集泄漏信息，可能增加性能开销。

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**废弃版本：** -1

<!--Device-jsLeakWatcher-function enable(isEnable: boolean): void--><!--Device-jsLeakWatcher-function enable(isEnable: boolean): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnable | boolean | 是 | 是否使能jsLeakWatcher。true：使能jsLeakWatcher；false：不使能jsLeakWatcher。 |

## 示例

```TypeScript
jsLeakWatcher.enable(true);
```

