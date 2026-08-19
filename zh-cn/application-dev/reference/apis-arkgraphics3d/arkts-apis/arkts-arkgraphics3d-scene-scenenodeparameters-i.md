# SceneNodeParameters

场景节点参数对象，用于提供场景节点层次中的名称和路径。

**起始版本：** 23

<!--Device-unnamed-export interface SceneNodeParameters--><!--Device-unnamed-export interface SceneNodeParameters-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## name

```TypeScript
name: string
```

要创建的节点名称，可由开发者自定义填写，用于标识场景节点。

**类型：** string

**起始版本：** 23

<!--Device-SceneNodeParameters-name: string--><!--Device-SceneNodeParameters-name: string-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## path

```TypeScript
path?: string
```

场景节点层次中的路径。用于指定创建的相机、灯光或节点在场景节点层次中的放置位置。 每层之间使用'/'符号进行分割。如果未提供，则将其设置为根节点的子节点。默认值为undefined。

**类型：** string

**起始版本：** 23

<!--Device-SceneNodeParameters-path?: string--><!--Device-SceneNodeParameters-path?: string-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

