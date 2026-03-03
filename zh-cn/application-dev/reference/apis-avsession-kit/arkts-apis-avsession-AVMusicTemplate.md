# Class (AVMusicTemplate)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->

> **说明：**
>
> - 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

调用[avMusicTemplate.createAVMusicTemplate](arkts-apis-avsession-AVMusicTemplate-f.md#avmusictemplatecreateavmusictemplate23)后，返回实例，可以获得ID，启动音频模板界面，设置数据获取方法，同步数据给模板控制方，以及执行其他相关操作。

## 导入模块

```ts
import { aVMusicTemplate } from '@kit.AVSessionKit';
```

## 属性

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称       | 类型   | 只读 | 可选 | 说明                 |
| :--------- | :----- | :--- | :--- | :------------------- |
| sessionId  | string | 是   | 否   | 音频模板唯一的标识。 |
| sessionTag | string | 是   | 否   | 音频模板标签。       |

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
    } catch (e) {
      console.error(`createTemplate, errCode: ${e?.code}`);
    }
  }
}
```

## startTemplate<sup>23+</sup>

startTemplate(): Promise&lt;OperResult&gt;

启动音频模板界面。接口采用Promise异步返回形式，返回操作结果。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型                                                         | 说明                        |
| ------------------------------------------------------------ | --------------------------- |
| Promise\<[OperResult](arkts-apis-avsession-AVMusicTemplate-i.md#operresult23)> | Promise对象。返回操作结果。 |

**错误码：**

以下错误码的详细介绍请参见[音频模板错误码](errorcode-avsession-avMusicTemplate.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * 模拟开启模板
   */
  public startTemplate() {
    this.template?.startTemplate();
  }
}
```

## onQueryMainTabs<sup>23+</sup>

onQueryMainTabs(callback: QueryMainTabsEvent): void

注册查询主标签的事件监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明               |
| -------- | ------------------------------------------------------------ | ---- | ------------------ |
| callback | [QueryMainTabsEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querymaintabsevent23) | 是   | 查询主选项卡回调。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryMainTabsEvent: avMusicTemplate.QueryMainTabsEvent = async () => {
    return new Promise<avMusicTemplate.MediaTab[]>(async (resolve, reject) => {
      try {
        let tabs: avMusicTemplate.MediaTab[] = await this.getMainTabs();
        resolve(tabs);
      } catch (e) {
        console.error(`queryMainTabsEvent fail, errCode: ${e?.code}`);
        reject(e);
      }
    });
  };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQueryMainTabs(this.queryMainTabsEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offQueryMainTabs();
  }

  /**
   * 模拟获取主界面的所有TAB。
   *
   * @returns Promise类型MediaTab数组
   */
  private async getMainTabs(): Promise<avMusicTemplate.MediaTab[]> {
    let homeTab: avMusicTemplate.MediaTab = {
      tabId: 'home',
      tabName: '首页'
    };
    let mineTab: avMusicTemplate.MediaTab = {
      tabId: 'mine',
      tabName: '我的'
    };
    let mainTabs: avMusicTemplate.MediaTab[] = [homeTab, mineTab];
    return mainTabs;
  };
}
```

## offQueryMainTabs<sup>23+</sup>

offQueryMainTabs(callback?: QueryMainTabsEvent): void

注销查询主标签事件监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明               |
| -------- | ------------------------------------------------------------ | ---- | ------------------ |
| callback | [QueryMainTabsEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querymaintabsevent23) | 否   | 查询主选项卡回调。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQueryMainTabs](#onquerymaintabs23)的示例。

## onQueryMediaTabContent<sup>23+</sup>

onQueryMediaTabContent(callback: QueryMediaTabContentEvent): void

注册查询媒体标签内容事件监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                       |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| callback | [QueryMediaTabContentEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querymediatabcontentevent23) | 是   | 查询媒体标签页内容的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryMediaTabContentEvent: avMusicTemplate.QueryMediaTabContentEvent = async (tabId: string) => {
    return new Promise<avMusicTemplate.MediaTabContent>(async (resolve, reject) => {
      try {
        let tabContent: avMusicTemplate.MediaTabContent = await this.createMediaTabContent();
        resolve(tabContent);
      } catch (e) {
        console.error(`queryMediaTabContentEvent fail, errCode: ${e?.code}`);
        reject(e);
      }
    });
  };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQueryMediaTabContent(this.queryMediaTabContentEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offQueryMediaTabContent();
  }

  /**
   * 模拟获取TAB内容。
   *
   * @returns 标签页内容。
   */
  private async createMediaTabContent(): Promise<avMusicTemplate.MediaTabContent> {
    let compilation: avMusicTemplate.Compilation = await this.createCompilation();
    let mediaTabContent: avMusicTemplate.MediaTabContent = {
      errorCode: 0,
      tabId: 'tabId',
      compilations: [compilation]
    }
    return mediaTabContent;
  };

  /**
   * 模拟获取合集数据。
   *
   * @returns 合集
   */
  private async createCompilation(): Promise<avMusicTemplate.Compilation> {
    let mediaEntity: avMusicTemplate.MediaEntity = await this.createMediaEntity();
    let compilation: avMusicTemplate.Compilation = {
      errorCode: 0,
      id: '',
      title: '',
      hasMoreData: false,
      totalSize: 1,
      memberMediaType: avMusicTemplate.EntityType.SINGLE,
      topElements: [mediaEntity],
    }
    return compilation;
  };

  /**
   * 模拟获取媒体数据
   *
   * @returns 媒体数据
   */
  private async createMediaEntity(): Promise<avMusicTemplate.MediaEntity> {
    let mediaEntity: avMusicTemplate.MediaEntity = {
      mediaId: 'mediaId',
      mediaType: avMusicTemplate.EntityType.SINGLE,
      parentId: 'parentId',
      parentMediaType: avMusicTemplate.EntityType.SINGLE,
      title: 'title',
      imageUrl: 'imageUrl',
      playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
    };
    return mediaEntity;
  };
}
```

## offQueryMediaTabContent<sup>23+</sup>

offQueryMediaTabContent(callback?: QueryMediaTabContentEvent): void

