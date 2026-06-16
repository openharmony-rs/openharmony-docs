# Class (AVMusicTemplate)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->

After calling [avMusicTemplate.createAVMusicTemplate](arkts-apis-avMusicTemplate-f.md#avmusictemplatecreateavmusictemplate) to obtain an instance, you can obtain the instance ID, start the audio template page, and configure the data obtaining method. Then, you can synchronize the data to the template controller to complete the subsequent operations.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This module applies only to cars running API version 23 or later.

## Modules to Import

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## Properties

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| Name      | Type  | Read-Only| Optional| Description                |
| :--------- | :----- | :--- | :--- | :------------------- |
| sessionId  | string | No  | No  | Unique ID of the audio template.|
| sessionTag | string | No  | No  | Audio template tag.      |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private static sInstance: TemplateManager;

  private constructor() {
  }

  /**
   * Obtain the template controller instance.
   *
   * @returns Template controller instance.
   */
  public static getInstance(): TemplateManager {
    if (!TemplateManager.sInstance) {
      TemplateManager.sInstance = new TemplateManager();
    }
    return TemplateManager.sInstance;
  };

  /**
   * Create an audio template.
   */
  public createTemplate() {
    if (this.template) {
      console.warn('createTemplate: template not undefined');
      return
    }
    this.template = avMusicTemplate.createAVMusicTemplate(avMusicTemplate.AVMusicTemplateType.DEFAULT);
    console.info('Succeeded in creating template.');
  }
}
```

## startTemplate

startTemplate(): Promise&lt;OperResult&gt;

Starts an audio template page. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type                                                        | Description                                         |
| ------------------------------------------------------------ | --------------------------------------------- |
| Promise\<[OperResult](arkts-apis-avMusicTemplate-i.md#operresult)> | Promise used to return the result of starting an audio template page.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ------------------------- |
| 801      | capability not supported. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Simulate the starting of a template.
   */
  public startTemplate() {
    this.template?.startTemplate();
  }
}
```

## onQueryMainTabs

onQueryMainTabs(callback: QueryMainTabsEvent): void

Registers a listener for the main tab query event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                          |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| callback | [QueryMainTabsEvent](arkts-apis-avMusicTemplate-t.md#querymaintabsevent) | Yes  | Callback used to return the main tab query event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQueryMainTabs can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryMainTabsEvent: avMusicTemplate.QueryMainTabsEvent = async () => {
    return new Promise<avMusicTemplate.MediaTab[]>(async (resolve, reject) => {
      let tabs: avMusicTemplate.MediaTab[] = await this.getMainTabs();
      resolve(tabs);
    });
  };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQueryMainTabs(this.queryMainTabsEvent);
  }

  /**
   * Simulate the obtaining of all tabs on the home page.
   *
   * @returns Promise used to return an array of MediaTab.
   */
  private async getMainTabs(): Promise<avMusicTemplate.MediaTab[]> {
    let homeTab: avMusicTemplate.MediaTab = {
      tabId: 'home',
      tabName: 'Home'
    };
    let mineTab: avMusicTemplate.MediaTab = {
      tabId: 'mine',
      tabName: 'Me'
    };
    let mainTabs: avMusicTemplate.MediaTab[] = [homeTab, mineTab];
    return mainTabs;
  };
}
```

## offQueryMainTabs

offQueryMainTabs(callback?: QueryMainTabsEvent): void

Unregisters the listener for the main tab query event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                  |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------ |
| callback | [QueryMainTabsEvent](arkts-apis-avMusicTemplate-t.md#querymaintabsevent) | No  | Main tab query event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQueryMainTabs can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQueryMainTabs();
  }
}
```

## onQueryMediaTabContent

onQueryMediaTabContent(callback: QueryMediaTabContentEvent): void

