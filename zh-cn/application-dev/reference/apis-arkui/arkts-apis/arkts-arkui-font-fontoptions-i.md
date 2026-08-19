# FontOptions

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-font-interface FontOptions--><!--Device-font-interface FontOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { font } from '@kit.ArkUI';
```

## familyName

```TypeScript
familyName: string | Resource
```

设置注册的字体名称。

**类型：** string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FontOptions-familyName: string | Resource--><!--Device-FontOptions-familyName: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## familySrc

```TypeScript
familySrc: string | Resource
```

设置注册字体文件的路径。 **说明：** 读取系统沙箱路径内的资源时，建议使用file://路径前缀的字符串，需要确保沙箱目录路径下的文件存在并且有可读权限。

**类型：** string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FontOptions-familySrc: string | Resource--><!--Device-FontOptions-familySrc: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