取消查询媒体标签内容监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                           |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| callback | [QueryMediaTabContentEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querymediatabcontentevent23) | 否   | 查询媒体标签页内容的回调函数。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQueryMediaTabContent](#onquerymediatabcontent23)的示例。

## onQueryMediaEntity<sup>23+</sup>

onQueryMediaEntity(callback: QueryMediaEntityEvent): void

注册查询媒体实体监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [QueryMediaEntityEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querymediaentityevent23) | 是   | 查询媒体实体的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryMediaEntityEvent: avMusicTemplate.QueryMediaEntityEvent =
    async (params: avMusicTemplate.QueryMediaEntityParam) => {
      return new Promise<avMusicTemplate.PageMediaEntity>(async (resolve, reject) => {
        try {
          let pageMediaEntity: avMusicTemplate.PageMediaEntity = await this.createPageMediaEntity();
          resolve(pageMediaEntity);
        } catch (e) {
          console.error(`queryMediaEntityEvent fail, errCode: ${e?.code}`);
          reject(e);
        }
      });
    };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQueryMediaEntity(this.queryMediaEntityEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offQueryMediaEntity();
  }

  /**
   * 模拟获取PageMediaEntity。
   *
   * @returns PageMediaEntity
   */
  private async createPageMediaEntity(): Promise<avMusicTemplate.PageMediaEntity> {
    let mediaEntity: avMusicTemplate.MediaEntity = await this.createMediaEntity();
    let pageMediaEntity: avMusicTemplate.PageMediaEntity = {
      errorCode: 0,
      pageIndex: 0,
      pageSize: 1,
      hasMoreData: false,
      totalSize: 1,
      memberMediaType: avMusicTemplate.EntityType.SINGLE,
      elements: [mediaEntity]
    }
    return pageMediaEntity;
  };

  /**
   * 模拟获取媒体数据
   *
   * @returns 媒体数据
   */
  private async createMediaEntity(): Promise<avMusicTemplate.MediaEntity> {
    let mediaEntity: avMusicTemplate.MediaEntity = {
      mediaId: 'mediaId',
      mediaType: avMusicTemplate.EntityType.SINGLE,
      parentId: 'parentId',
      parentMediaType: avMusicTemplate.EntityType.SINGLE,
      title: 'title',
      imageUrl: 'imageUrl',
      playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
    };
    return mediaEntity;
  };
}
```

## offQueryMediaEntity<sup>23+</sup>

offQueryMediaEntity(callback?: QueryMediaEntityEvent): void

注销查询媒体实体监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [QueryMediaEntityEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querymediaentityevent23) | 否   | 查询媒体实体的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQueryMediaEntity](#onquerymediaentity23)的示例。

## onQueryCompilation<sup>23+</sup>

onQueryCompilation(callback: QueryCompilationEvent): void

注册查询合集的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明             |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| callback | [QueryCompilationEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querycompilationevent23) | 是   | 查询合集的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryCompilationEvent: avMusicTemplate.QueryCompilationEvent =
    async (compilationId: string, pageIndex: number) => {
      return new Promise<avMusicTemplate.PageMediaEntity>(async (resolve, reject) => {
        try {
          let pageMediaEntity: avMusicTemplate.PageMediaEntity = await this.createPageMediaEntity();
          resolve(pageMediaEntity);
        } catch (e) {
          console.error(`queryCompilationEvent fail, errCode: ${e?.code}`);
          reject(e);
        }
      });
    };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQueryCompilation(this.queryCompilationEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offQueryCompilation();
  }

  /**
   * 模拟获取PageMediaEntity。
   *
   * @returns PageMediaEntity
   */
  private async createPageMediaEntity(): Promise<avMusicTemplate.PageMediaEntity> {
    let mediaEntity: avMusicTemplate.MediaEntity = await this.createMediaEntity();
    let pageMediaEntity: avMusicTemplate.PageMediaEntity = {
      errorCode: 0,
      pageIndex: 0,
      pageSize: 1,
      hasMoreData: false,
      totalSize: 1,
      memberMediaType: avMusicTemplate.EntityType.SINGLE,
      elements: [mediaEntity]
    }
    return pageMediaEntity;
  };

  /**
   * 模拟获取媒体数据
   *
   * @returns 媒体数据
   */
  private async createMediaEntity(): Promise<avMusicTemplate.MediaEntity> {
    let mediaEntity: avMusicTemplate.MediaEntity = {
      mediaId: 'mediaId',
      mediaType: avMusicTemplate.EntityType.SINGLE,
      parentId: 'parentId',
      parentMediaType: avMusicTemplate.EntityType.SINGLE,
      title: 'title',
      imageUrl: 'imageUrl',
      playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
    };
    return mediaEntity;
  };
}
```

## offQueryCompilation<sup>23+</sup>

offQueryCompilation(callback?: QueryCompilationEvent): void

注销查询合集的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明             |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| callback | [QueryCompilationEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querycompilationevent23) | 否   | 查询合集的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQueryCompilation](#onquerycompilation23)的示例。

## onQueryPlaylist<sup>23+</sup>

onQueryPlaylist(callback: QueryPlaylistEvent): void

注册查询播放列表的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [QueryPlaylistEvent](arkts-apis-avsession-AVMusicTemplate-t.md#queryplaylistevent23) | 是   | 查询播放列表的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryPlaylistEvent: avMusicTemplate.QueryPlaylistEvent =
    async (pageIndex: number, sort: avMusicTemplate.Sort) => {
      return new Promise<avMusicTemplate.PageMediaEntity>(async (resolve, reject) => {
        try {
          let pageMediaEntity: avMusicTemplate.PageMediaEntity = await this.createPageMediaEntity();
          resolve(pageMediaEntity);
        } catch (e) {
          console.error(`queryPlaylistEvent fail, errCode: ${e?.code}`);
          reject(e);
        }
      });
    };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQueryPlaylist(this.queryPlaylistEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offQueryPlaylist();
  }

  /**
   * 模拟获取PageMediaEntity。
   *
   * @returns PageMediaEntity
   */
  private async createPageMediaEntity(): Promise<avMusicTemplate.PageMediaEntity> {
    let mediaEntity: avMusicTemplate.MediaEntity = await this.createMediaEntity();
    let pageMediaEntity: avMusicTemplate.PageMediaEntity = {
      errorCode: 0,
      pageIndex: 0,
      pageSize: 1,
      hasMoreData: false,
      totalSize: 1,
      memberMediaType: avMusicTemplate.EntityType.SINGLE,
      elements: [mediaEntity]
    }
    return pageMediaEntity;
  };

  /**
   * 模拟获取媒体数据
   *
   * @returns 媒体数据
   */
  private async createMediaEntity(): Promise<avMusicTemplate.MediaEntity> {
    let mediaEntity: avMusicTemplate.MediaEntity = {
      mediaId: 'mediaId',
      mediaType: avMusicTemplate.EntityType.SINGLE,
      parentId: 'parentId',
      parentMediaType: avMusicTemplate.EntityType.SINGLE,
      title: 'title',
      imageUrl: 'imageUrl',
      playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
    };
    return mediaEntity;
  };
}
```

## offQueryPlaylist<sup>23+</sup>

offQueryPlaylist(callback?: QueryPlaylistEvent): void

注销查询播放列表的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [QueryPlaylistEvent](arkts-apis-avsession-AVMusicTemplate-t.md#queryplaylistevent23) | 否   | 查询播放列表的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQueryPlaylist](#onqueryplaylist23)的示例。

## onQueryCurrentSingle<sup>23+</sup>

onQueryCurrentSingle(callback: QueryCurrentSingleEvent): void

注册查询当前单曲的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [QueryCurrentSingleEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querycurrentsingleevent23) | 是   | 查询当前单曲的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryCurrentSingleEvent: avMusicTemplate.QueryCurrentSingleEvent = async () => {
    return new Promise<avMusicTemplate.Single>(async (resolve, reject) => {
      try {
        let single: avMusicTemplate.Single = await this.createCurrentSingle();
        resolve(single);
      } catch (e) {
        console.error(`queryCurrentSingleEvent fail, errCode: ${e?.code}`);
        reject(e);
      }
    });
  };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQueryCurrentSingle(this.queryCurrentSingleEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offQueryCurrentSingle();
  }

  /**
   * 模拟获取当前单曲
   *
   * @returns 当前单曲
   */
  private async createCurrentSingle(): Promise<avMusicTemplate.Single> {
    let playInfo: avMusicTemplate.PlayInfo = {
      playCounts: '100w',
      isSupportNext: true,
      isSupportPrev: false,
      isSupportQuickForward: true,
      isSupportQuickBackward: true,
      quickForwardStep: 10,
      quickBackwardStep: 10,
      isSupportSkipHead: false,
      isSupportSkipTail: true,
      isSupportPlayMode: true,
      isSupportPlayRate: true,
      supportedPlayRate: ['1', '2', '3'],
      currentPlayRate: 'string;',
      isSupportSoundQuality: false,
      isSupportSoundEffect: true,
      totalDuration: 60,
      currentPlayDuration: 10,
      isSupportProgress: false,
    }
    let favoriteData: avMusicTemplate.FavoriteData = {
      isSupportFav: true,
      isFavorite: false,
      favCounts: '1000+'
    }
    let single: avMusicTemplate.Single = {
      mediaId: 'mediaId',
      mediaType: avMusicTemplate.EntityType.SINGLE,
      parentId: 'parentId',
      parentMediaType: avMusicTemplate.EntityType.SINGLE,
      title: '歌曲标题',
      desc: '歌曲描述',
      imageUrl: '',
      playState: 0,
      isVip: false,
      singer: '',
      tags: [],
      playInfo: playInfo,
      favSubscribeData: favoriteData
    }
    return single;
  };
}
```

## offQueryCurrentSingle<sup>23+</sup>

offQueryCurrentSingle(callback?: QueryCurrentSingleEvent): void

注销查询当前单曲的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [QueryCurrentSingleEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querycurrentsingleevent23) | 否   | 查询当前单曲的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQueryCurrentSingle](#onquerycurrentsingle23)的示例。

## onQueryCompilationByKeyword<sup>23+</sup>

onQueryCompilationByKeyword(callback: QueryCompilationByKeywordEvent): void

注册按关键字查询合集的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                     |
| -------- | ------------------------------------------------------------ | ---- | ------------------------ |
| callback | [QueryCompilationByKeywordEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querycompilationbykeywordevent23) | 是   | 按关键字查询合集的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryCompilationByKeywordEvent: avMusicTemplate.QueryCompilationByKeywordEvent = async (keyword: string) => {
    return new Promise<avMusicTemplate.Compilation[]>(async (resolve, reject) => {
      try {
        let compilation: avMusicTemplate.Compilation = await this.createCompilation();
        let compilations: avMusicTemplate.Compilation[] = [compilation];
        resolve(compilations);
      } catch (e) {
        console.error(`queryCompilationByKeywordEvent fail, errCode: ${e?.code}`);
        reject(e);
      }
    });
  };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQueryCompilationByKeyword(this.queryCompilationByKeywordEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offQueryCompilationByKeyword();
  }

  /**
   * 模拟获取合集数据。
   *
   * @returns 合集
   */
  private async createCompilation(): Promise<avMusicTemplate.Compilation> {
    let mediaEntity: avMusicTemplate.MediaEntity = await this.createMediaEntity();
    let compilation: avMusicTemplate.Compilation = {
      errorCode: 0,
      id: '',
      title: '',
      hasMoreData: false,
      totalSize: 1,
      memberMediaType: avMusicTemplate.EntityType.SINGLE,
      topElements: [mediaEntity],
    }
    return compilation;
  };

  /**
   * 模拟获取媒体数据
   *
   * @returns 媒体数据
   */
  private async createMediaEntity(): Promise<avMusicTemplate.MediaEntity> {
    let mediaEntity: avMusicTemplate.MediaEntity = {
      mediaId: 'mediaId',
      mediaType: avMusicTemplate.EntityType.SINGLE,
      parentId: 'parentId',
      parentMediaType: avMusicTemplate.EntityType.SINGLE,
      title: 'title',
      imageUrl: 'imageUrl',
      playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
    };
    return mediaEntity;
  };
}
```

## offQueryCompilationByKeyword<sup>23+</sup>

offQueryCompilationByKeyword(callback?: QueryCompilationByKeywordEvent): void

注销按关键字查询合集的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                     |
| -------- | ------------------------------------------------------------ | ---- | ------------------------ |
| callback | [QueryCompilationByKeywordEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querycompilationbykeywordevent23) | 否   | 按关键字查询合集的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQueryCompilationByKeyword](#onquerycompilationbykeyword23)的示例。

## onQueryMediaEntityByKeyword<sup>23+</sup>

onQueryMediaEntityByKeyword(callback: QueryMediaEntityByKeywordEvent): void

注册按关键字查询媒体实体的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                         |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------- |
| callback | [QueryMediaEntityByKeywordEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querymediaentitybykeywordevent23) | 是   | 按关键字查询媒体实体的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryMediaEntityByKeywordEvent: avMusicTemplate.QueryMediaEntityByKeywordEvent =
    async (keyword: string, searchType: avMusicTemplate.EntityType, pageIndex: number) => {
      return new Promise<avMusicTemplate.PageMediaEntity>(async (resolve, reject) => {
        try {
          let pageMediaEntity: avMusicTemplate.PageMediaEntity = await this.createPageMediaEntity();
          resolve(pageMediaEntity);
        } catch (e) {
          console.error(`queryMediaEntityByKeywordEvent fail, errCode: ${e?.code}`);
          reject(e);
        }
      });
    };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQueryMediaEntityByKeyword(this.queryMediaEntityByKeywordEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offQueryMediaEntityByKeyword();
  }

  /**
   * 模拟获取PageMediaEntity。
   *
   * @returns PageMediaEntity
   */
  private async createPageMediaEntity(): Promise<avMusicTemplate.PageMediaEntity> {
    let mediaEntity: avMusicTemplate.MediaEntity = await this.createMediaEntity();
    let pageMediaEntity: avMusicTemplate.PageMediaEntity = {
      errorCode: 0,
      pageIndex: 0,
      pageSize: 1,
      hasMoreData: false,
      totalSize: 1,
      memberMediaType: avMusicTemplate.EntityType.SINGLE,
      elements: [mediaEntity]
    }
    return pageMediaEntity;
  };

  /**
   * 模拟获取媒体数据
   *
   * @returns 媒体数据
   */
  private async createMediaEntity(): Promise<avMusicTemplate.MediaEntity> {
    let mediaEntity: avMusicTemplate.MediaEntity = {
      mediaId: 'mediaId',
      mediaType: avMusicTemplate.EntityType.SINGLE,
      parentId: 'parentId',
      parentMediaType: avMusicTemplate.EntityType.SINGLE,
      title: 'title',
      imageUrl: 'imageUrl',
      playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
    };
    return mediaEntity;
  };
}
```

