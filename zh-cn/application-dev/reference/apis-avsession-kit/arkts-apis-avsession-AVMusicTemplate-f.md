# Functions
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->
> **说明：**
>
> 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## avMusicTemplate.createAVMusicTemplate<sup>23+</sup>

createAVMusicTemplate(accessType: AVMusicTemplateType): AVMusicTemplate

创建音频模板，返回音频模板实例。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明               |
| ---------- | ------------------------------------------------------------ | ---- | ------------------ |
| accessType | [AVMusicTemplateType](arkts-apis-avsession-AVMusicTemplate-e.md#AVMusicTemplateType23) | 是   | 音频模板枚举类型。 |

**返回值：**

| 类型                                                       | 说明                             |
| ---------------------------------------------------------- | -------------------------------- |
| [AVMusicTemplate](arkts-apis-avsession-AVMusicTemplate.md) | 音频模板对象，可用于获取会话ID。 |

**错误码：**

以下错误码的详细介绍请参见[音频模板错误码](errorcode-avsession-avMusicTemplate.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |
| 35000001 | Failed to create the AVMusicTemplate.                        |

**示例：**

```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { TemplateManager } from '../manager/TemplateManager';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    console.info('onCreate');
    TemplateManager.getInstance().createTemplate();
  }
}
```

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private static sInstance: TemplateManager;

  private constructor() {
  }

  /**
   * 获取模板控制器实例
   *
   * @returns 模板控制器实例
   */
  public static getInstance(): TemplateManager {
    if (!TemplateManager.sInstance) {
      TemplateManager.sInstance = new TemplateManager();
    }
    return TemplateManager.sInstance;
  };

  /**
   * 创建音频模板
   */
  public createTemplate() {
    if (this.template) {
      console.warn('createTemplate: template not undefined');
      return
    }
    try {
      this.template = avMusicTemplate.createAVMusicTemplate(avMusicTemplate.AVMusicTemplateType.DEFAULT);
      console.info('createTemplate: success');
      this.registerListener();
    } catch (e) {
      console.error(`createTemplate, errCode: ${e?.code}`);
    }
  }
}
```



## avMusicTemplate.createAVMusicTemplateController<sup>23+</sup>

createAVMusicTemplateController(sessionId: string): AVMusicTemplateController

创建音频模板控制器，返回音频模板控制器对象。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名    | 类型   | 必填 | 说明                          |
| --------- | ------ | ---- | ----------------------------- |
| sessionId | string | 是   | AVSession对象唯一的会话标识。 |

**错误码：**

以下错误码的详细介绍请参见[音频模板错误码](errorcode-avsession-avMusicTemplate.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verify failed.                                    |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |
| 35000002 | Failed to create the AVMusicTemplate controller.             |
| 35000005 | AVMusicTemplate does not exist.                              |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private currentBundleName: string | undefined = undefined;
  private templateCreateCallback: Callback<avMusicTemplate.AVMusicTemplateDescriptor> =
    (descriptor: avMusicTemplate.AVMusicTemplateDescriptor) => {
      if (this.isInvalid(descriptor)) {
        console.warn(TAG, 'templateCreateCallback: descriptor is invalid');
        return;
      }
      console.info(TAG, `templateCreateCallback, bundleName: ${descriptor.bundleName}`);
      this.createController(descriptor.sessionId, descriptor.bundleName);
    };
  private templateDestroyCallback: Callback<avMusicTemplate.AVMusicTemplateDescriptor> =
    (descriptor: avMusicTemplate.AVMusicTemplateDescriptor) => {
      if (this.isInvalid(descriptor)) {
        console.warn(TAG, 'templateDestroyCallback: descriptor is invalid');
        return;
      }
      if (this.isStringEmpty(this.currentBundleName)) {
        console.warn(TAG, 'templateDestroyCallback: current bundleName is empty');
        return;
      }
      if (this.currentBundleName !== descriptor.bundleName) {
        console.warn(TAG, 'templateDestroyCallback: not current bundleName');
        return;
      }
      this.unregisterListener();
      this.destroyController();
    };

  /**
   * 通过getAllAVMusicTemplateDescriptors创建模板
   */
  public createAvMusicTemplateController(bundleName: string) {
    if (this.isStringEmpty(bundleName)) {
      console.warn(TAG, 'createAvMusicTemplateController: bundleName is empty');
      return;
    }
    this.currentBundleName = bundleName;
    try {
      // 该方法需要权限ohos.permission.MANAGE_MEDIA_RESOURCES
      let descriptors: avMusicTemplate.AVMusicTemplateDescriptor[] = avMusicTemplate.getAllAVMusicTemplateDescriptors();
      if (this.isEmptyArray(descriptors)) {
        console.info(TAG, 'createAvMusicTemplateController: descriptors is empty');
        return;
      }
      for (let descriptor of descriptors) {
        if (descriptor === null || descriptor === undefined) {
          console.warn(TAG, 'createAvMusicTemplateController: descriptor is invalid continue');
          continue;
        }
        if (this.currentBundleName === descriptor.bundleName) {
          this.createController(descriptor.sessionId, descriptor.bundleName);
          return;
        }
      }
    } catch (e) {
      console.error(TAG, `getAllAVMusicTemplateDescriptors failed, errCode: ${e?.code}`);
    }
  };

  private isInvalid<T>(obj: T): boolean {
    return obj === undefined || obj === null;
  }

  private isStringEmpty(str: string | undefined): boolean {
    return str === undefined || str === null || str.trim().length === 0;
  }

  private isEmptyArray<T>(array: T[]): boolean {
    return this.isInvalid(array) || array.length <= 0;
  }

  /**
   * 注册模板监听
   */
  public registerAVMusicTemplateListener() {
    try {
      // 该方法需要权限ohos.permission.MANAGE_MEDIA_RESOURCES
      avMusicTemplate.onAVMusicTemplateCreate(this.templateCreateCallback);

      // 该方法需要权限ohos.permission.MANAGE_MEDIA_RESOURCES
      avMusicTemplate.onAVMusicTemplateDestroy(this.templateDestroyCallback);
    } catch (e) {
      console.error(TAG, `registerAVMusicTemplateListener: errCode: ${e?.code}`);
    }
  }

  private createController(sessionId: string, bundleName: string) {
    if (this.currentBundleName === null || this.currentBundleName === undefined) {
      console.warn(TAG, 'createController: sessionId is invalid');
      return;
    }
    if (sessionId === null || sessionId === undefined) {
      console.warn(TAG, 'createController: sessionId is invalid');
      return;
    }
    if (bundleName === null || bundleName === undefined) {
      console.warn(TAG, 'createController: bundleName is invalid');
      return;
    }
    if (this.currentBundleName !== bundleName) {
      console.warn(TAG, 'createController: not current bundleName');
      return;
    }
    if (this.controller != undefined) {
      console.warn(TAG, 'createController: controller not undefined');
      return;
    }
    try {
      this.controller = avMusicTemplate.createAVMusicTemplateController(sessionId);
      console.info(TAG, `createController success, bundleName: ${this.currentBundleName}`);
    } catch (e) {
      console.error(TAG, `createController: errCode: ${e?.code}`);
    }
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    // 注销用户信息改变的监听。
    this.controller?.offUserInfoChange();

    // 注销弹框命令改变的监听。
    this.controller?.offDialogCommandChange();

    // 注销当前单曲改变的监听。
    this.controller?.offCurrentSingleChange();

    // 注销媒体实体改变的监听。
    this.controller?.offMediaEntitiesChange();

    // 注销标签页内容改变的监听。
    this.controller?.offTabContentChange();

    // 注销播放列表改变的监听。
    this.controller?.offPlaylistChange();

    // 注销下载媒体状态改变的监听。
    this.controller?.offDownloadMediaEntityStatusChange();

    // 注销自定义元素改变的监听。
    this.controller?.offCustomElementsChange();

    // 注销设置改变的监听。
    this.controller?.offSettingsChange();

    // 注销上报执行动作的监听。
    this.controller?.offReportExecuteAction();

    // 注销通知媒体中心拉起指定三方应用界面的信息的监听。
    this.controller?.offExtensionAbilityChange();
  }

  /**
   * 销毁控制器
   */
  public destroyController() {
    console.info(TAG, 'destroyController')
    this.controller?.destroy();
    this.controller = undefined;
    this.currentBundleName = undefined;
  }

  /**
   * 反注册模板监听
   */
  public unregisterAVMusicTemplateListener() {
    try {
      avMusicTemplate.offAVMusicTemplateCreate();
      avMusicTemplate.offAVMusicTemplateDestroy();
    } catch (e) {
      console.error(TAG, `unregisterAVMusicTemplateListener: errCode: ${e?.code}`);
    }
  }
}
```

## avMusicTemplate.getAllAVMusicTemplateDescriptors<sup>23+</sup>

getAllAVMusicTemplateDescriptors(userId?: int): AVMusicTemplateDescriptor[]

获取所有的音频模板描述，返回音频模板描述的集合。

**需要权限：**ohos.permission.MANAGE_MEDIA_RESOURCES

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明     |
| ------ | ---- | ---- | -------- |
| userId | int  | 否   | 用户ID。 |

**返回值：**

| 类型                                                         | 说明                 |
| ------------------------------------------------------------ | -------------------- |
| [AVMusicTemplateDescriptor](arkts-apis-avsession-AVMusicTemplate-i.md#AVMusicTemplateDescriptor)[] | 音频模板描述的集合。 |

**错误码：**

以下错误码的详细介绍请参见[音频模板错误码](errorcode-avsession-avMusicTemplate.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verify failed.                                    |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private currentBundleName: string | undefined = undefined;

  /**
   * 创建模板
   */
  public createAvMusicTemplateController(bundleName: string) {
    if (this.isStringEmpty(bundleName)) {
      console.warn(TAG, 'createAvMusicTemplateController: bundleName is empty');
      return;
    }
    this.currentBundleName = bundleName;
    try {
      // 该方法需要权限ohos.permission.MANAGE_MEDIA_RESOURCES
      let descriptors: avMusicTemplate.AVMusicTemplateDescriptor[] = avMusicTemplate.getAllAVMusicTemplateDescriptors();
    } catch (e) {
      console.error(TAG, `getAllAVMusicTemplateDescriptors failed, errCode: ${e?.code}`);
    }
  };

  private isStringEmpty(str: string | undefined): boolean {
    return str === undefined || str === null || str.trim().length === 0;
  }
}
```

## avMusicTemplate.onAVMusicTemplateCreate<sup>23+</sup>

onAVMusicTemplateCreate(callback: Callback&lt;AVMusicTemplateDescriptor&gt;): void

注册音频模板创建监听。

**需要权限：**ohos.permission.MANAGE_MEDIA_RESOURCES

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                         |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------- |
| callback | Callback<[AVMusicTemplateDescriptor](arkts-apis-avsession-AVMusicTemplate-i.md#AVMusicTemplateDescriptor)> | 是   | 回调函数，返回音频模板描述。 |

**错误码：**

以下错误码的详细介绍请参见[音频模板错误码](errorcode-avsession-avMusicTemplate.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verify failed.                                    |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private templateCreateCallback: Callback<avMusicTemplate.AVMusicTemplateDescriptor> =
    (descriptor: avMusicTemplate.AVMusicTemplateDescriptor) => {
      if (this.isInvalid(descriptor)) {
        console.warn(TAG, 'templateCreateCallback: descriptor is invalid');
        return;
      }
      console.info(TAG, `templateCreateCallback, bundleName: ${descriptor.bundleName}`);
    };

  private isInvalid<T>(obj: T): boolean {
    return obj === undefined || obj === null;
  }

  /**
   * 注册模板监听
   */
  public registerAVMusicTemplateListener() {
    try {
      // 该方法需要权限ohos.permission.MANAGE_MEDIA_RESOURCES
      avMusicTemplate.onAVMusicTemplateCreate(this.templateCreateCallback);
    } catch (e) {
      console.error(TAG, `registerAVMusicTemplateListener: errCode: ${e?.code}`);
    }
  }
}
```

## avMusicTemplate.offAVMusicTemplateCreate<sup>23+</sup>

offAVMusicTemplateCreate(callback?: Callback&lt;AVMusicTemplateDescriptor&gt;): void

注销音频模板创建监听。

**需要权限：**ohos.permission.MANAGE_MEDIA_RESOURCES

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                         |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------- |
| callback | Callback<[AVMusicTemplateDescriptor](arkts-apis-avsession-AVMusicTemplate-i.md#AVMusicTemplateDescriptor)> | 否   | 回调函数，返回音频模板描述。 |

**错误码：**

以下错误码的详细介绍请参见[音频模板错误码](errorcode-avsession-avMusicTemplate.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verify failed.                                    |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  /**
   * 反注册模板监听
   */
  public unregisterAVMusicTemplateListener() {
    try {
      avMusicTemplate.offAVMusicTemplateCreate();
    } catch (e) {
      console.error(TAG, `unregisterAVMusicTemplateListener: errCode: ${e?.code}`);
    }
  }
}
```

## avMusicTemplate.onAVMusicTemplateDestroy<sup>23+</sup>

onAVMusicTemplateDestroy(callback: Callback&lt;AVMusicTemplateDescriptor&gt;): void

注册音频模板销毁监听。

**需要权限：**ohos.permission.MANAGE_MEDIA_RESOURCES

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                         |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------- |
| callback | Callback<[AVMusicTemplateDescriptor](arkts-apis-avsession-AVMusicTemplate-i.md#AVMusicTemplateDescriptor)> | 是   | 回调函数，返回音频模板描述。 |

**错误码：**

以下错误码的详细介绍请参见[音频模板错误码](errorcode-avsession-avMusicTemplate.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verify failed.                                    |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private templateDestroyCallback: Callback<avMusicTemplate.AVMusicTemplateDescriptor> =
    (descriptor: avMusicTemplate.AVMusicTemplateDescriptor) => {
    };

  /**
   * 注册模板监听
   */
  public registerAVMusicTemplateListener() {
    try {
      // 该方法需要权限ohos.permission.MANAGE_MEDIA_RESOURCES
      avMusicTemplate.onAVMusicTemplateDestroy(this.templateDestroyCallback);
    } catch (e) {
      console.error(TAG, `registerAVMusicTemplateListener: errCode: ${e?.code}`);
    }
  }
}
```

## avMusicTemplate.offAVMusicTemplateDestroy<sup>23+</sup>

offAVMusicTemplateDestroy(callback?: Callback&lt;AVMusicTemplateDescriptor&gt;): void

注销音频模板销毁监听。

**需要权限：**ohos.permission.MANAGE_MEDIA_RESOURCES

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                         |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------- |
| callback | Callback<[AVMusicTemplateDescriptor](arkts-apis-avsession-AVMusicTemplate-i.md#AVMusicTemplateDescriptor)> | 否   | 回调函数，返回音频模板描述。 |

**错误码：**

以下错误码的详细介绍请参见[音频模板错误码](errorcode-avsession-avMusicTemplate.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verify failed.                                    |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  /**
   * 反注册模板监听
   */
  public unregisterAVMusicTemplateListener() {
    try {
      avMusicTemplate.offAVMusicTemplateDestroy();
    } catch (e) {
      console.error(TAG, `unregisterAVMusicTemplateListener: errCode: ${e?.code}`);
    }
  }
}
```