Registers a listener for the media tab content query event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                    |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------- |
| callback | [QueryMediaTabContentEvent](arkts-apis-avMusicTemplate-t.md#querymediatabcontentevent) | Yes  | Callback used to return the media tab content query event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQueryMediaTabContent can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryMediaTabContentEvent: avMusicTemplate.QueryMediaTabContentEvent = async (tabId: string) => {
    return new Promise<avMusicTemplate.MediaTabContent>(async (resolve, reject) => {
      let tabContent: avMusicTemplate.MediaTabContent = await this.createMediaTabContent();
      resolve(tabContent);
    });
  };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQueryMediaTabContent(this.queryMediaTabContentEvent);
  }

  /**
   * Simulate the obtaining of tab content.
   *
   * @returns Tab content.
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
   * Simulate the obtaining of compilation data.
   *
   * @returns Compilation data.
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
   * Simulate the obtaining of media data.
   *
   * @returns Media data.
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

## offQueryMediaTabContent

offQueryMediaTabContent(callback?: QueryMediaTabContentEvent): void

Unregisters the listener for the media tab content query event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [QueryMediaTabContentEvent](arkts-apis-avMusicTemplate-t.md#querymediatabcontentevent) | No  | Callback used to return the media tab content query event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQueryMediaTabContent can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQueryMediaTabContent();
  }
}
```

## onQueryMediaEntity

onQueryMediaEntity(callback: QueryMediaEntityEvent): void

Registers a listener for the media entity query event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                              |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| callback | [QueryMediaEntityEvent](arkts-apis-avMusicTemplate-t.md#querymediaentityevent) | Yes  | Callback used to return the media entity query event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQueryMediaEntity can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryMediaEntityEvent: avMusicTemplate.QueryMediaEntityEvent =
    async (params: avMusicTemplate.QueryMediaEntityParam) => {
      return new Promise<avMusicTemplate.PageMediaEntity>(async (resolve, reject) => {
        let pageMediaEntity: avMusicTemplate.PageMediaEntity = await this.createPageMediaEntity();
        resolve(pageMediaEntity);
      });
    };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQueryMediaEntity(this.queryMediaEntityEvent);
  }

  /**
   * Simulate the obtaining of PageMediaEntity.
   *
   * @returns The PageMediaEntity instance.
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
   * Simulate the obtaining of media data.
   *
   * @returns Media data.
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

## offQueryMediaEntity

offQueryMediaEntity(callback?: QueryMediaEntityEvent): void

Unregisters the listener for the media entity query event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                      |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| callback | [QueryMediaEntityEvent](arkts-apis-avMusicTemplate-t.md#querymediaentityevent) | No  | Media entity query event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQueryMediaEntity can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQueryMediaEntity();
  }
}
```

## onQueryCompilation

onQueryCompilation(callback: QueryCompilationEvent): void

Registers a listener for the compilation query event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                          |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| callback | [QueryCompilationEvent](arkts-apis-avMusicTemplate-t.md#querycompilationevent) | Yes  | Callback used to return the compilation query event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQueryCompilation can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryCompilationEvent: avMusicTemplate.QueryCompilationEvent =
    async (compilationId: string, pageIndex: number) => {
      return new Promise<avMusicTemplate.PageMediaEntity>(async (resolve, reject) => {
        let pageMediaEntity: avMusicTemplate.PageMediaEntity = await this.createPageMediaEntity();
        resolve(pageMediaEntity);
      });
    };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQueryCompilation(this.queryCompilationEvent);
  }

  /**
   * Simulate the obtaining of PageMediaEntity.
   *
   * @returns The PageMediaEntity instance.
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
   * Simulate the obtaining of media data.
   *
   * @returns Media data.
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

## offQueryCompilation

offQueryCompilation(callback?: QueryCompilationEvent): void

Unregisters the listener for the compilation query event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                  |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------ |
| callback | [QueryCompilationEvent](arkts-apis-avMusicTemplate-t.md#querycompilationevent) | No  | Compilation query event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQueryCompilation can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQueryCompilation();
  }
}
```

## onQueryPlaylist

onQueryPlaylist(callback: QueryPlaylistEvent): void

Registers a listener for the playlist query event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                              |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| callback | [QueryPlaylistEvent](arkts-apis-avMusicTemplate-t.md#queryplaylistevent) | Yes  | Callback used to return the playlist query event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQueryPlaylist can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryPlaylistEvent: avMusicTemplate.QueryPlaylistEvent =
    async (pageIndex: number, sort: avMusicTemplate.Sort) => {
      return new Promise<avMusicTemplate.PageMediaEntity>(async (resolve, reject) => {
        let pageMediaEntity: avMusicTemplate.PageMediaEntity = await this.createPageMediaEntity();
        resolve(pageMediaEntity);
      });
    };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQueryPlaylist(this.queryPlaylistEvent);
  }

  /**
   * Simulate the obtaining of PageMediaEntity.
   *
   * @returns The PageMediaEntity instance.
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
   * Simulate the obtaining of media data.
   *
   * @returns Media data.
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

## offQueryPlaylist

offQueryPlaylist(callback?: QueryPlaylistEvent): void

Unregisters the listener for the playlist query event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                      |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| callback | [QueryPlaylistEvent](arkts-apis-avMusicTemplate-t.md#queryplaylistevent) | No  | Playlist query event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQueryPlaylist can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQueryPlaylist();
  }
}
```

## onQueryCurrentSingle

onQueryCurrentSingle(callback: QueryCurrentSingleEvent): void

Registers a listener for the event of querying the current single track. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                              |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| callback | [QueryCurrentSingleEvent](arkts-apis-avMusicTemplate-t.md#querycurrentsingleevent) | Yes  | Callback used to return the event of querying the current single track.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQueryCurrentSingle can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryCurrentSingleEvent: avMusicTemplate.QueryCurrentSingleEvent = async () => {
    return new Promise<avMusicTemplate.Single>(async (resolve, reject) => {
      let single: avMusicTemplate.Single = await this.createCurrentSingle();
      resolve(single);
    });
  };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQueryCurrentSingle(this.queryCurrentSingleEvent);
  }

  /**
   * Simulate the obtaining of the current single track.
   *
   * @returns The current single track.
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
      title: 'Track title',
      desc: 'Track description',
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

## offQueryCurrentSingle

offQueryCurrentSingle(callback?: QueryCurrentSingleEvent): void

Unregisters the listener for the event of querying the current single track.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                      |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| callback | [QueryCurrentSingleEvent](arkts-apis-avMusicTemplate-t.md#querycurrentsingleevent) | No  | Event of querying the current single track. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQueryCurrentSingle can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQueryCurrentSingle();
  }
}
```

## onQueryCompilationByKeyword

onQueryCompilationByKeyword(callback: QueryCompilationByKeywordEvent): void

Registers a listener for the event of querying compilations by keyword. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                  |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| callback | [QueryCompilationByKeywordEvent](arkts-apis-avMusicTemplate-t.md#querycompilationbykeywordevent) | Yes  | Callback used to return the event of querying compilations by keyword.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQueryCompilationByKeyword can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryCompilationByKeywordEvent: avMusicTemplate.QueryCompilationByKeywordEvent = async (keyword: string) => {
    return new Promise<avMusicTemplate.Compilation[]>(async (resolve, reject) => {
      let compilation: avMusicTemplate.Compilation = await this.createCompilation();
      let compilations: avMusicTemplate.Compilation[] = [compilation];
      resolve(compilations);
    });
  };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQueryCompilationByKeyword(this.queryCompilationByKeywordEvent);
  }

  /**
   * Simulate the obtaining of compilation data.
   *
   * @returns Compilation data.
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
   * Simulate the obtaining of media data.
   *
   * @returns Media data.
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

## offQueryCompilationByKeyword

offQueryCompilationByKeyword(callback?: QueryCompilationByKeywordEvent): void

Unregisters the listener for the event of querying compilations by keyword.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [QueryCompilationByKeywordEvent](arkts-apis-avMusicTemplate-t.md#querycompilationbykeywordevent) | No  | Event of querying compilations by keyword. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQueryCompilationByKeyword can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQueryCompilationByKeyword();
  }
}
```

## onQueryMediaEntityByKeyword

onQueryMediaEntityByKeyword(callback: QueryMediaEntityByKeywordEvent): void

Registers a listener for the event of querying media entities by keyword. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                      |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------ |
| callback | [QueryMediaEntityByKeywordEvent](arkts-apis-avMusicTemplate-t.md#querymediaentitybykeywordevent) | Yes  | Callback used to return the event of querying media entities by keyword.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQueryMediaEntityByKeyword can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryMediaEntityByKeywordEvent: avMusicTemplate.QueryMediaEntityByKeywordEvent =
    async (keyword: string, searchType: avMusicTemplate.EntityType, pageIndex: number) => {
      return new Promise<avMusicTemplate.PageMediaEntity>(async (resolve, reject) => {
        let pageMediaEntity: avMusicTemplate.PageMediaEntity = await this.createPageMediaEntity();
        resolve(pageMediaEntity);
      });
    };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQueryMediaEntityByKeyword(this.queryMediaEntityByKeywordEvent);
  }

  /**
   * Simulate the obtaining of PageMediaEntity.
   *
   * @returns The PageMediaEntity instance.
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
   * Simulate the obtaining of media data.
   *
   * @returns Media data.
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

## offQueryMediaEntityByKeyword

offQueryMediaEntityByKeyword(callback?: QueryMediaEntityByKeywordEvent): void

Unregisters the listener for the event of querying media entities by keyword.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [QueryMediaEntityByKeywordEvent](arkts-apis-avMusicTemplate-t.md#querymediaentitybykeywordevent) | No  | Event of querying media entities by keyword. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQueryMediaEntityByKeyword can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQueryMediaEntityByKeyword();
  }
}
```

## onQueryRecommendMediaEntityList

onQueryRecommendMediaEntityList(callback: QueryRecommendMediaEntityListEvent): void

Registers a listener for the event of querying the recommended media list. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                  |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| callback | [QueryRecommendMediaEntityListEvent](arkts-apis-avMusicTemplate-t.md#queryrecommendmediaentitylistevent) | Yes  | Callback used to return the event of querying the recommended media list.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQueryRecommendMediaEntityList can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryRecommendMediaEntityListEvent: avMusicTemplate.QueryRecommendMediaEntityListEvent = async () => {
    return new Promise<avMusicTemplate.MediaEntity[]>(async (resolve, reject) => {
      let mediaEntity: avMusicTemplate.MediaEntity = await this.createMediaEntity();
      let mediaEntities: avMusicTemplate.MediaEntity[] = [mediaEntity];
      resolve(mediaEntities);
    });
  };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQueryRecommendMediaEntityList(this.queryRecommendMediaEntityListEvent);
  }

  /**
   * Simulate the obtaining of media data.
   *
   * @returns Media data.
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

## offQueryRecommendMediaEntityList

offQueryRecommendMediaEntityList(callback?: QueryRecommendMediaEntityListEvent): void

Unregisters the listener for the event of querying the recommended media list.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [QueryRecommendMediaEntityListEvent](arkts-apis-avMusicTemplate-t.md#queryrecommendmediaentitylistevent) | No  | Event of querying the recommended media list. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQueryRecommendMediaEntityList can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQueryRecommendMediaEntityList();
  }
}
```

## onQueryHotWords

onQueryHotWords(callback: QueryHotWordsEvent): void

Registers a listener for the hot word query event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                          |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| callback | [QueryHotWordsEvent](arkts-apis-avMusicTemplate-t.md#queryhotwordsevent) | Yes  | Callback used to return the hot word query event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQueryHotWords can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryHotWordsEvent: avMusicTemplate.QueryHotWordsEvent = async () => {
    return new Promise<string[]>(async (resolve, reject) => {
      let hotWords: string[] = ['hot word 1', 'hot word 2', 'hot word 3', 'hot word 4', 'hot word 5'];
      resolve(hotWords);
    });
  };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQueryHotWords(this.queryHotWordsEvent);
  }
}
```

## offQueryHotWords

offQueryHotWords(callback?: QueryHotWordsEvent): void

Unregisters the listener for the hot word query event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                  |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------ |
| callback | [QueryHotWordsEvent](arkts-apis-avMusicTemplate-t.md#queryhotwordsevent) | No  | Hot word query event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQueryHotWords can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQueryHotWords();
  }
}
```

## onQuerySearchHistory

onQuerySearchHistory(callback: QuerySearchHistoryEvent): void

Registers a listener for the search history query event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                              |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| callback | [QuerySearchHistoryEvent](arkts-apis-avMusicTemplate-t.md#querysearchhistoryevent) | Yes  | Callback used to return the search history query event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQuerySearchHistory can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private querySearchHistoryEvent: avMusicTemplate.QuerySearchHistoryEvent = async () => {
    return new Promise<string[]>(async (resolve, reject) => {
      let searchHistory: string[] = ['search history 1', 'search history 2', 'search history 3', 'search history 4', 'search history 5'];
      resolve(searchHistory);
    });
  };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQuerySearchHistory(this.querySearchHistoryEvent);
  }
}
```

## offQuerySearchHistory

offQuerySearchHistory(callback?: QuerySearchHistoryEvent): void

Unregisters the listener for the search history query event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                      |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| callback | [QuerySearchHistoryEvent](arkts-apis-avMusicTemplate-t.md#querysearchhistoryevent) | No  | Search history query event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQuerySearchHistory can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQuerySearchHistory();
  }
}
```

## onClearSearchHistory

onClearSearchHistory(callback: ClearSearchHistoryEvent): void

Registers a listener for the event of clearing search history. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                              |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| callback | [ClearSearchHistoryEvent](arkts-apis-avMusicTemplate-t.md#clearsearchhistoryevent) | Yes  | Callback used to return the event of clearing search history.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onClearSearchHistory can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private clearSearchHistoryEvent: avMusicTemplate.ClearSearchHistoryEvent = async () => {
    return new Promise<avMusicTemplate.OperResult>(async (resolve, reject) => {
      let operResult: avMusicTemplate.OperResult = await this.createOperResult();
      resolve(operResult);
    });
  };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onClearSearchHistory(this.clearSearchHistoryEvent);
  }

  /**
   * Simulate the operation result.
   *
   * @returns Operation result.
   */
  private async createOperResult(): Promise<avMusicTemplate.OperResult> {
    let operResult: avMusicTemplate.OperResult = {
      errorCode: 0,
    }
    return operResult;
  };
}
```

## offClearSearchHistory

offClearSearchHistory(callback?: ClearSearchHistoryEvent): void

Unregisters the listener for the event of clearing search history.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                      |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| callback | [ClearSearchHistoryEvent](arkts-apis-avMusicTemplate-t.md#clearsearchhistoryevent) | No  | Event of clearing search history. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offClearSearchHistory can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offClearSearchHistory();
  }
}
```