## offQueryMediaEntityByKeyword<sup>23+</sup>

offQueryMediaEntityByKeyword(callback?: QueryMediaEntityByKeywordEvent): void

注销按关键字查询媒体实体的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                         |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------- |
| callback | [QueryMediaEntityByKeywordEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querymediaentitybykeywordevent23) | 否   | 按关键字查询媒体实体的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQueryMediaEntityByKeyword](#onquerymediaentitybykeyword23)的示例。

## onQueryRecommendMediaEntityList<sup>23+</sup>

onQueryRecommendMediaEntityList(callback: QueryRecommendMediaEntityListEvent): void

注册查询推荐媒体列表的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                     |
| -------- | ------------------------------------------------------------ | ---- | ------------------------ |
| callback | [QueryRecommendMediaEntityListEvent](arkts-apis-avsession-AVMusicTemplate-t.md#queryrecommendmediaentitylistevent23) | 是   | 查询推荐媒体列表的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryRecommendMediaEntityListEvent: avMusicTemplate.QueryRecommendMediaEntityListEvent = async () => {
    return new Promise<avMusicTemplate.MediaEntity[]>(async (resolve, reject) => {
      try {
        let mediaEntity: avMusicTemplate.MediaEntity = await this.createMediaEntity();
        let mediaEntities: avMusicTemplate.MediaEntity[] = [mediaEntity];
        resolve(mediaEntities);
      } catch (e) {
        console.error(`queryRecommendMediaEntityListEvent fail, errCode: ${e?.code}`);
        reject(e);
      }
    });
  };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQueryRecommendMediaEntityList(this.queryRecommendMediaEntityListEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offQueryRecommendMediaEntityList();
  }

  /**
   * 模拟获取媒体数据
   *
   * @returns 媒体数据
   */
  private async createMediaEntity(): Promise<avMusicTemplate.MediaEntity> {
    let mediaEntity: avMusicTemplate.MediaEntity = {
      mediaId: 'mediaId',
      mediaType: avMusicTemplate.EntityType.SINGLE,
      parentId: 'parentId',
      parentMediaType: avMusicTemplate.EntityType.SINGLE,
      title: 'title',
      imageUrl: 'imageUrl',
      playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
    };
    return mediaEntity;
  };
}
```

## offQueryRecommendMediaEntityList<sup>23+</sup>

offQueryRecommendMediaEntityList(callback?: QueryRecommendMediaEntityListEvent): void

注销查询推荐媒体列表的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                     |
| -------- | ------------------------------------------------------------ | ---- | ------------------------ |
| callback | [QueryRecommendMediaEntityListEvent](arkts-apis-avsession-AVMusicTemplate-t.md#queryrecommendmediaentitylistevent23) | 否   | 查询推荐媒体列表的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQueryRecommendMediaEntityList](#onqueryrecommendmediaentitylist23)的示例。

## onQueryHotWords<sup>23+</sup>

onQueryHotWords(callback: QueryHotWordsEvent): void

注册查询热词的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明             |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| callback | [QueryHotWordsEvent](arkts-apis-avsession-AVMusicTemplate-t.md#queryhotwordsevent23) | 是   | 查询热词的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryHotWordsEvent: avMusicTemplate.QueryHotWordsEvent = async () => {
    return new Promise<string[]>(async (resolve, reject) => {
      try {
        let hotWords: string[] = ['热词1', '热词2', '热词3', '热词4', '热词5'];
        resolve(hotWords);
      } catch (e) {
        console.error(`queryHotWordsEvent fail, errCode: ${e?.code}`);
        reject(e);
      }
    });
  };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQueryHotWords(this.queryHotWordsEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offQueryHotWords();
  }
}
```

