# SceneResourceParameters

场景资源参数对象，包含name和uri，用于提供场景资源的名称以及3D场景所需的资源文件路径。

**起始版本：** 23

<!--Device-unnamed-export interface SceneResourceParameters--><!--Device-unnamed-export interface SceneResourceParameters-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## name

```TypeScript
name: string
```

要创建资源的名称，可由开发者自定义填写，用于标识该场景资源。

**类型：** string

**起始版本：** 23

<!--Device-SceneResourceParameters-name: string--><!--Device-SceneResourceParameters-name: string-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## uri

```TypeScript
uri?: ResourceStr
```

3D场景所需的资源文件路径。默认值为undefined。

**类型：** ResourceStr

**起始版本：** 23

<!--Device-SceneResourceParameters-uri?: ResourceStr--><!--Device-SceneResourceParameters-uri?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