## onLogin

onLogin(callback: LoginEvent): void

Registers a listener for the login event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                    |
| -------- | ------------------------------------------------------------ | ---- | ------------------------ |
| callback | [LoginEvent](arkts-apis-avMusicTemplate-t.md#loginevent) | Yes  | Callback used to return the login event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onLogin can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private loginEvent: avMusicTemplate.LoginEvent = async (controlType: avMusicTemplate.LoginType, id?: string) => {
    return new Promise<avMusicTemplate.QrCodeInfo[]>(async (resolve, reject) => {
      let qrCodeInfo: avMusicTemplate.QrCodeInfo = await this.createQrCodeInfo();
      let qrCodeInfos: avMusicTemplate.QrCodeInfo[] = [qrCodeInfo];
      resolve(qrCodeInfos);
    });
  };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onLogin(this.loginEvent);
  }

  /**
   * Simulate the creation of a QR code information array.
   *
   * @returns Promise used to return the QR code information array.
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

## offLogin

offLogin(callback?: LoginEvent): void

Unregisters the listener for the login event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                            |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------ |
| callback | [LoginEvent](arkts-apis-avMusicTemplate-t.md#loginevent) | No  | Login event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offLogin can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offLogin();
  }
}
```

## onRequestDialogInfo

onRequestDialogInfo(callback: RequestDialogInfoEvent): void

Registers a listener for the event of requesting dialog box information. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------ |
| callback | [RequestDialogInfoEvent](arkts-apis-avMusicTemplate-t.md#requestdialoginfoevent) | Yes  | Callback used to return the event of requesting dialog box information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onRequestDialogInfo can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private requestDialogInfoEvent: avMusicTemplate.RequestDialogInfoEvent =
    async (actionType: avMusicTemplate.DialogActionType, actionInfo?: avMusicTemplate.DialogActionInfo) => {
      return new Promise<avMusicTemplate.DialogInfo>(async (resolve, reject) => {
        let dialogInfo: avMusicTemplate.DialogInfo = await this.createDialogInfo();
        resolve(dialogInfo);
      });
    };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onRequestDialogInfo(this.requestDialogInfoEvent);
  }

  /**
   * Simulate dialog box information.
   *
   * @returns Dialog box information.
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

## offRequestDialogInfo

offRequestDialogInfo(callback?: RequestDialogInfoEvent): void

Unregisters the listener for the event of requesting dialog box information.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [RequestDialogInfoEvent](arkts-apis-avMusicTemplate-t.md#requestdialoginfoevent) | No  | Event of requesting dialog box information. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offRequestDialogInfo can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offRequestDialogInfo();
  }
}
```

## onHandleMemberPurchase

onHandleMemberPurchase(callback: HandleMemberPurchaseEvent): void

Registers a listener for the membership purchase handling event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                              |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| callback | [HandleMemberPurchaseEvent](arkts-apis-avMusicTemplate-t.md#handlememberpurchaseevent) | Yes  | Callback used to return the membership purchase handling event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onHandleMemberPurchase can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private handleMemberPurchaseEvent: avMusicTemplate.HandleMemberPurchaseEvent =
    async (info: avMusicTemplate.MemberPurchaseInfo) => {
      return new Promise<avMusicTemplate.DialogInfo>(async (resolve, reject) => {
        let dialogInfo: avMusicTemplate.DialogInfo = await this.createDialogInfo();
        resolve(dialogInfo);
      });
    };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onHandleMemberPurchase(this.handleMemberPurchaseEvent);
  }

  /**
   * Simulate dialog box information.
   *
   * @returns Dialog box information.
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

## offHandleMemberPurchase

offHandleMemberPurchase(callback?: HandleMemberPurchaseEvent): void

Unregisters the listener for the membership purchase handling event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                      |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| callback | [HandleMemberPurchaseEvent](arkts-apis-avMusicTemplate-t.md#handlememberpurchaseevent) | No  | Membership purchase handling event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offHandleMemberPurchase can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offHandleMemberPurchase();
  }
}
```

## onQueryMemberPurchase

onQueryMemberPurchase(callback: QueryMemberPurchaseEvent): void

Registers a listener for the membership purchase query event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                              |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| callback | [QueryMemberPurchaseEvent](arkts-apis-avMusicTemplate-t.md#querymemberpurchaseevent) | Yes  | Callback used to return the membership purchase query event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQueryMemberPurchase can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryMemberPurchaseEvent: avMusicTemplate.QueryMemberPurchaseEvent =
    async (memberPurchaseType: avMusicTemplate.MemberPurchaseType) => {
      return new Promise<avMusicTemplate.MemberPurchaseInfo[]>(async (resolve, reject) => {
        let memberPurchaseInfo: avMusicTemplate.MemberPurchaseInfo = await this.createQueryMemberPurchase();
        let memberPurchaseInfos: avMusicTemplate.MemberPurchaseInfo[] = [memberPurchaseInfo];
        resolve(memberPurchaseInfos);
      });
    };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQueryMemberPurchase(this.queryMemberPurchaseEvent);
  }

  /**
   * Simulates the query of membership purchase information.
   *
   * @returns Promise used to return the membership purchase information array.
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

## offQueryMemberPurchase

offQueryMemberPurchase(callback?: QueryMemberPurchaseEvent): void

Unregisters the listener for the membership purchase query event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                      |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| callback | [QueryMemberPurchaseEvent](arkts-apis-avMusicTemplate-t.md#querymemberpurchaseevent) | No  | Membership purchase query event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQueryMemberPurchase can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQueryMemberPurchase();
  }
}
```

## onQueryCustomContent

onQueryCustomContent(callback: QueryCustomContentEvent): void

Registers a listener for the custom content query event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------ |
| callback | [QueryCustomContentEvent](arkts-apis-avMusicTemplate-t.md#querycustomcontentevent) | Yes  | Callback used to return the custom content query event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onQueryCustomContent can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private queryCustomContentEvent: avMusicTemplate.QueryCustomContentEvent =
    async (queryTypes: avMusicTemplate.CustomType[]) => {
      return new Promise<avMusicTemplate.CustomElement>(async (resolve, reject) => {
        let customElement: avMusicTemplate.CustomElement = await this.createCustomContent();
        resolve(customElement);
      });
    };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onQueryCustomContent(this.queryCustomContentEvent);
  }

  /**
   * Simulate the obtaining of custom content.
   *
   * @returns Custom element.
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

## offQueryCustomContent

offQueryCustomContent(callback?: QueryCustomContentEvent): void

Unregisters the listener for the custom content query event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [QueryCustomContentEvent](arkts-apis-avMusicTemplate-t.md#querycustomcontentevent) | No  | Custom content query event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offQueryCustomContent can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offQueryCustomContent();
  }
}
```

## onDownloadMediaEntity

onDownloadMediaEntity(callback: DownloadMediaEntityEvent): void

Registers a listener for the media entity download event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                              |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| callback | [DownloadMediaEntityEvent](arkts-apis-avMusicTemplate-t.md#downloadmediaentityevent) | Yes  | Callback used to return the media entity download event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onDownloadMediaEntity can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private downloadMediaEntityEvent: avMusicTemplate.DownloadMediaEntityEvent =
    async (controlType: avMusicTemplate.DownloadControlType, mediaEntity: avMusicTemplate.MediaEntity) => {
      return new Promise<avMusicTemplate.OperResult>(async (resolve, reject) => {
        let operResult: avMusicTemplate.OperResult = await this.createOperResult();
        this.downloadMediaEntity(mediaEntity);
        resolve(operResult);
      });
    };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onDownloadMediaEntity(this.downloadMediaEntityEvent);
  }

  /**
   * Download status and progress update.
   */
  public setDownloadMediaEntityStatus(mediaEntity: avMusicTemplate.MediaEntity) {
    this.template?.setDownloadMediaEntityStatus(mediaEntity);
  };

  /**
   * Simulate a settings change.
   *
   * @returns Promise used to return the settings item.
   */
  /**
   * Simulate the operation result.
   *
   * @returns Operation result.
   */
  private async createOperResult(): Promise<avMusicTemplate.OperResult> {
    let operResult: avMusicTemplate.OperResult = {
      errorCode: 0,
    }
    return operResult;
  };

  /**
   * Simulate the download process.
   *
   * @param mediaEntity Media entity.
   */
  private async downloadMediaEntity(mediaEntity: avMusicTemplate.MediaEntity) {
    // After the download is complete.
    this.setDownloadMediaEntityStatus(mediaEntity);
  };
}
```

## offDownloadMediaEntity

offDownloadMediaEntity(callback?: DownloadMediaEntityEvent): void

Unregisters the listener for the media entity download event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                      |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| callback | [DownloadMediaEntityEvent](arkts-apis-avMusicTemplate-t.md#downloadmediaentityevent) | No  | Media entity download event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offDownloadMediaEntity can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offDownloadMediaEntity();
  }
}
```