## offQueryHotWords<sup>23+</sup>

offQueryHotWords(callback?: QueryHotWordsEvent): void

注销查询热词的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明             |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| callback | [QueryHotWordsEvent](arkts-apis-avsession-AVMusicTemplate-t.md#queryhotwordsevent23) | 否   | 查询热词的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQueryHotWords](#onqueryhotwords23)的示例。

## onQuerySearchHistory<sup>23+</sup>

onQuerySearchHistory(callback: QuerySearchHistoryEvent): void

注册查询搜索历史的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [QuerySearchHistoryEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querysearchhistoryevent23) | 是   | 查询搜索历史的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private querySearchHistoryEvent: avMusicTemplate.QuerySearchHistoryEvent = async () => {
    return new Promise<string[]>(async (resolve, reject) => {
      try {
        let searchHistory: string[] = ['搜索历史1', '搜索历史2', '搜索历史3', '搜索历史4', '搜索历史5'];
        resolve(searchHistory);
      } catch (e) {
        console.error(`querySearchHistoryEvent fail, errCode: ${e?.code}`);
        reject(e);
      }
    });
  };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQuerySearchHistory(this.querySearchHistoryEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offClearSearchHistory();
  }
}
```

## offQuerySearchHistory<sup>23+</sup>

offQuerySearchHistory(callback?: QuerySearchHistoryEvent): void

注销查询搜索历史的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [QuerySearchHistoryEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querysearchhistoryevent23) | 否   | 查询搜索历史的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQuerySearchHistory](#onquerysearchhistory23)的示例。

## onClearSearchHistory<sup>23+</sup>

onClearSearchHistory(callback: ClearSearchHistoryEvent): void

注册清除搜索历史的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [ClearSearchHistoryEvent](arkts-apis-avsession-AVMusicTemplate-t.md#clearsearchhistoryevent23) | 是   | 清除搜索历史的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private clearSearchHistoryEvent: avMusicTemplate.ClearSearchHistoryEvent = async () => {
    return new Promise<avMusicTemplate.OperResult>(async (resolve, reject) => {
      try {
        let operResult: avMusicTemplate.OperResult = await this.createOperResult();
        resolve(operResult);
      } catch (e) {
        console.error(`clearSearchHistoryEvent fail, errCode: ${e?.code}`);
        reject(e);
      }
    });
  };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onClearSearchHistory(this.clearSearchHistoryEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offClearSearchHistory();
  }

  /**
   * 模拟操作结果
   *
   * @returns 操作结果
   */
  private async createOperResult(): Promise<avMusicTemplate.OperResult> {
    let operResult: avMusicTemplate.OperResult = {
      errorCode: 0,
    }
    return operResult;
  };
}
```

## offClearSearchHistory<sup>23+</sup>

offClearSearchHistory(callback?: ClearSearchHistoryEvent): void

注销清除搜索历史的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [ClearSearchHistoryEvent](arkts-apis-avsession-AVMusicTemplate-t.md#clearsearchhistoryevent23) | 否   | 清除搜索历史的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onClearSearchHistory](#onclearsearchhistory23)的示例。

## onLogin<sup>23+</sup>

onLogin(callback: LoginEvent): void

注册登录事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明       |
| -------- | ------------------------------------------------------------ | ---- | ---------- |
| callback | [LoginEvent](arkts-apis-avsession-AVMusicTemplate-t.md#loginevent23) | 是   | 登录事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private loginEvent: avMusicTemplate.LoginEvent = async (controlType: avMusicTemplate.LoginType, id?: string) => {
    return new Promise<avMusicTemplate.QrCodeInfo[]>(async (resolve, reject) => {
      try {
        let qrCodeInfo: avMusicTemplate.QrCodeInfo = await this.createQrCodeInfo();
        let qrCodeInfos: avMusicTemplate.QrCodeInfo[] = [qrCodeInfo];
        resolve(qrCodeInfos);
      } catch (e) {
        console.error(`loginEvent fail, errCode: ${e?.code}`);
        reject(e);
      }
    });
  };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onLogin(this.loginEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offLogin();
  }

  /**
   * 模拟创建二维码信息数组
   *
   * @returns Promise类型的二维码信息数组
   */
  private async createQrCodeInfo(): Promise<avMusicTemplate.QrCodeInfo> {
    let qrCodeInfo: avMusicTemplate.QrCodeInfo = {
      id: 'id',
      price: '10',
      titleName: 'title',
      detailName: 'detail',
      tips: 'tip',
      content: 'content',
      validPeriod: 1
    };
    return qrCodeInfo;
  };
}
```

## offLogin<sup>23+</sup>

offLogin(callback?: LoginEvent): void

注销登录事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明       |
| -------- | ------------------------------------------------------------ | ---- | ---------- |
| callback | [LoginEvent](arkts-apis-avsession-AVMusicTemplate-t.md#loginevent23) | 否   | 登录事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onLogin](#onlogin23)的示例。

## onRequestDialogInfo<sup>23+</sup>

onRequestDialogInfo(callback: RequestDialogInfoEvent): void

注册请求弹框信息的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [RequestDialogInfoEvent](arkts-apis-avsession-AVMusicTemplate-t.md#requestdialoginfoevent23) | 是   | 请求弹框信息的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private requestDialogInfoEvent: avMusicTemplate.RequestDialogInfoEvent =
    async (actionType: avMusicTemplate.DialogActionType, actionInfo?: avMusicTemplate.DialogActionInfo) => {
      return new Promise<avMusicTemplate.DialogInfo>(async (resolve, reject) => {
        try {
          let dialogInfo: avMusicTemplate.DialogInfo = await this.createDialogInfo();
          resolve(dialogInfo);
        } catch (e) {
          console.error(`requestDialogInfoEvent fail, errCode: ${e?.code}`);
          reject(e);
        }
      });
    };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onRequestDialogInfo(this.requestDialogInfoEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offRequestDialogInfo();
  }

  /**
   * 模拟弹框信息
   *
   * @returns 弹框信息
   */
  private async createDialogInfo(): Promise<avMusicTemplate.DialogInfo> {
    let qrCodeInfo: avMusicTemplate.QrCodeInfo[] = [{
      id: 'id',
      price: '10',
      titleName: 'title',
      detailName: 'detail',
      tips: 'tip',
      content: 'content',
      validPeriod: 1
    }
    ];
    let dialogInfo: avMusicTemplate.DialogInfo = {
      dialogId: 'dialogId',
      dialogType: avMusicTemplate.DialogType.LOGIN,
      qrCodes: qrCodeInfo
    };
    return dialogInfo;
  };
}
```

## offRequestDialogInfo<sup>23+</sup>

offRequestDialogInfo(callback?: RequestDialogInfoEvent): void

