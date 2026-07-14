# ProcessPriority

子进程压制档位。

**起始版本：** 17

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

## PROCESS_BACKGROUND

```TypeScript
PROCESS_BACKGROUND = 1
```

该档位相较PROCESS_INACTIVE压制效果更显著，获取到的CPU资源更少。推荐执行处于后台的图文页面等用户无感知业务的后台子进程时设置该档位。

**起始版本：** 17

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

## PROCESS_INACTIVE

```TypeScript
PROCESS_INACTIVE = 2
```

推荐正在执行播放音频、导航等用户可感知业务的后台子进程时设置该档位。

**起始版本：** 17

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