## onSettingsChange

onSettingsChange(callback: SettingsChangeEvent): void

Registers a listener for the settings change event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                          |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| callback | [SettingsChangeEvent](arkts-apis-avMusicTemplate-t.md#settingschangeevent) | Yes  | Callback used to return the settings change event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onSettingsChange can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private settingsChangeEvent: avMusicTemplate.SettingsChangeEvent =
    async (settingItem: avMusicTemplate.SettingItem) => {
      return new Promise<avMusicTemplate.SettingItem>(async (resolve, reject) => {
        let settingItem: avMusicTemplate.SettingItem = await this.settingsChange();
        resolve(settingItem);
      });
    };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onSettingsChange(this.settingsChangeEvent);
  }

  /**
   * Simulate a settings change.
   *
   * @returns Promise used to return the settings item.
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

## offSettingsChange

offSettingsChange(callback?: SettingsChangeEvent): void

Unregisters the listener for the settings change event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                  |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------ |
| callback | [SettingsChangeEvent](arkts-apis-avMusicTemplate-t.md#settingschangeevent) | No  | Settings change event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offSettingsChange can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offSettingsChange();
  }
}
```

## onProblemAndAdvice

onProblemAndAdvice(callback: ProblemAndAdviceEvent): void

Registers a listener for the problem and advice event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                  |
| -------- | ------------------------------------------------------------ | ---- | ---------------------- |
| callback | [ProblemAndAdviceEvent](arkts-apis-avMusicTemplate-t.md#problemandadviceevent) | Yes  | Callback used to return the problem and advice event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onProblemAndAdvice can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private problemAndAdviceEvent: avMusicTemplate.ProblemAndAdviceEvent = async (advice: string) => {
    return new Promise<avMusicTemplate.OperResult>(async (resolve, reject) => {
      let operResult: avMusicTemplate.OperResult = await this.createOperResult();
      resolve(operResult);
    });
  };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onProblemAndAdvice(this.problemAndAdviceEvent);
  }

  /**
   * Simulate the operation result.
   *
   * @returns Operation result.
   */
  private async createOperResult(): Promise<avMusicTemplate.OperResult> {
    let operResult: avMusicTemplate.OperResult = {
      errorCode: 0,
    }
    return operResult;
  };
}
```

## offProblemAndAdvice

offProblemAndAdvice(callback?: ProblemAndAdviceEvent): void

Unregisters the listener for the problem and advice event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [ProblemAndAdviceEvent](arkts-apis-avMusicTemplate-t.md#problemandadviceevent) | No  | Callback for handling the problem and advice event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offProblemAndAdvice can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offProblemAndAdvice();
  }
}
```