注销请求弹框信息的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [RequestDialogInfoEvent](arkts-apis-avsession-AVMusicTemplate-t.md#requestdialoginfoevent23) | 否   | 请求弹框信息的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onRequestDialogInfo](#onrequestdialoginfo23)的示例。

## onHandleMemberPurchase<sup>23+</sup>

onHandleMemberPurchase(callback: HandleMemberPurchaseEvent): void

注册处理购买会员事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [HandleMemberPurchaseEvent](arkts-apis-avsession-AVMusicTemplate-t.md#handlememberpurchaseevent23) | 是   | 处理购买会员的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private handleMemberPurchaseEvent: avMusicTemplate.HandleMemberPurchaseEvent =
    async (info: avMusicTemplate.MemberPurchaseInfo) => {
      return new Promise<avMusicTemplate.DialogInfo>(async (resolve, reject) => {
        try {
          let dialogInfo: avMusicTemplate.DialogInfo = await this.createDialogInfo();
          resolve(dialogInfo);
        } catch (e) {
          console.error(`handleMemberPurchaseEvent fail, errCode: ${e?.code}`);
          reject(e);
        }
      });
    };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onHandleMemberPurchase(this.handleMemberPurchaseEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offHandleMemberPurchase();
  }

  /**
   * 模拟弹框信息
   *
   * @returns 弹框信息
   */
  private async createDialogInfo(): Promise<avMusicTemplate.DialogInfo> {
    let qrCodeInfo: avMusicTemplate.QrCodeInfo[] = [{
      id: 'id',
      price: '10',
      titleName: 'title',
      detailName: 'detail',
      tips: 'tip',
      content: 'content',
      validPeriod: 1
    }
    ];
    let dialogInfo: avMusicTemplate.DialogInfo = {
      dialogId: 'dialogId',
      dialogType: avMusicTemplate.DialogType.LOGIN,
      qrCodes: qrCodeInfo
    };
    return dialogInfo;
  };
}
```

## offHandleMemberPurchase<sup>23+</sup>

offHandleMemberPurchase(callback?: HandleMemberPurchaseEvent): void

注销处理购买会员事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [HandleMemberPurchaseEvent](arkts-apis-avsession-AVMusicTemplate-t.md#handlememberpurchaseevent23) | 否   | 处理购买会员的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onHandleMemberPurchase](#onhandlememberpurchase23)的示例。

## onQueryMemberPurchase<sup>23+</sup>

onQueryMemberPurchase(callback: QueryMemberPurchaseEvent): void

注册查询购买会员事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [QueryMemberPurchaseEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querymemberpurchaseevent23) | 是   | 查询购买会员的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryMemberPurchaseEvent: avMusicTemplate.QueryMemberPurchaseEvent =
    async (memberPurchaseType: avMusicTemplate.MemberPurchaseType) => {
      return new Promise<avMusicTemplate.MemberPurchaseInfo[]>(async (resolve, reject) => {
        try {
          let memberPurchaseInfo: avMusicTemplate.MemberPurchaseInfo = await this.createQueryMemberPurchase();
          let memberPurchaseInfos: avMusicTemplate.MemberPurchaseInfo[] = [memberPurchaseInfo];
          resolve(memberPurchaseInfos);
        } catch (e) {
          console.error(`queryMemberPurchaseEvent fail, errCode: ${e?.code}`);
          reject(e);
        }
      });
    };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQueryMemberPurchase(this.queryMemberPurchaseEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offQueryMemberPurchase();
  }

  /**
   * 模拟查询会员购买信息
   *
   * @returns Promise类型的购买会员信息数组
   */
  private async createQueryMemberPurchase(): Promise<avMusicTemplate.MemberPurchaseInfo> {
    let memberPurchaseInfo: avMusicTemplate.MemberPurchaseInfo = {
      id: 'id',
      diagramUrl: 'diagramUrl',
      diagramContent: 'diagramContent',
      memberPurchaseType: avMusicTemplate.MemberPurchaseType.NORMAL
    };
    return memberPurchaseInfo;
  };
}
```

## offQueryMemberPurchase<sup>23+</sup>

offQueryMemberPurchase(callback?: QueryMemberPurchaseEvent): void

注销查询购买会员事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [QueryMemberPurchaseEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querymemberpurchaseevent23) | 否   | 查询购买会员的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQueryMemberPurchase](#onquerymemberpurchase23)的示例。

## onQueryCustomContent<sup>23+</sup>

onQueryCustomContent(callback: QueryCustomContentEvent): void

注册查询自定义内容事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                   |
| -------- | ------------------------------------------------------------ | ---- | ---------------------- |
| callback | [QueryCustomContentEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querycustomcontentevent23) | 是   | 查询自定义内容的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryCustomContentEvent: avMusicTemplate.QueryCustomContentEvent =
    async (queryTypes: avMusicTemplate.CustomType[]) => {
      return new Promise<avMusicTemplate.CustomElement>(async (resolve, reject) => {
        try {
          let customElement: avMusicTemplate.CustomElement = await this.createCustomContent();
          resolve(customElement);
        } catch (e) {
          console.error(`queryCustomContentEvent fail, errCode: ${e?.code}`);
          reject(e);
        }
      });
    };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onQueryCustomContent(this.queryCustomContentEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offQueryCustomContent();
  }

  /**
   * 模拟获取自定义内容
   *
   * @returns 自定义元素
   */
  private async createCustomContent(): Promise<avMusicTemplate.CustomElement> {
    let mediaEntity: avMusicTemplate.MediaEntity = {
      mediaId: 'mediaId',
      mediaType: avMusicTemplate.EntityType.SINGLE,
      parentId: 'parentId',
      parentMediaType: avMusicTemplate.EntityType.SINGLE,
      title: 'title',
      imageUrl: 'imageUrl',
      playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
    }
    let compilation: avMusicTemplate.Compilation = {
      errorCode: 0,
      errorMsg: 'success',
      id: 'id',
      title: 'title',
      hasMoreData: false,
      totalSize: 1,
      memberMediaType: avMusicTemplate.EntityType.SINGLE,
      topElements: [mediaEntity]
    };
    let customElement: avMusicTemplate.CustomElement = {
      errorCode: 0,
      customCompilations: [compilation],
    };
    return customElement;
  };
}
```

## offQueryCustomContent<sup>23+</sup>

offQueryCustomContent(callback?: QueryCustomContentEvent): void

注销查询自定义内容事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                   |
| -------- | ------------------------------------------------------------ | ---- | ---------------------- |
| callback | [QueryCustomContentEvent](arkts-apis-avsession-AVMusicTemplate-t.md#querycustomcontentevent23) | 否   | 查询自定义内容的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onQueryCustomContent](#onquerycustomcontent23)的示例。

## onDownloadMediaEntity<sup>23+</sup>

onDownloadMediaEntity(callback: DownloadMediaEntityEvent): void

注册下载媒体实体事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [DownloadMediaEntityEvent](arkts-apis-avsession-AVMusicTemplate-t.md#downloadmediaentityevent23) | 是   | 下载媒体实体的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private downloadMediaEntityEvent: avMusicTemplate.DownloadMediaEntityEvent =
    async (controlType: avMusicTemplate.DownloadControlType, mediaEntity: avMusicTemplate.MediaEntity) => {
      return new Promise<avMusicTemplate.OperResult>(async (resolve, reject) => {
        try {
          let operResult: avMusicTemplate.OperResult = await this.createOperResult();
          this.downloadMediaEntity(mediaEntity);
          resolve(operResult);
        } catch (e) {
          console.error(`downloadMediaEntityEvent fail, errCode: ${e?.code}`);
          reject(e);
        }
      });
    };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onDownloadMediaEntity(this.downloadMediaEntityEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offDownloadMediaEntity();
  }

  /**
   * 下载状态，进度刷新
   */
  public setDownloadMediaEntityStatus(mediaEntity: avMusicTemplate.MediaEntity) {
    this.template?.setDownloadMediaEntityStatus(mediaEntity);
  };

  /**
   * 模拟设置改变
   *
   * @returns Promise类型的设置条目
   */
  /**
   * 模拟操作结果
   *
   * @returns 操作结果
   */
  private async createOperResult(): Promise<avMusicTemplate.OperResult> {
    let operResult: avMusicTemplate.OperResult = {
      errorCode: 0,
    }
    return operResult;
  };

  /**
   * 模拟下载过程
   *
   * @param mediaEntity 媒体实体
   */
  private async downloadMediaEntity(mediaEntity: avMusicTemplate.MediaEntity) {
    // 下载完成之后。
    this.setDownloadMediaEntityStatus(mediaEntity);
  };
}
```

## offDownloadMediaEntity<sup>23+</sup>

offDownloadMediaEntity(callback?: DownloadMediaEntityEvent): void

