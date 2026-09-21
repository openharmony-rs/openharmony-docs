# FontScope

```TypeScript
enum FontScope
```

表示字体作用范围的枚举。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Global.FontManager

## APP

```TypeScript
APP = 0
```

应用级字体。字体的生命周期跟随应用的生命周期，应用退出或字体服务异常退出时，安装的字体文件会被自动清理\卸载。需先调用onFontObserver注册监听后才能安装。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Global.FontManager

## SESSION

```TypeScript
SESSION = 1
```

会话级字体。字体的生命周期不跟随应用的生命周期，设备重启或当前用户退出（多用户场景下）时，安装的字体文件会被自动清理\卸载。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Global.FontManager