## onPlayForSearch

onPlayForSearch(callback: PlayForSearchEvent): void

Registers a listener for the search and playback event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                      |
| -------- | ------------------------------------------------------------ | ---- | -------------------------- |
| callback | [PlayForSearchEvent](arkts-apis-avMusicTemplate-t.md#playforsearchevent) | Yes  | Callback used to return the search and playback event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onPlayForSearch can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private playForSearchEvent: avMusicTemplate.PlayForSearchEvent = async (command: avMusicTemplate.SearchPlayInfoType,
    args: avMusicTemplate.SearchPlayInfo) => {
    return new Promise<avMusicTemplate.OperResult>(async (resolve, reject) => {
      let operResult: avMusicTemplate.OperResult = await this.createOperResult();
      resolve(operResult);
    });
  };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onPlayForSearch(this.playForSearchEvent);
  }

  /**
   * Simulate the operation result.
   *
   * @returns Operation result.
   */
  private async createOperResult(): Promise<avMusicTemplate.OperResult> {
    let operResult: avMusicTemplate.OperResult = {
      errorCode: 0,
    }
    return operResult;
  };
}
```

## offPlayForSearch

offPlayForSearch(callback?: PlayForSearchEvent): void

Unregisters the listener for the search and playback event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                              |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------------------- |
| callback | [PlayForSearchEvent](arkts-apis-avMusicTemplate-t.md#playforsearchevent) | No  | Search and playback event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offPlayForSearch can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offPlayForSearch();
  }
}
```