注销下载媒体实体事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [DownloadMediaEntityEvent](arkts-apis-avsession-AVMusicTemplate-t.md#downloadmediaentityevent23) | 否   | 下载媒体实体的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onDownloadMediaEntity](#ondownloadmediaentity23)的示例。

## onSettingsChange<sup>23+</sup>

onSettingsChange(callback: SettingsChangeEvent): void

注册设置改变事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明             |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| callback | [SettingsChangeEvent](arkts-apis-avsession-AVMusicTemplate-t.md#settingschangeevent23) | 是   | 设置改变的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private settingsChangeEvent: avMusicTemplate.SettingsChangeEvent =
    async (settingItem: avMusicTemplate.SettingItem) => {
      return new Promise<avMusicTemplate.SettingItem>(async (resolve, reject) => {
        try {
          let settingItem: avMusicTemplate.SettingItem = await this.settingsChange();
          resolve(settingItem);
        } catch (e) {
          console.error(`settingsChangeEvent fail, errCode: ${e?.code}`);
          reject(e);
        }
      });
    };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onSettingsChange(this.settingsChangeEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offSettingsChange();
  }

  /**
   * 模拟设置改变
   *
   * @returns Promise类型的设置条目
   */
  private async settingsChange(): Promise<avMusicTemplate.SettingItem> {
    let setting: avMusicTemplate.SettingItem = {
      id: 'id',
      title: 'title',
      desc: 'desc',
      mediaId: 'mediaId',
      settingType: avMusicTemplate.SettingType.SWITCH,
      settingValue: false
    }
    return setting;
  };
}
```

## offSettingsChange<sup>23+</sup>

offSettingsChange(callback?: SettingsChangeEvent): void

注销设置改变事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明             |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| callback | [SettingsChangeEvent](arkts-apis-avsession-AVMusicTemplate-t.md#settingschangeevent23) | 否   | 设置改变的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onSettingsChange](#onsettingschange23)的示例。

## onProblemAndAdvice<sup>23+</sup>

onProblemAndAdvice(callback: ProblemAndAdviceEvent): void

注册问题与建议事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                   |
| -------- | ------------------------------------------------------------ | ---- | ---------------------- |
| callback | [ProblemAndAdviceEvent](arkts-apis-avsession-AVMusicTemplate-t.md#problemandadviceevent23) | 是   | 问题与建议的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private problemAndAdviceEvent: avMusicTemplate.ProblemAndAdviceEvent = async (advice: string) => {
    return new Promise<avMusicTemplate.OperResult>(async (resolve, reject) => {
      try {
        let operResult: avMusicTemplate.OperResult = await this.createOperResult();
        resolve(operResult);
      } catch (e) {
        console.error(`problemAndAdviceEvent fail, errCode: ${e?.code}`);
        reject(e);
      }
    });
  };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onProblemAndAdvice(this.problemAndAdviceEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offProblemAndAdvice();
  }

  /**
   * 模拟操作结果
   *
   * @returns 操作结果
   */
  private async createOperResult(): Promise<avMusicTemplate.OperResult> {
    let operResult: avMusicTemplate.OperResult = {
      errorCode: 0,
    }
    return operResult;
  };
}
```

## offProblemAndAdvice<sup>23+</sup>

offProblemAndAdvice(callback?: ProblemAndAdviceEvent): void

注销问题与建议事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                   |
| -------- | ------------------------------------------------------------ | ---- | ---------------------- |
| callback | [ProblemAndAdviceEvent](arkts-apis-avsession-AVMusicTemplate-t.md#problemandadviceevent23) | 否   | 问题与建议的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onProblemAndAdvice](#onproblemandadvice23)的示例。

## onPlayForSearch<sup>23+</sup>

onPlayForSearch(callback: PlayForSearchEvent): void

注册搜播事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明         |
| -------- | ------------------------------------------------------------ | ---- | ------------ |
| callback | [PlayForSearchEvent](arkts-apis-avsession-AVMusicTemplate-t.md#playforsearchevent23) | 是   | 搜播的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private playForSearchEvent: avMusicTemplate.PlayForSearchEvent = async (command: avMusicTemplate.SearchPlayInfoType,
    args: avMusicTemplate.SearchPlayInfo) => {
    return new Promise<avMusicTemplate.OperResult>(async (resolve, reject) => {
      try {
        let operResult: avMusicTemplate.OperResult = await this.createOperResult();
        resolve(operResult);
      } catch (e) {
        console.error(`playForSearchEvent fail, errCode: ${e?.code}`);
        reject(e);
      }
    });
  };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onPlayForSearch(this.playForSearchEvent);
  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offPlayForSearch();
  }

  /**
   * 模拟操作结果
   *
   * @returns 操作结果
   */
  private async createOperResult(): Promise<avMusicTemplate.OperResult> {
    let operResult: avMusicTemplate.OperResult = {
      errorCode: 0,
    }
    return operResult;
  };
}
```

## offPlayForSearch<sup>23+</sup>

offPlayForSearch(callback?: PlayForSearchEvent): void

注销搜播事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明         |
| -------- | ------------------------------------------------------------ | ---- | ------------ |
| callback | [PlayForSearchEvent](arkts-apis-avsession-AVMusicTemplate-t.md#playforsearchevent23) | 否   | 搜播的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onPlayForSearch](#onplayforsearch23)的示例。

## onExecuteAction<sup>23+</sup>

onExecuteAction(callback: ExecuteActionEvent): void

注册执行操作事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明             |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| callback | [ExecuteActionEvent](arkts-apis-avsession-AVMusicTemplate-t.md#executeactionevent23) | 是   | 执行操作的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private executeActionEvent: avMusicTemplate.ExecuteActionEvent = async (actionType: string, params: string) => {
    return new Promise<string>(async (resolve, reject) => {
      try {
        let result: string = 'success';
        resolve(result);
      } catch (e) {
        console.error(`executeActionEvent fail, errCode: ${e?.code}`);
        reject(e);
      }
    });
  };

  /**
   * 注册监听。
   */
  private registerListener() {
    this.template?.onExecuteAction(this.executeActionEvent);  }

  /**
   * 注销监听
   */
  public unregisterListener() {
    this.template?.offExecuteAction();
  }
}
```

## offExecuteAction<sup>23+</sup>

offExecuteAction(callback?: ExecuteActionEvent): void

