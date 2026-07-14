# RouterOptions

路由跳转选项。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

## params

```TypeScript
params?: Object
```

表示路由跳转时要同时传递到目标页面的数据，切换到其他页面时，当前接收的数据失效。跳转到目标页面后，使用router.getParams()获取传递的参数，此外，在类web范式中，参数也可以在页面中直接使用，如
this.keyValue(keyValue为跳转时params参数中的key值)，如果目标页面中已有该字段，则其值会被传入的字段值覆盖。

**说明：**

params参数只能传递可序列化的参数，不能传递方法和系统接口返回的对象（例如，媒体接口定义和返回的PixelMap对象）。建议开发者提取系统接口返回的对象中需要被传递的基础类型属性，自行构造object类型对象进行传递。

**类型：** Object

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

## recoverable

```TypeScript
recoverable?: boolean
```

表示对应的页面是否可恢复，默认为true。当为true时，表示可恢复，当为false时，表示不可恢复。

**说明：**

当应用退到后台，并且在未来的某个时间点，由于系统资源限制等原因被系统杀死，如果某个页面被设置成可恢复，那么该应用再次被拉到前台后系统可以恢复出页面，详细说明请参考
[UIAbility备份恢复](../../../../application-models/ability-recover-guideline.md)。

**类型：** boolean

**起始版本：** 14

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

## url

```TypeScript
url: string
```

表示目标页面的url，可以用以下两种格式：

-?页面绝对路径，由配置文件中pages列表提供，例如：

??-?pages/index/index

??-?pages/detail/detail

-?特殊值，如果url的值是"/"，则跳转到首页，首页默认为页面跳转配置项src数组的第一个数据项。

**类型：** string

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