## onExecuteAction

onExecuteAction(callback: ExecuteActionEvent): void

Registers a listener for the action execution event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                          |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| callback | [ExecuteActionEvent](arkts-apis-avMusicTemplate-t.md#executeactionevent) | Yes  | Callback used to return the action execution event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onExecuteAction can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private executeActionEvent: avMusicTemplate.ExecuteActionEvent = async (actionType: string, params: string) => {
    return new Promise<string>(async (resolve, reject) => {
      let result: string = 'success';
      resolve(result);
    });
  };

  /**
   * Register a listener.
   */
  private registerListener() {
    this.template?.onExecuteAction(this.executeActionEvent);
  }
}
```

## offExecuteAction

offExecuteAction(callback?: ExecuteActionEvent): void

Unregisters the listener for the action execution event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                  |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------ |
| callback | [ExecuteActionEvent](arkts-apis-avMusicTemplate-t.md#executeactionevent) | No  | Action execution event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offExecuteAction can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offExecuteAction();
  }
}
```

## onPlayMediaEntity

onPlayMediaEntity(callback: PlayMediaEntityEvent): void

Registers a listener for the media entity playback event. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                              |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| callback | [PlayMediaEntityEvent](arkts-apis-avMusicTemplate-t.md#playmediaentityevent) | Yes  | Callback used to return the media entity playback event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onPlayMediaEntity can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
    private playMediaEntityEvent: avMusicTemplate.PlayMediaEntityEvent =
        async (mediaEntity: avMusicTemplate.MediaEntity) => {
            console.info('playMediaEntity');
        };

    /**
     * Register a listener.
     */
    private registerListener() {
        this.template?.onPlayMediaEntity(this.playMediaEntityEvent);
    }
}
```


## offPlayMediaEntity

offPlayMediaEntity(callback?: PlayMediaEntityEvent): void

Unregisters the listener for the media entity playback event.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                      |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| callback | [PlayMediaEntityEvent](arkts-apis-avMusicTemplate-t.md#playmediaentityevent) | No  | Media entity playback event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offPlayMediaEntity can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offPlayMediaEntity();
  }
}
```