注销执行操作事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明             |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| callback | [ExecuteActionEvent](arkts-apis-avsession-AVMusicTemplate-t.md#executeactionevent23) | 否   | 执行操作的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onExecuteAction](#onexecuteaction23)的示例。

## onPlayMediaEntity<sup>23+</sup>

onPlayMediaEntity(callback: PlayMediaEntityEvent): void

注册播放媒体实体事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [PlayMediaEntityEvent](arkts-apis-avsession-AVMusicTemplate-t.md#playmediaentityevent23) | 是   | 播放媒体实体的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
    private playMediaEntityEvent: avMusicTemplate.PlayMediaEntityEvent =
        async (mediaEntity: avMusicTemplate.MediaEntity) => {
            console.info('playMediaEntity');
        };

    /**
     * 注册监听。
     */
    private registerListener() {
        this.template?.onPlayMediaEntity(this.playMediaEntityEvent);
    }

    /**
     * 注销监听
     */
    public unregisterListener() {
        this.template?.offPlayMediaEntity();
    }
}
```


## offPlayMediaEntity<sup>23+</sup>

offPlayMediaEntity(callback?: PlayMediaEntityEvent): void

注销播放媒体实体事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [PlayMediaEntityEvent](arkts-apis-avsession-AVMusicTemplate-t.md#playmediaentityevent23) | 否   | 播放媒体实体的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onPlayMediaEntity](#onplaymediaentity23)的示例。

## onFavoriteMediaEntity<sup>23+</sup>

onFavoriteMediaEntity(callback: FavoriteMediaEntityEvent): void

注册收藏媒体实体事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [FavoriteMediaEntityEvent](arkts-apis-avsession-AVMusicTemplate-t.md#favoritemediaentityevent23) | 是   | 收藏媒体实体的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
    private favoriteMediaEntityEvent: avMusicTemplate.FavoriteMediaEntityEvent =
        async (actionType: avMusicTemplate.MediaFavoriteType, mediaEntity: avMusicTemplate.MediaEntity) => {
            return new Promise<avMusicTemplate.OperResult>(async (resolve, reject) => {
                try {
                    let operResult: avMusicTemplate.OperResult = await this.createOperResult();
                    resolve(operResult);
                } catch (e) {
                    console.error(`favoriteMediaEntityEvent fail, errCode: ${e?.code}`);
                    reject(e);
                }
            });
        };

    /**
     * 注册监听。
     */
    private registerListener() {
        this.template?.onFavoriteMediaEntity(this.favoriteMediaEntityEvent);
    }

    /**
     * 注销监听
     */
    public unregisterListener() {
        this.template?.offFavoriteMediaEntity();
    }

    /**
     * 模拟操作结果
     *
     * @returns 操作结果
     */
    private async createOperResult(): Promise<avMusicTemplate.OperResult> {
        let operResult: avMusicTemplate.OperResult = {
            errorCode: 0,
        }
        return operResult;
    };
}

```
## offFavoriteMediaEntity<sup>23+</sup>

offFavoriteMediaEntity(callback: FavoriteMediaEntityEvent): void

注销收藏媒体实体事件的监听。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [FavoriteMediaEntityEvent](arkts-apis-avsession-AVMusicTemplate-t.md#favoritemediaentityevent23) | 否   | 收藏媒体实体的事件。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**示例：**

请参考[onFavoriteMediaEntity](#onfavoritemediaentity23)的示例。

## setUserInfo<sup>23+</sup>

setUserInfo(userInfo: UserInfo): Promise&lt;void&gt;

向音频模板控制方同步用户信息。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明       |
| -------- | ------------------------------------------------------------ | ---- | ---------- |
| userInfo | [UserInfo](arkts-apis-avsession-AVMusicTemplate-i.md#userinfo23) | 是   | 用户信息。 |

**返回值：**

| 类型                | 说明         |
| ------------------- | ------------ |
| Promise&lt;void&gt; | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
    private isLogin: boolean = false;

    /**
     * 模拟登录状态改变
     *
     * @param isLogin 是否登录
     */
    public setLoginState(isLogin: boolean) {
        this.isLogin = isLogin;
        this.setUserInfo();
    }

    /**
     * 用户信息发生变化后通知界面刷新用户信息，如登陆账号后
     */
    public setUserInfo() {
        let userInfo: avMusicTemplate.UserInfo = {
            userInfoId: this.isLogin ? 'userInfoId' : '',
            nickName: this.isLogin ? '昵称' : '',
            profilePicUrl: this.isLogin ? 'profilePicUrl' : '',
            tips: this.isLogin ? 'tips' : '',
            isLogin: this.isLogin,
            isVip: false
        };
        this.template?.setUserInfo(userInfo);
    };
}
```

## setDialogCommand<sup>23+</sup>

setDialogCommand(type: DialogControlType, dialogInfo: DialogInfo): Promise&lt;void&gt;

向音频模板控制方同步弹框命令。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明           |
| ---------- | ------------------------------------------------------------ | ---- | -------------- |
| type       | [DialogControlType](arkts-apis-avsession-AVMusicTemplate-t.md#dialogcontroltype23) | 是   | 弹框控制类型。 |
| dialogInfo | [DialogInfo](arkts-apis-avsession-AVMusicTemplate-i.md#dialoginfo23) | 是   | 弹框信息。     |

**返回值：**

| 类型                | 说明         |
| ------------------- | ------------ |
| Promise&lt;void&gt; | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * 弹框相关的操作，如：打开，关闭
     */
    public setDialogCommand() {
        let type: avMusicTemplate.DialogControlType = 'open';
        let qrCodeInfo: avMusicTemplate.QrCodeInfo[] = [{
            id: 'id',
            price: '10',
            titleName: 'title',
            detailName: 'detail',
            tips: 'tip',
            content: 'content',
            validPeriod: 1
        }];
        let dialogInfo: avMusicTemplate.DialogInfo = {
            dialogId: 'dialogId',
            dialogType: avMusicTemplate.DialogType.LOGIN,
            qrCodes: qrCodeInfo
        };
        this.template?.setDialogCommand(type, dialogInfo);
    };
}
```
## setCurrentSingle<sup>23+</sup>

setCurrentSingle(single: Single): Promise&lt;void&gt;

向音频模板控制方同步当前单曲。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明       |
| ------ | ------------------------------------------------------------ | ---- | ---------- |
| single | [Single](arkts-apis-avsession-AVMusicTemplate-i.md#single23) | 是   | 当前单曲。 |

**返回值：**

| 类型                | 说明         |
| ------------------- | ------------ |
| Promise&lt;void&gt; | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    public async setCurrentSingle() {
        let single: avMusicTemplate.Single = await this.createCurrentSingle()
        this.template?.setCurrentSingle(single);
    };

    /**
     * 模拟获取当前单曲
     *
     * @returns 当前单曲
     */
    private async createCurrentSingle(): Promise<avMusicTemplate.Single> {
        let playInfo: avMusicTemplate.PlayInfo = {
            playCounts: '100w',
            isSupportNext: true,
            isSupportPrev: false,
            isSupportQuickForward: true,
            isSupportQuickBackward: true,
            quickForwardStep: 10,
            quickBackwardStep: 10,
            isSupportSkipHead: false,
            isSupportSkipTail: true,
            isSupportPlayMode: true,
            isSupportPlayRate: true,
            supportedPlayRate: ['1', '2', '3'],
            currentPlayRate: 'string;',
            isSupportSoundQuality: false,
            isSupportSoundEffect: true,
            totalDuration: 60,
            currentPlayDuration: 10,
            isSupportProgress: false,
        }
        let favoriteData: avMusicTemplate.FavoriteData = {
            isSupportFav: true,
            isFavorite: false,
            favCounts: '1000+'
        }
        let single: avMusicTemplate.Single = {
            mediaId: 'mediaId',
            mediaType: avMusicTemplate.EntityType.SINGLE,
            parentId: 'parentId',
            parentMediaType: avMusicTemplate.EntityType.SINGLE,
            title: '歌曲标题',
            desc: '歌曲描述',
            imageUrl: '',
            playState: 0,
            isVip: false,
            singer: '',
            tags: [],
            playInfo: playInfo,
            favSubscribeData: favoriteData
        }
        return single;
    };
}
```

## setMediaEntities<sup>23+</sup>

setMediaEntities(entities: MediaEntity[]): Promise&lt;void&gt;

向音频模板控制方同步媒体资源变更信息。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明             |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| entities | [MediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#mediaentity23)[] | 是   | 媒体实体的数组。 |

**返回值：**

| 类型                | 说明         |
| ------------------- | ------------ |
| Promise&lt;void&gt; | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * 媒体播放后信息后，如：歌单的播放状态
     */
    public setMediaEntities() {
        let mediaEntities: avMusicTemplate.MediaEntity[] = [{
            mediaId: 'mediaId',
            mediaType: avMusicTemplate.EntityType.SINGLE,
            parentId: 'parentId',
            parentMediaType: avMusicTemplate.EntityType.SINGLE,
            title: 'title',
            imageUrl: 'imageUrl',
            playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
        }];
        this.template?.setMediaEntities(mediaEntities);
    };
}
```
## setTabContent<sup>23+</sup>

setTabContent(tabId: string, tabContent: MediaTabContent): Promise&lt;void&gt;

向音频模板控制方同步标签页内容信息。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明             |
| ---------- | ------------------------------------------------------------ | ---- | ---------------- |
| tabId      | string                                                       | 是   | 标签的ID。       |
| tabContent | [MediaTabContent](arkts-apis-avsession-AVMusicTemplate-i.md#mediatabcontent23) | 是   | 媒体标签页内容。 |

**返回值：**

| 类型                | 说明         |
| ------------------- | ------------ |
| Promise&lt;void&gt; | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
    /**
     * 某个tab页签下的内容发生变化后通知界面刷新
     */
    public setTabContent() {
        let mediaEntity: avMusicTemplate.MediaEntity[] = [{
            mediaId: 'mediaId',
            mediaType: avMusicTemplate.EntityType.SINGLE,
            parentId: 'parentId',
            parentMediaType: avMusicTemplate.EntityType.SINGLE,
            title: 'title',
            imageUrl: 'imageUrl',
            playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
        }]
        let compilation: avMusicTemplate.Compilation[] = [{
            errorCode: 0,
            errorMsg: 'success',
            id: 'id',
            title: 'title',
            hasMoreData: true,
            totalSize: 2,
            memberMediaType: avMusicTemplate.EntityType.SINGLE,
            topElements: mediaEntity
        }]
        let mediaTabContent: avMusicTemplate.MediaTabContent = {
            errorCode: 0,
            errorMsg: 'success',
            tabId: 'tabId',
            compilations: compilation
        }
        this.template?.setTabContent('tabId', mediaTabContent);
    };
}
```
## setPlaylist<sup>23+</sup>

setPlaylist(playlist: PageMediaEntity): Promise&lt;void&gt;

向音频模板控制方同步播放列表。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明           |
| -------- | ------------------------------------------------------------ | ---- | -------------- |
| playlist | [PageMediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#pagemediaentity23) | 是   | 分页媒体实体。 |

**返回值：**

| 类型                | 说明         |
| ------------------- | ------------ |
| Promise&lt;void&gt; | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * 播放列表发送变化后通知界面刷新
     */
    public setPlaylist() {
        let mediaEntity: avMusicTemplate.MediaEntity = {
            mediaId: 'mediaId',
            mediaType: avMusicTemplate.EntityType.SINGLE,
            parentId: 'parentId',
            parentMediaType: avMusicTemplate.EntityType.SINGLE,
            title: 'title',
            imageUrl: 'imageUrl',
            playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
        }
        let pageMediaEntity: avMusicTemplate.PageMediaEntity = {
            errorCode: 0,
            errorMsg: 'success',
            pageIndex: 0,
            pageSize: 1,
            hasMoreData: true,
            totalSize: 2,
            memberMediaType: avMusicTemplate.EntityType.SINGLE,
            elements: [mediaEntity]
        }
        this.template?.setPlaylist(pageMediaEntity);
    };
}
```

## setDownloadMediaEntityStatus<sup>23+</sup>

setDownloadMediaEntityStatus(single: MediaEntity): Promise&lt;void&gt;

向音频模板控制方同步单曲下载状态信息。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明       |
| ------ | ------------------------------------------------------------ | ---- | ---------- |
| single | [MediaEntity](arkts-apis-avsession-AVMusicTemplate-i.md#mediaentity23) | 是   | 媒体实体。 |

**返回值：**

| 类型                | 说明         |
| ------------------- | ------------ |
| Promise&lt;void&gt; | 无返回结果。 |

**示例：**

请参考[onDownloadMediaEntity](#ondownloadmediaentity23)的示例。

## setCustomElements<sup>23+</sup>

setCustomElements(actionType: ActionType, customType: CustomType, customElement: CustomElement): Promise&lt;void&gt;

向音频模板控制方同步自定义元素变更信息。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名        | 类型                                                         | 必填 | 说明         |
| ------------- | ------------------------------------------------------------ | ---- | ------------ |
| actionType    | [ActionType](arkts-apis-avsession-AVMusicTemplate-t.md#actiontype23) | 是   | 操作类型。   |
| customType    | [CustomType](arkts-apis-avsession-AVMusicTemplate-t.md#customtype23) | 是   | 自定义类型。 |
| customElement | [CustomElement](arkts-apis-avsession-AVMusicTemplate-i.md#customelement23) | 是   | 自定义元素。 |

**返回值：**

| 类型                | 说明         |
| ------------------- | ------------ |
| Promise&lt;void&gt; | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * 自定义数据发生变化后通知
     */
    public setCustomElements() {
        let mediaEntity: avMusicTemplate.MediaEntity = {
            mediaId: 'mediaId',
            mediaType: avMusicTemplate.EntityType.SINGLE,
            parentId: 'parentId',
            parentMediaType: avMusicTemplate.EntityType.SINGLE,
            title: 'title',
            imageUrl: 'imageUrl',
            playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
        }
        let compilation: avMusicTemplate.Compilation = {
            errorCode: 0,
            errorMsg: 'success',
            id: 'id',
            title: 'title',
            hasMoreData: true,
            totalSize: 2,
            memberMediaType: avMusicTemplate.EntityType.SINGLE,
            topElements: [mediaEntity]
        }
        let customElement: avMusicTemplate.CustomElement = {
            errorCode: 0,
            errorMsg: 'success',
            customCompilations: [compilation]
        }
        this.template?.setCustomElements('add', 'COMPILATION', customElement);
    };
}
```
## setSettings<sup>23+</sup>

setSettings(settingItems: SettingItem[]): Promise&lt;void&gt;

向音频模板控制方同步设置信息。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                                         | 必填 | 说明         |
| ------------ | ------------------------------------------------------------ | ---- | ------------ |
| settingItems | [SettingItem](arkts-apis-avsession-AVMusicTemplate-i.md#settingitem23) | 是   | 设置项数组。 |

**返回值：**

| 类型                | 说明         |
| ------------------- | ------------ |
| Promise&lt;void&gt; | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * 设置项变化后通知
     */
    public setSettings() {
        let settingItems: avMusicTemplate.SettingItem[] = [{
            id: 'id',
            title: 'title',
            desc: 'desc',
            mediaId: 'mediaId',
            settingType: avMusicTemplate.SettingType.SWITCH,
            settingValue: false
        }];
        this.template?.setSettings(settingItems);
    };
}
```

## reportExecuteAction<sup>23+</sup>

reportExecuteAction(actionType: string, params: string): Promise&lt;void&gt;

向音频模板控制方同步执行操作信息。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型   | 必填 | 说明       |
| ---------- | ------ | ---- | ---------- |
| actionType | string | 是   | 行为类型。 |
| params     | string | 是   | 行为信息。 |

**返回值：**

| 类型                | 说明         |
| ------------------- | ------------ |
| Promise&lt;void&gt; | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * 模拟向媒体中心同步执行操作信息
     */
    public reportExecuteAction() {
        let actionType: string = 'actionType';
        let params: string = 'params';
        this.template?.reportExecuteAction(actionType, params);
    };
}
```

## setExtensionAbility<sup>23+</sup>

setExtensionAbility(want: WantAgent): Promise&lt;void&gt;

向音频模板控制方同步用于被拉起的Ability。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明       |
| ------ | ------------------------------------------------------------ | ---- | ---------- |
| want   | [WantAgent](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#WantAgent) | 是   | 能力信息。 |

**返回值：**

| 类型                | 说明         |
| ------------------- | ------------ |
| Promise&lt;void&gt; | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';
import { wantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * 媒体应用需要拉起应用的自定义界面时调用
     */
    public setExtensionAbility() {
        let wantAgentInfo: wantAgent.WantAgentInfo = {
            wants: [
                {
                    bundleName: "com.example.templateprovider",
                    abilityName: 'EntryAbility',
                    type: 'action',
                    parameters: {
                        'ability.want.params.uiExtensionType': 'action'
                    }
                }
            ],
            actionType: wantAgent.OperationType.START_ABILITIES,
            requestCode: 0
        }
        wantAgent.getWantAgent(wantAgentInfo).then((agent) => {
            this.template?.setExtensionAbility(agent);
        }).catch((e: BusinessError) => {
            console.error(`getWantAgent, errCode: ${e?.code}`);
        })
    };
}
```


## destroy<sup>23+</sup>

destroy(): Promise&lt;void&gt;

销毁音频模板实例。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型                | 说明         |
| ------------------- | ------------ |
| Promise&lt;void&gt; | 无返回结果。 |

**示例：**

```ts
import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  public unregisterListener() {
    this.template?.destroy();
    this.template = undefined;
  }
}
```