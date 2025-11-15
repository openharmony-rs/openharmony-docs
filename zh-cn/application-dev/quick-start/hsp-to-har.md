# HSP转HAR指导
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

HSP对bundleName和签名有一致性要求，在调试阶段需要先安装HSP包，这导致多模块集成开发场景下容易出现多种集成问题。在此场景下，建议使用HAR包来提供所需功能。本文通过配置项的变更将HSP工程变成HAR工程。

>
> **说明：**
>
> 阅读本文前，请开发者完成[HSP](in-app-hsp.md)、[HAR](hap-package.md)、[module.json5](module-configuration-file.md)、[hvigorfile.ts](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-config-ohos-guide)、[oh-package.json5](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-oh-package-json5)、[build-profile.json5](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-build-profile-app)学习。
>
> 部分组件和模块在HAP、HSP、HAR中集成使用时存在差异，例如[加载HAR中Worker线程文件相比HSP存在单独的使用约束](../arkts-utils/worker-introduction.md#文件路径注意事项)，因此按照如下步骤完成HSP转HAR后，请关注对应组件和模块介绍并进行适配。
>

## HSP转HAR的操作步骤

1. 修改HSP模块下的module.json5文件，将type字段值改为har，删除deliveryWithInstall和pages字段。

    <!-- @[hsp_to_har_001](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/HspToHar/library/src/main/module.json5) -->

``` JSON5
{
  "module": {
    "name": "har",
    "type": "har",
    "deviceTypes": [
      "tablet",
      "2in1"
    ]
  }
}
```

2. 在resource\base\profile文件夹下，删除main_pages.json文件。

3. 修改HSP模块的hvigorfile.ts文件，将内容替换为以下内容。

    <!-- @[hsp_to_har_002](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/HspToHar/library/hvigorfile.ts) -->

``` TypeScript
// MyApplication\library\hvigorfile.ts
import { harTasks } from '@ohos/hvigor-ohos-plugin';

export default {
  system: harTasks,  // 编译修改成har的任务
  plugins:[]
}
```

4. 修改HSP模块的oh-package.json5文件，删除packageType配置。

5. 修改项目级的配置文件 `build-profile.json5`，在 `modules` 模块下找到 HSP 的配置信息，删除 HSP 配置下的 `targets`。