## onFavoriteMediaEntity

onFavoriteMediaEntity(callback: FavoriteMediaEntityEvent): void

Registers a listener for the event of favoriting a media entity. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                              |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| callback | [FavoriteMediaEntityEvent](arkts-apis-avMusicTemplate-t.md#favoritemediaentityevent) | Yes  | Callback used to return the event of favoriting a media entity.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function onFavoriteMediaEntity can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
    private favoriteMediaEntityEvent: avMusicTemplate.FavoriteMediaEntityEvent =
        async (actionType: avMusicTemplate.MediaFavoriteType, mediaEntity: avMusicTemplate.MediaEntity) => {
            return new Promise<avMusicTemplate.OperResult>(async (resolve, reject) => {
                let operResult: avMusicTemplate.OperResult = await this.createOperResult();
                resolve(operResult);
            });
        };

    /**
     * Register a listener.
     */
    private registerListener() {
        this.template?.onFavoriteMediaEntity(this.favoriteMediaEntityEvent);
    }

    /**
     * Simulate the operation result.
     *
     * @returns Operation result.
     */
    private async createOperResult(): Promise<avMusicTemplate.OperResult> {
        let operResult: avMusicTemplate.OperResult = {
            errorCode: 0,
        }
        return operResult;
    };
}
```

## offFavoriteMediaEntity

offFavoriteMediaEntity(callback?: FavoriteMediaEntityEvent): void

Unregisters the listener for the event of favoriting a media entity.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                      |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| callback | [FavoriteMediaEntityEvent](arkts-apis-avMusicTemplate-t.md#favoritemediaentityevent) | No  | Event of favoriting a media entity. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function offFavoriteMediaEntity can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000012 | AVMusicTemplate error.                                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    this.template?.offFavoriteMediaEntity();
  }
}
```

## setUserInfo

setUserInfo(userInfo: UserInfo): Promise&lt;void&gt;

Synchronizes user information to the audio template controller. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description      |
| -------- | ------------------------------------------------------------ | ---- | ---------- |
| userInfo | [UserInfo](arkts-apis-avMusicTemplate-i.md#userinfo) | Yes  | User Information.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function setUserInfo can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000011 | The data write error, data is invalid.                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
    private isLogin: boolean = false;

    /**
     * Simulate a login status change.
     *
     * @param isLogin Whether the user is logged in.
     */
    public setLoginState(isLogin: boolean) {
        this.isLogin = isLogin;
        this.setUserInfo();
    }

    /**
     * Notify the UI to refresh user information after user information changes, such as after a user logs in.
     */
    public setUserInfo() {
        let userInfo: avMusicTemplate.UserInfo = {
            userInfoId: this.isLogin ? 'userInfoId' : '',
            nickName: this.isLogin ? 'nickname' : '',
            profilePicUrl: this.isLogin ? 'profilePicUrl' : '',
            tips: this.isLogin ? 'tips' : '',
            isLogin: this.isLogin,
            isVip: false
        };
        this.template?.setUserInfo(userInfo);
    };
}
```

## setDialogCommand

setDialogCommand(type: DialogControlType, dialogInfo: DialogInfo): Promise&lt;void&gt;

Synchronizes the dialog box command to the audio template controller. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type                                                        | Mandatory| Description            |
| ---------- | ------------------------------------------------------------ | ---- | ---------------- |
| type       | [DialogControlType](arkts-apis-avMusicTemplate-t.md#dialogcontroltype) | Yes  | Dialog box control type.|
| dialogInfo | [DialogInfo](arkts-apis-avMusicTemplate-i.md#dialoginfo) | Yes  | Dialog box information.    |

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function setDialogCommand can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000011 | The data write error, data is invalid.                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * Operations related to the dialog box, such as opening and closing the dialog box.
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
## setCurrentSingle

setCurrentSingle(single: Single): Promise&lt;void&gt;

Synchronizes the current single track to the audio template controller. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type                                                        | Mandatory| Description      |
| ------ | ---------------------------------------------------------- | ---- | ---------- |
| single | [Single](arkts-apis-avMusicTemplate-i.md#single) | Yes  | Current single track.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function setCurrentSingle can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000011 | The data write error, data is invalid.                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    public async setCurrentSingle() {
        let single: avMusicTemplate.Single = await this.createCurrentSingle()
        this.template?.setCurrentSingle(single);
    };

    /**
     * Simulate the obtaining of the current single track.
     *
     * @returns The current single track.
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
            title: 'Track title',
            desc: 'Track description',
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

## setMediaEntities

setMediaEntities(entities: MediaEntity[]): Promise&lt;void&gt;

Synchronizes media resource change information to the audio template controller. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description            |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| entities | [MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity)[] | Yes  | Array of media entities.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function setMediaEntities can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000011 | The data write error, data is invalid.                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * Media playback information, for example, the playback state of a playlist.
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
## setTabContent

setTabContent(tabId: string, tabContent: MediaTabContent): Promise&lt;void&gt;

Synchronizes tab content information to the audio template controller. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type                                                        | Mandatory| Description            |
| ---------- | ------------------------------------------------------------ | ---- | ---------------- |
| tabId      | string                                                       | Yes  | Tag ID.      |
| tabContent | [MediaTabContent](arkts-apis-avMusicTemplate-i.md#mediatabcontent) | Yes  | Media tab content.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function setTabContent can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000011 | The data write error, data is invalid.                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
    /**
     * Notify the UI to refresh when the content on a tab page changes.
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
## setPlaylist

setPlaylist(playlist: PageMediaEntity): Promise&lt;void&gt;

Synchronizes the playlist to the audio template controller. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description          |
| -------- | ------------------------------------------------------------ | ---- | -------------- |
| playlist | [PageMediaEntity](arkts-apis-avMusicTemplate-i.md#pagemediaentity) | Yes  | Pagination media entity.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function setPlaylist can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000011 | The data write error, data is invalid.                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * Notify the UI to refresh after the playlist changes.
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

## setDownloadMediaEntityStatus

setDownloadMediaEntityStatus(single: MediaEntity): Promise&lt;void&gt;

Synchronizes the single track download status to the audio template controller. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type                                                        | Mandatory| Description      |
| ------ | ------------------------------------------------------------ | ---- | ---------- |
| single | [MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity) | Yes  | Media entity.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function setDownloadMediaEntityStatus can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000011 | The data write error, data is invalid.                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  /**
   * Download status and progress update.
   */
  public setDownloadMediaEntityStatus(mediaEntity: avMusicTemplate.MediaEntity) {
    this.template?.setDownloadMediaEntityStatus(mediaEntity);
  };

  /**
   * Simulate the download process.
   *
   * @param mediaEntity Media entity.
   */
  private async downloadMediaEntity(mediaEntity: avMusicTemplate.MediaEntity) {
    // After the download is complete.
    this.setDownloadMediaEntityStatus(mediaEntity);
  };
}
```

## setCustomElements

setCustomElements(actionType: ActionType, customType: CustomType, customElement: CustomElement): Promise&lt;void&gt;

Synchronizes custom element change information to the audio template controller. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name       | Type                                                        | Mandatory| Description        |
| ------------- | ------------------------------------------------------------ | ---- | ------------ |
| actionType    | [ActionType](arkts-apis-avMusicTemplate-t.md#actiontype) | Yes  | Action type.  |
| customType    | [CustomType](arkts-apis-avMusicTemplate-t.md#customtype) | Yes  | Custom type.|
| customElement | [CustomElement](arkts-apis-avMusicTemplate-i.md#customelement) | Yes  | Custom element.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function setCustomElements can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000011 | The data write error, data is invalid.                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * Notification is sent after the custom data changes.
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
## setSettings

setSettings(settingItems: SettingItem[]): Promise&lt;void&gt;

Synchronizes settings information to the audio template controller. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name      | Type                                                        | Mandatory| Description        |
| ------------ | ------------------------------------------------------------ | ---- | ------------ |
| settingItems | [SettingItem](arkts-apis-avMusicTemplate-i.md#settingitem)[] | Yes  | Array of setting items.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function setSettings can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000011 | The data write error, data is invalid.                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * Notification is sent after the settings item changes.
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

## reportExecuteAction

reportExecuteAction(actionType: string, params: string): Promise&lt;void&gt;

Synchronizes action execution information to the audio template controller. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type  | Mandatory| Description      |
| ---------- | ------ | ---- | ---------- |
| actionType | string | Yes  | Action type.|
| params     | string | Yes  | Action information.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function reportExecuteAction can not work correctly due to limited device capabilities. |
| 35000005 | AVMusicTemplate does not exist.                              |
| 35000011 | The data write error, data is invalid.                       |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * Simulates the operation of synchronizing action execution information to the media center.
     */
    public reportExecuteAction() {
        let actionType: string = 'actionType';
        let params: string = 'params';
        this.template?.reportExecuteAction(actionType, params);
    };
}
```

## setExtensionAbility

setExtensionAbility(want: WantAgent): Promise&lt;void&gt;

Synchronizes the ability to be started to the audio template controller. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type                                                        | Mandatory| Description      |
| ------ | ------------------------------------------------------------ | ---- | ---------- |
| want   | [WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md#wantagent) | Yes  | Ability information.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                              |
| -------- | -------------------------------------- |
| 801      | capability not supported.              |
| 35000005 | AVMusicTemplate does not exist.        |
| 35000011 | The data write error, data is invalid. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';
import { wantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export class TemplateManager {
    private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

    /**
     * Called when a media application needs to launch a custom application UI.
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
        })
    };
}
```


## destroy

destroy(): Promise&lt;void&gt;

Destroys an audio template instance. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function destroy can not work correctly due to limited device capabilities. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;

  public unregisterListener() {
    this.template?.destroy();
    this.template = undefined;
  }
}
```
