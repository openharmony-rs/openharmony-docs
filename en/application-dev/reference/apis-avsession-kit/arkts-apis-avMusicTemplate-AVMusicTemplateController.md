# Class (AVMusicTemplateController)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->

Defines the audio template controller, which can be used to obtain the unique ID of the audio template controller and exchange data with the media application accessing the audio template.

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

| Name     | Type   | Read-Only| Optional| Description                                                   |
| :-------- | :------ | :--- | :--- | :------------------------------------------------------ |
| sessionId | string  | No  | No  | Unique ID of the audio template controller.                             |
| isDestroy | boolean | No  | No  | Whether the audio template is destroyed. **true**: yes; **false**: no. No default value.|

## queryMainTabs

queryMainTabs(): Promise&lt;MediaTab[]&gt;

Queries the main tabs. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type                                                        | Description                                 |
| ------------------------------------------------------------ | ------------------------------------- |
| Promise<[MediaTab](arkts-apis-avMusicTemplate-i.md#mediatab)[]> | Promise used to return the array of main tabs.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Query the main label.
   */
  public async queryMainTabs(): Promise<avMusicTemplate.MediaTab[]> {
    let tabs: avMusicTemplate.MediaTab[] = [];
    if (!this.controller) {
      console.info(TAG, 'queryMainTabs: controller is undefined')
      return tabs;
    }
    try {
      console.info(TAG, 'queryMainTabs')
      tabs = await this.controller.queryMainTabs();
    } catch (e) {
      console.error(TAG, `queryMainTabs failed, errCode: ${e?.code}`)
    }
    return tabs;
  }
}
```

## queryMediaTabContent

queryMediaTabContent(tabId: string): Promise&lt;MediaTabContent&gt;

Queries the media tab content. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| tabId  | string | Yes  | Tab ID.|

**Return value**

| Type                                                        | Description                             |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<[MediaTabContent](arkts-apis-avMusicTemplate-i.md#mediatabcontent)> | Promise used to return the media tab content.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the query of the media tab content.
   *
   * @param tabId Tab ID.
   */
  public async queryMediaTabContent(tabId: string): Promise<avMusicTemplate.MediaTabContent | undefined> {
    try {
      let tabContent: avMusicTemplate.MediaTabContent | undefined = await this.controller?.queryMediaTabContent(tabId);
      if (tabContent?.errorCode != 0) {
        console.warn(TAG, 'queryMediaTabContent fail')
        return undefined;
      }
      console.info('Succeeded in querying media tab content.');
      return tabContent;
    } catch (e) {
      console.error(TAG, `queryMediaTabContent failed, errCode: ${e?.code}`)
      return undefined;
    }
  }
}
```

## queryMediaEntity

queryMediaEntity(params: QueryMediaEntityParam): Promise&lt;PageMediaEntity&gt;

Queries a media entity. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type                                                        | Mandatory| Description              |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| params | [QueryMediaEntityParam](arkts-apis-avMusicTemplate-i.md#querymediaentityparam) | Yes  | Parameters for querying the media entity.|

**Return value**

| Type                                                        | Description                                     |
| ------------------------------------------------------------ | ----------------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avMusicTemplate-i.md#pagemediaentity)> | Promise used to return the pagination object of the queried media entity.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the query of the media entity.
   *
   * @returns Media entity on the page.
   */
  public async queryMediaEntity(): Promise<avMusicTemplate.PageMediaEntity | undefined> {
    // Query the media entity.
    let queryMediaEntityParam: avMusicTemplate.QueryMediaEntityParam = {
      entityId: 'entityId',
      pageIndex: 0,
      type: avMusicTemplate.EntityType.SINGLE
    };
    try {
      let pageMediaEntity: avMusicTemplate.PageMediaEntity | undefined =
        await this.controller?.queryMediaEntity(queryMediaEntityParam);
      if (pageMediaEntity?.errorCode != 0) {
        console.warn(TAG, 'queryMediaEntity fail')
        return undefined;
      }
      console.info('Succeeded in querying media entity.');
      return pageMediaEntity;
    } catch (e) {
      console.error(TAG, `queryMediaEntity failed, errCode: ${e?.code}`)
      return undefined;
    }
  }
}
```

## queryCompilation

queryCompilation(compilationId: string, pageIndex: number): Promise&lt;PageMediaEntity&gt;

Queries a compilation. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name       | Type  | Mandatory| Description          |
| ------------- | ------ | ---- | -------------- |
| compilationId | string | Yes  | ID of the compilation.    |
| pageIndex     | number    | Yes  | Index of the tab page.|

**Return value**

| Type                                                        | Description                                   |
| ------------------------------------------------------------ | --------------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avMusicTemplate-i.md#pagemediaentity)> | Promise used to return the pagination object of the queried compilation.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the query of a compilation.
   *
   * @returns Page media entity.
   */
  public async queryCompilation(): Promise<avMusicTemplate.PageMediaEntity | undefined> {
    let compilationId: string = 'compilationId';
    let pageIndex: number = 0;
    try {
      let pageMediaEntity: avMusicTemplate.PageMediaEntity | undefined =
        await this.controller?.queryCompilation(compilationId, pageIndex);
      if (pageMediaEntity?.errorCode != 0) {
        console.warn(TAG, 'queryCompilation fail')
        return undefined;
      }
      console.info('Succeeded in querying compilation.');
      return pageMediaEntity;
    } catch (e) {
      console.error(TAG, `queryCompilation failed, errCode: ${e?.code}`)
      return undefined;
    }
  }
}
```

## queryPlaylist

queryPlaylist(pageIndex: number, sort: Sort): Promise&lt;PageMediaEntity&gt;

Queries a playlist. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name   | Type                                                  | Mandatory| Description                            |
| --------- | ------------------------------------------------------ | ---- | -------------------------------- |
| pageIndex | number                                                 | Yes  | Index of the tab page.                  |
| sort      | [Sort](arkts-apis-avMusicTemplate-e.md#sort) | Yes  | Sorting type of the queried playlist data.|

**Return value**

| Type                                                        | Description                                       |
| ------------------------------------------------------------ | ------------------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avMusicTemplate-i.md#pagemediaentity)> | Promise used to return the pagination object of the queried playlist.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the query of a playlist.
   *
   * @returns Page media entity.
   */
  public async queryPlaylist(): Promise<avMusicTemplate.PageMediaEntity | undefined> {
    let pageIndex: number = 0;
    let sort: avMusicTemplate.Sort = avMusicTemplate.Sort.ORDER;
    try {
      let pageMediaEntity: avMusicTemplate.PageMediaEntity | undefined =
        await this.controller?.queryPlaylist(pageIndex, sort);
      if (pageMediaEntity?.errorCode != 0) {
        console.warn(TAG, 'queryPlaylist fail')
        return undefined;
      }
      console.info('Succeeded in querying playlist.');
      return pageMediaEntity;
    } catch (e) {
      console.error(TAG, `queryPlaylist failed, errCode: ${e?.code}`)
      return undefined;
    }
  }
}
```

## queryCurrentSingle

queryCurrentSingle(): Promise&lt;Single&gt;

Queries the current single track. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type                                                        | Description                       |
| ------------------------------------------------------------ | --------------------------- |
| Promise<[Single](arkts-apis-avMusicTemplate-i.md#single)> | Promise used to return the single track.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the query of the current single track.
   *
   * @returns A single track.
   */
  public async queryCurrentSingle(): Promise<avMusicTemplate.Single | undefined> {
    try {
      let single: avMusicTemplate.Single | undefined = await this.controller?.queryCurrentSingle();
      if (!single?.mediaId || single?.mediaId === '') {
        console.warn(TAG, 'queryCurrentSingle fail')
        return undefined;
      }
      console.info('Succeeded in querying current single.');
      return single;
    } catch (e) {
      console.error(TAG, `queryCurrentSingle failed, errCode: ${e?.code}`)
      return undefined;
    }
  }
}
```

## queryCompilationByKeyword

queryCompilationByKeyword(keyword: string): Promise&lt;Compilation[]&gt;

Queries compilations by keyword. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name | Type  | Mandatory| Description    |
| ------- | ------ | ---- | -------- |
| keyword | string | Yes  | Keyword.|

**Return value**

| Type                                                        | Description                       |
| ------------------------------------------------------------ | --------------------------- |
| Promise<[Compilation](arkts-apis-avMusicTemplate-i.md#compilation)[]> | Promise used to return the array of compilations.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the query of compilations by keyword.
   *
   * @returns Array of compilations.
   */
  public async queryCompilationByKeyword(): Promise<avMusicTemplate.Compilation[]> {
    let compilations: avMusicTemplate.Compilation[] = [];
    if (!this.controller) {
      console.error(TAG, 'queryCompilationByKeyword controller is undefined');
      return compilations;
    }
    let keyword: string = 'keyword';
    try {
      compilations = await this.controller.queryCompilationByKeyword(keyword);
      console.info('Succeeded in querying compilation by keyword.');
    } catch (e) {
      console.error(TAG, `queryCompilationByKeyword failed, errCode: ${e?.code}`)
    }
    return compilations;
  }
}
```

## queryMediaEntityByKeyword

queryMediaEntityByKeyword(keyword: string, searchType: EntityType, pageIndex: number): Promise&lt;PageMediaEntity&gt;

Queries media entities by keyword. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type                                                        | Mandatory| Description          |
| ---------- | ------------------------------------------------------------ | ---- | -------------- |
| keyword    | string                                                       | Yes  | Keyword.      |
| searchType | [EntityType](arkts-apis-avMusicTemplate-e.md#entitytype) | Yes  | Media resource type.|
| pageIndex  | number                                                          | Yes  | Tab index.  |

**Return value**

| Type                                                        | Description                                               |
| ------------------------------------------------------------ | --------------------------------------------------- |
| Promise<[PageMediaEntity](arkts-apis-avMusicTemplate-i.md#pagemediaentity)> | Promise used to return the media entity pagination object related to the keyword.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the query of media entities by keyword.
   *
   * @returns Array of compilations.
   */
  public async queryMediaEntityByKeyword(): Promise<avMusicTemplate.PageMediaEntity | undefined> {
    let keyword: string = 'keyword';
    let searchType: avMusicTemplate.EntityType = avMusicTemplate.EntityType.SINGER;
    let pageIndex: number = 0;
    try {
      let pageMediaEntity: avMusicTemplate.PageMediaEntity | undefined =
        await this.controller?.queryMediaEntityByKeyword(keyword, searchType, pageIndex);
      if (pageMediaEntity?.errorCode != 0) {
        console.warn(TAG, 'queryMediaEntityByKeyword fail')
        return undefined;
      }
      console.info('Succeeded in querying media entity by keyword.');
      return pageMediaEntity;
    } catch (e) {
      console.error(TAG, `queryMediaEntityByKeyword failed, errCode: ${e?.code}`)
    }
    return undefined;
  }
}
```

## queryRecommendMediaEntityList

queryRecommendMediaEntityList(): Promise&lt;MediaEntity[]&gt;

Queries the list of recommended media entities. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type                                                        | Description                                 |
| ------------------------------------------------------------ | ------------------------------------- |
| Promise<[MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity)[]> | Promise used to return the array of recommended media entities.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the query of the list of recommended media entities.
   *
   * @returns Array of media entities.
   */
  public async queryRecommendMediaEntityList(): Promise<avMusicTemplate.MediaEntity[]> {
    let mediaEntities: avMusicTemplate.MediaEntity[] = [];
    if (!this.controller) {
      console.error(TAG, 'queryRecommendMediaEntityList controller is undefined');
      return mediaEntities;
    }
    try {
      mediaEntities = await this.controller.queryRecommendMediaEntityList();
      console.info('Succeeded in querying recommend media entity list.');
    } catch (e) {
      console.error(TAG, `queryRecommendMediaEntityList failed, errCode: ${e?.code}`)
    }
    return mediaEntities;
  }
}
```

## queryHotWords

queryHotWords(): Promise&lt;string[]&gt;

Queries hot words. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type             | Description                       |
| ----------------- | --------------------------- |
| Promise<string[]> | Promise used to return the array of hot words.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the query of hot words.
   *
   * @returns Array of hot words.
   */
  public async queryHotWords(): Promise<string[]> {
    let hotWords: string[] = [];
    if (!this.controller) {
      console.error(TAG, 'queryHotWords controller is undefined');
      return hotWords;
    }
    try {
      hotWords = await this.controller.queryHotWords();
      console.info('Succeeded in querying hot words.');
    } catch (e) {
      console.error(TAG, `queryHotWords failed, errCode: ${e?.code}`)
    }
    return hotWords;
  }
}
```

## querySearchHistory

querySearchHistory(): Promise&lt;string[]&gt;

Queries the search history. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type             | Description                             |
| ----------------- | --------------------------------- |
| Promise<string[]> | Promise used to return the array of search history.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the query of search history.
   *
   * @returns Array of search history.
   */
  public async querySearchHistory(): Promise<string[]> {
    let searchHistory: string[] = [];
    if (!this.controller) {
      console.error(TAG, 'querySearchHistory controller is undefined');
      return searchHistory;
    }
    try {
      searchHistory = await this.controller.querySearchHistory();
      console.info('Succeeded in querying search history.');
    } catch (e) {
      console.error(TAG, `querySearchHistory failed, errCode: ${e?.code}`)
    }
    return searchHistory;
  }
}
```

## clearSearchHistory

clearSearchHistory(): Promise&lt;OperResult&gt;

Clears the search history. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type                                                        | Description                                     |
| ------------------------------------------------------------ | ----------------------------------------- |
| Promise<[OperResult](arkts-apis-avMusicTemplate-i.md#operresult)> | Promise used to return the result of clearing the search history.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the operation of clearing the search history.
   *
   * @returns A boolean value of the Promise type, indicating whether the operation is successful.
   */
  public async clearSearchHistory(): Promise<boolean> {
    try {
      let operResult: avMusicTemplate.OperResult | undefined = await this.controller?.clearSearchHistory()
      if (operResult?.errorCode != 0) {
        console.warn(TAG, 'clearSearchHistory fail');
        return false;
      }
      console.info('Succeeded in clearing search history.');
      return true;
    } catch (e) {
      console.error(TAG, `clearSearchHistory failed, errCode: ${e?.code}`);
      return false;
    }
  }
}
```

## updateSettings

updateSettings(settingItem: SettingItem): Promise&lt;SettingItem&gt;

Updates the settings. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name     | Type                                                        | Mandatory| Description            |
| ----------- | ------------------------------------------------------------ | ---- | ---------------- |
| settingItem | [SettingItem](arkts-apis-avMusicTemplate-i.md#settingitem) | Yes  | Setting item to be updated.|

**Return value**

| Type                                                        | Description                             |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<[SettingItem](arkts-apis-avMusicTemplate-i.md#settingitem)> | Promise used to return the updated settings.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the settings update.
   *
   * @returns Promise used to return the updated settings.
   */
  public async updateSettings(): Promise<avMusicTemplate.SettingItem | undefined> {
    let settingItem: avMusicTemplate.SettingItem = {
      id: 'id',
      title: 'title',
      desc: 'desc',
      mediaId: 'mediaId',
      settingType: avMusicTemplate.SettingType.SWITCH,
      settingValue: false
    };
    try {
      let setting: avMusicTemplate.SettingItem | undefined = await this.controller?.updateSettings(settingItem);
      if (!setting?.id || setting?.id !== settingItem.id) {
        console.warn(TAG, 'updateSettings fail')
        return settingItem;
      }
      console.info('Succeeded in updating settings.');
      return setting;
    } catch (e) {
      console.error(TAG, `updateSettings failed, errCode: ${e?.code}`)
      return settingItem;
    }
  }
}
```

## reportProblemAndAdvice

reportProblemAndAdvice(advice: string): Promise&lt;OperResult&gt;

Reports a problem and a piece of advice. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| advice | string | Yes  | Problem or advice.|

**Return value**

| Type                                                        | Description                                       |
| ------------------------------------------------------------ | ------------------------------------------- |
| Promise<[OperResult](arkts-apis-avMusicTemplate-i.md#operresult)> | Promise used to return the result of reporting a problem and a piece of advice.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the reporting of a problem and a piece of advice.
   *
   * @returns Promise used to return the result. true: success; false: failure.
   */
  public async reportProblemAndAdvice(): Promise<boolean> {
    let advice: string = 'advice';
    try {
      let operResult: avMusicTemplate.OperResult | undefined = await this.controller?.reportProblemAndAdvice(advice);
      if (operResult?.errorCode != 0) {
        console.warn(TAG, 'reportProblemAndAdvice fail')
        return false;
      }
      console.info('Succeeded in reporting problem and advice.');
      return true;
    } catch (e) {
      console.error(TAG, `reportProblemAndAdvice failed, errCode: ${e?.code}`)
      return false;
    }
  }
}
```

## login

login(controlType: LoginType, id?: string): Promise&lt;QrCodeInfo[]&gt;

Logs in. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name     | Type                                                        | Mandatory| Description      |
| ----------- | ------------------------------------------------------------ | ---- | ---------- |
| controlType | [LoginType](arkts-apis-avMusicTemplate-t.md#logintype) | Yes  | Login type.|
| id          | string                                                       | No  | QR code ID.|

**Return value**

| Type                                                        | Description                               |
| ------------------------------------------------------------ | ----------------------------------- |
| Promise<[QrCodeInfo](arkts-apis-avMusicTemplate-i.md#qrcodeinfo)[]> | Promise used to return the array of QR code information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate a login.
   *
   * @returns Promise used to return the array of QR code information.
   */
  public async login(): Promise<avMusicTemplate.QrCodeInfo[]> {
    let qrCodeInfos: avMusicTemplate.QrCodeInfo[] = [];
    if (!this.controller) {
      console.error(TAG, 'login controller is undefined');
      return qrCodeInfos;
    }
    let controlType: avMusicTemplate.LoginType = 'queryLoginInfo';
    // id is optional. The value of id is QrCodeInfo.id, which is used when LoginType is set to refreshLoginInfo.
    let id: string | undefined = undefined;
    try {
      qrCodeInfos = await this.controller.login(controlType, id);
      console.info('Succeeded in logging in callback.');
    } catch (e) {
      console.error(TAG, `login callback failed, errCode: ${e?.code}`)
    }
    return qrCodeInfos;
  }
}
```

## requestDialogInfo

requestDialogInfo(actionType: DialogActionType, actionInfo?: DialogActionInfo): Promise&lt;DialogInfo&gt;

Requests dialog box information. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type                                                        | Mandatory| Description              |
| ---------- | ------------------------------------------------------------ | ---- | ------------------ |
| actionType | [DialogActionType](arkts-apis-avMusicTemplate-t.md#dialogactiontype) | Yes  | Dialog box action type.  |
| actionInfo | [DialogActionInfo](arkts-apis-avMusicTemplate-i.md#dialogactioninfo) | No  | Dialog box action information.|

**Return value**

| Type                                                        | Description                         |
| ------------------------------------------------------------ | ----------------------------- |
| Promise<[DialogInfo](arkts-apis-avMusicTemplate-i.md#dialoginfo)> | Promise used to return the dialog box information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the request for dialog box information.
   *
   * @returns Promise used to return the dialog box information.
   */
  public async requestDialogInfo(): Promise<avMusicTemplate.DialogInfo | undefined> {
    let actionType: avMusicTemplate.DialogActionType = 'open';
    // actionInfo is optional. It is used in the scenarios where DialogActionType is set to refresh or close.
    let actionInfo: avMusicTemplate.DialogActionInfo = {
      dialogId: 'dialogId',
      isChecked: true,
      clickedBtnId: 'clickedBtnId'
    };
    try {
      let dialogInfo: avMusicTemplate.DialogInfo | undefined =
        await this.controller?.requestDialogInfo(actionType, actionInfo);
      if (!dialogInfo?.dialogId || dialogInfo?.dialogId === '') {
        console.info(TAG, 'requestDialogInfo fail')
        return undefined;
      }
      console.info('Succeeded in requesting dialog info.');
      return dialogInfo;
    } catch (e) {
      console.error(TAG, `requestDialogInfo failed, errCode: ${e?.code}`)
    }
    return undefined;
  }
}
```

## handleMemberPurchase

handleMemberPurchase(info: MemberPurchaseInfo): Promise&lt;DialogInfo&gt;

Handles the membership purchase. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name| Type                                                        | Mandatory| Description            |
| ------ | ------------------------------------------------------------ | ---- | ---------------- |
| info   | [MemberPurchaseInfo](arkts-apis-avMusicTemplate-i.md#memberpurchaseinfo) | Yes  | Membership purchase information.|

**Return value**

| Type                                                        | Description                         |
| ------------------------------------------------------------ | ----------------------------- |
| Promise<[DialogInfo](arkts-apis-avMusicTemplate-i.md#dialoginfo)> | Promise used to return the dialog box information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the request for dialog box information.
   *
   * @returns Promise used to return the dialog box information.
   */
  public async handleMemberPurchase(): Promise<avMusicTemplate.DialogInfo | undefined> {
    let memberPurchaseInfo: avMusicTemplate.MemberPurchaseInfo = {
      id: 'id',
      diagramUrl: 'diagramUrl',
      diagramContent: 'diagramContent',
      memberPurchaseType: avMusicTemplate.MemberPurchaseType.NORMAL
    };
    try {
      let dialogInfo: avMusicTemplate.DialogInfo | undefined =
        await this.controller?.handleMemberPurchase(memberPurchaseInfo);
      if (!dialogInfo?.dialogId || dialogInfo?.dialogId === '') {
        console.info(TAG, 'handleMemberPurchase fail')
        return undefined;
      }
      console.info('Succeeded in handling member purchase.');
      return dialogInfo;
    } catch (e) {
      console.error(TAG, `handleMemberPurchase failed, errCode: ${e?.code}`)
    }
    return undefined;
  }
}
```

## queryMemberPurchase

queryMemberPurchase(memberPurchaseType: MemberPurchaseType): Promise&lt;MemberPurchaseInfo[]&gt;

Queries the membership purchase. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name            | Type                                                        | Mandatory| Description          |
| ------------------ | ------------------------------------------------------------ | ---- | -------------- |
| memberPurchaseType | [MemberPurchaseType](arkts-apis-avMusicTemplate-e.md#memberpurchasetype) | Yes  | Type of the membership purchase.|

**Return value**

| Type                                                        | Description                                 |
| ------------------------------------------------------------ | ------------------------------------- |
| Promise<[MemberPurchaseInfo](arkts-apis-avMusicTemplate-i.md#memberpurchaseinfo)[]> | Promise used to return the array of membership purchase information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the query of membership purchase.
   *
   * @returns List of membership purchase information.
   */
  public async queryMemberPurchase(): Promise<avMusicTemplate.MemberPurchaseInfo[]> {
    let memberPurchaseInfo: avMusicTemplate.MemberPurchaseInfo[] = [];
    if (!this.controller) {
      console.error(TAG, 'queryMemberPurchase controller is undefined');
      return memberPurchaseInfo;
    }
    let memberPurchaseType: avMusicTemplate.MemberPurchaseType = avMusicTemplate.MemberPurchaseType.NORMAL;
    try {
      memberPurchaseInfo = await this.controller.queryMemberPurchase(memberPurchaseType);
      console.info('Succeeded in querying member purchase.');
    } catch (e) {
      console.error(TAG, `queryMemberPurchase failed, errCode: ${e?.code}`)
    }
    return memberPurchaseInfo;
  }
}
```

## queryCustomContent

queryCustomContent(queryType: CustomType[]): Promise&lt;CustomElement&gt;

Queries the custom content. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name   | Type                                                        | Mandatory| Description            |
| --------- | ------------------------------------------------------------ | ---- | ---------------- |
| queryType | [CustomType](arkts-apis-avMusicTemplate-t.md#customtype)[] | Yes  | Array of custom types.|

**Return value**

| Type                                                        | Description                               |
| ------------------------------------------------------------ | ----------------------------------- |
| Promise<[CustomElement](arkts-apis-avMusicTemplate-i.md#customelement)> | Promise used to return the queried custom elements.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the query of custom content.
   *
   * @returns Custom element.
   */
  public async queryCustomContent(): Promise<avMusicTemplate.CustomElement | undefined> {
    let queryType: avMusicTemplate.CustomType[] = ['USER_INFO', 'TAB', 'COMPILATION', 'SETTINGS'];
    try {
      let customElement: avMusicTemplate.CustomElement | undefined =
        await this.controller?.queryCustomContent(queryType);
      if (customElement?.errorCode != 0) {
        console.warn(TAG, 'queryCustomContent fail')
        return undefined;
      }
      console.info('Succeeded in querying custom content.');
      return customElement;
    } catch (e) {
      console.error(TAG, `queryCustomContent failed, errCode: ${e?.code}`)
      return undefined;
    }
  }
}
```

## downloadMediaEntity

downloadMediaEntity(controlType: DownloadControlType, mediaEntity: MediaEntity): Promise&lt;OperResult&gt;

Downloads a media entity. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name     | Type                                                        | Mandatory| Description            |
| ----------- | ------------------------------------------------------------ | ---- | ---------------- |
| controlType | [DownloadControlType](arkts-apis-avMusicTemplate-t.md#downloadcontroltype) | Yes  | Download control type.|
| mediaEntity | [MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity) | Yes  | Media entity.      |

**Return value**

| Type                                                        | Description                                     |
| ------------------------------------------------------------ | ----------------------------------------- |
| Promise<[OperResult](arkts-apis-avMusicTemplate-i.md#operresult)> | Promise used to return the result of downloading the media entity.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the download of a media entity.
   *
   * @returns Promise used to return the operation result.
   */
  public async downloadMediaEntity(): Promise<boolean> {
    let controlType: avMusicTemplate.DownloadControlType = 'startDownload';
    let mediaEntity: avMusicTemplate.MediaEntity = {
      mediaId: 'mediaId',
      mediaType: avMusicTemplate.EntityType.SINGLE,
      parentId: 'parentId',
      parentMediaType: avMusicTemplate.EntityType.SINGLE,
      title: 'title',
      imageUrl: 'imageUrl',
      playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
    };
    try {
      let operResult: avMusicTemplate.OperResult | undefined =
        await this.controller?.downloadMediaEntity(controlType, mediaEntity);
      if (operResult?.errorCode != 0) {
        console.warn(TAG, 'start downloadMediaEntity fail')
        return false;
      }
      console.info('Succeeded in starting download media entity.');
      return true;
    } catch (e) {
      console.error(TAG, `start downloadMediaEntity failed, errCode: ${e?.code}`)
      return false;
    }
  }
}
```

## playForSearch

playForSearch(command: SearchPlayInfoType, args: SearchPlayInfo): Promise&lt;OperResult&gt;

Searches for playback. Audio and video are supported. The following uses audio as an example. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name | Type                                                        | Mandatory| Description                |
| ------- | ------------------------------------------------------------ | ---- | -------------------- |
| command | [SearchPlayInfoType](arkts-apis-avMusicTemplate-e.md#searchplayinfotype) | Yes  | Type enumeration of the search and playback information.|
| args    | [SearchPlayInfo](arkts-apis-avMusicTemplate-i.md#searchplayinfo) | Yes  | Search and playback information.          |

**Return value**

| Type                                                        | Description                       |
| ------------------------------------------------------------ | --------------------------- |
| Promise<[OperResult](arkts-apis-avMusicTemplate-i.md#operresult)> | Promise used to return the operation result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the search and playback operation.
   *
   * @returns Promise used to return the operation result.
   */
  public async playForSearch(): Promise<boolean> {
    let command: avMusicTemplate.SearchPlayInfoType = avMusicTemplate.SearchPlayInfoType.PLAY_MUSIC;
    let searchPlayMusicItems: avMusicTemplate.SearchPlayMusicItem[] = [{
      entityId: 'entityId',
      entityName: 'entityName'
    }];
    let searchPlayMusicInfo: avMusicTemplate.SearchPlayMusicInfo = {
      items: searchPlayMusicItems,
      displayName: 'displayName',
      description: 'description'
    };
    let searchPlayInfo: avMusicTemplate.SearchPlayInfo = {
      musicInfo: searchPlayMusicInfo
    };
    try {
      let operResult: avMusicTemplate.OperResult | undefined =
        await this.controller?.playForSearch(command, searchPlayInfo);
      if (operResult?.errorCode != 0) {
        console.warn(TAG, 'playForSearch fail')
        return false;
      }
      console.info('Succeeded in playing for search.');
      return true;
    } catch (e) {
      console.error(TAG, `playForSearch failed, errCode: ${e?.code}`)
      return false;
    }
  }
}
```

## executeAction

executeAction(actionType: string, params: string): Promise&lt;string&gt;

Executes an action. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type  | Mandatory| Description      |
| ---------- | ------ | ---- | ---------- |
| actionType | string | Yes  | Action type.|
| params     | string | Yes  | Action information.|

**Return value**

| Type                 | Description                             |
| --------------------- | --------------------------------- |
| Promise&lt;string&gt; | Promise used to return the action execution result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the execution of an action.
   *
   * @returns Promise<string> used to return the operation result.
   */
  public async executeAction(): Promise<string> {
    let actionType: string = 'actionType';
    let params: string = 'params';
    try {
      let result: string | undefined = await this.controller?.executeAction(actionType, params);
      if (!result || result === '') {
        console.warn(TAG, 'executeAction fail')
        return '';
      }
      console.info('Succeeded in executing action.');
      return result;
    } catch (e) {
      console.error(TAG, `executeAction failed, errCode: ${e?.code}`)
      return '';
    }
  }
}
```

## playMediaEntity

playMediaEntity(mediaEntity: MediaEntity): Promise&lt;void&gt;

Plays a media entry. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name     | Type                                                        | Mandatory| Description      |
| ----------- | ------------------------------------------------------------ | ---- | ---------- |
| mediaEntity | [MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity) | Yes  | Media entity object that contains metadata such as the title and author.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate media playback.
   */
  public async playMediaEntity() {
    let mediaEntity: avMusicTemplate.MediaEntity = {
      mediaId: 'mediaId',
      mediaType: avMusicTemplate.EntityType.SINGLE,
      parentId: 'parentId',
      parentMediaType: avMusicTemplate.EntityType.SINGLE,
      title: 'title',
      imageUrl: 'imageUrl',
      playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
    };
    this.controller?.playMediaEntity(mediaEntity);
  }
}
```

## favoriteMediaEntity

favoriteMediaEntity(actionType: MediaFavoriteType, mediaEntity: MediaEntity): Promise&lt;OperResult&gt;

Favorites a media entity. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name     | Type                                                        | Mandatory| Description            |
| ----------- | ------------------------------------------------------------ | ---- | ---------------- |
| actionType  | [MediaFavoriteType](arkts-apis-avMusicTemplate-t.md#mediafavoritetype) | Yes  | Type of the media to be added to favorites.|
| mediaEntity | [MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity) | Yes  | Media entity.      |

**Return value**

| Type                                                        | Description                                 |
| ------------------------------------------------------------ | ------------------------------------- |
| Promise<[OperResult](arkts-apis-avMusicTemplate-i.md#operresult)> | Promise used to return the result of adding a media entity to favorites.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000003 | Template listener not registered.         |
| 35000005 | AVMusicTemplate does not exist.           |
| 35000006 | AVMusicTemplateController does not exist. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Simulate the operation of adding a media entity to favorites.
   *
   * @returns Promise used to return the operation result.
   */
  public async favoriteMediaEntity(): Promise<boolean> {
    let actionType: avMusicTemplate.MediaFavoriteType = 'addFavorite';
    let mediaEntity: avMusicTemplate.MediaEntity = {
      mediaId: 'mediaId',
      mediaType: avMusicTemplate.EntityType.SINGLE,
      parentId: 'parentId',
      parentMediaType: avMusicTemplate.EntityType.SINGLE,
      title: 'title',
      imageUrl: 'imageUrl',
      playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
    };
    try {
      let operResult: avMusicTemplate.OperResult | undefined =
        await this.controller?.favoriteMediaEntity(actionType, mediaEntity);
      if (operResult?.errorCode != 0) {
        console.warn(TAG, 'favoriteMediaEntity fail')
        return false;
      }
      console.info('Succeeded in favoriting media entity.');
      return true;
    } catch (e) {
      console.error(TAG, `favoriteMediaEntity failed, errCode: ${e?.code}`)
      return false;
    }
  }
}
```

## onUserInfoChange

onUserInfoChange(callback: Callback&lt;UserInfo&gt;): void

Registers a callback for user information changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description           |
| -------- | ------------------------------------------------------------ | ---- |---------------|
| callback | Callback<[UserInfo](arkts-apis-avMusicTemplate-i.md#userinfo)> | Yes  | Callback used to return the user information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private userInfoChangeCallback: Callback<avMusicTemplate.UserInfo> = (userInfo: avMusicTemplate.UserInfo) => {
    console.info(TAG, 'userInfoChangeCallback');
  };

  public registerListener() {
    // Register the listener for user information changes.
    this.controller?.onUserInfoChange(this.userInfoChangeCallback);
  }
}
```

## offUserInfoChange

offUserInfoChange(callback?: Callback&lt;UserInfo&gt;): void

Unregisters the callback for user information changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                              |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| callback | Callback<[UserInfo](arkts-apis-avMusicTemplate-i.md#userinfo)> | No  | Callback used to return the user information. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    // Unregister the listener for user information changes.
    this.controller?.offUserInfoChange();
  }
}
```

## onDialogCommandChange

onDialogCommandChange(callback: ReportDialogCommandEvent): void

Registers a callback for dialog box command changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                          |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| callback | [ReportDialogCommandEvent](arkts-apis-avMusicTemplate-t.md#reportdialogcommandevent) | Yes  | Callback used to report dialog box command events.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private reportDialogCommandEvent: avMusicTemplate.ReportDialogCommandEvent =
    (type: avMusicTemplate.DialogControlType, buttonInfo: avMusicTemplate.DialogInfo) => {
      console.info(TAG, 'reportDialogCommandEvent');
    };

  public registerListener() {
    // Register a listener for dialog box command changes.
    this.controller?.onDialogCommandChange(this.reportDialogCommandEvent);
  }
}
```

## offDialogCommandChange

offDialogCommandChange(callback?: ReportDialogCommandEvent): void

Unregisters the callback for dialog box command changes.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                      |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| callback | [ReportDialogCommandEvent](arkts-apis-avMusicTemplate-t.md#reportdialogcommandevent) | No  | Callback used to report dialog box command events. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    // Unregister the listener for dialog box command changes.
    this.controller?.offDialogCommandChange();
  }
}
```

## onCurrentSingleChange

onCurrentSingleChange(callback: Callback&lt;Single&gt;): void

Registers a callback for the current single track changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                    |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------- |
| callback | Callback<[Single](arkts-apis-avMusicTemplate-i.md#single)> | Yes  | Callback used to return the current single track information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private currentSingleChangeCallback: Callback<avMusicTemplate.Single> = (single: avMusicTemplate.Single) => {
    console.info(TAG, 'onCurrentSingleChange');
  };

  public registerListener() {
    // Register a listener for the current single track changes.
    this.controller?.onCurrentSingleChange(this.currentSingleChangeCallback);
  }
}
```

## offCurrentSingleChange

offCurrentSingleChange(callback?: Callback&lt;Single&gt;): void

Unregisters the callback for the current single track changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                    |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------- |
| callback | Callback<[Single](arkts-apis-avMusicTemplate-i.md#single)> | No  | Callback used to return the current single track information. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    // Unregister the listener for the current single track changes.
    this.controller?.offCurrentSingleChange();
  }
}
```

## onMediaEntitiesChange

onMediaEntitiesChange(callback: Callback&lt;MediaEntity[]&gt;): void

Registers a callback for media entity changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                  |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| callback | Callback<[MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity)[]> | Yes  | Callback used to return the array of media entities.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private mediaEntitiesChangeCallback: Callback<avMusicTemplate.MediaEntity[]> =
    (single: avMusicTemplate.MediaEntity[]) => {
      console.info(TAG, 'mediaEntitiesChangeCallback');
    }

  public registerListener() {
    // Register a listener for media entity changes.
    this.controller?.onMediaEntitiesChange(this.mediaEntitiesChangeCallback);
  }
}
```

## offMediaEntitiesChange

offMediaEntitiesChange(callback?: Callback&lt;MediaEntity[]&gt;): void

Unregisters the callback for media entity changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                  |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| callback | Callback<[MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity)[]> | No  | Callback used to return the array of media entities. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    // Unregister the listener for media entity changes.
    this.controller?.offMediaEntitiesChange();
  }
}
```

## onTabContentChange

onTabContentChange(callback: ReportTabContentEvent): void

Registers a callback for tab content changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description              |
| -------- | ------------------------------------------------------------ | ---- | ------------------ |
| callback | [ReportTabContentEvent](arkts-apis-avMusicTemplate-t.md#reporttabcontentevent) | Yes  | Callback used to report the tab content event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private reportTabContentEvent: avMusicTemplate.ReportTabContentEvent =
    (tabId: string, tabContent: avMusicTemplate.MediaTabContent) => {
      console.info(TAG, 'reportTabContentEvent');
    };

  public registerListener() {
    // Register a listener for tab content changes.
    this.controller?.onTabContentChange(this.reportTabContentEvent);
  }
}
```

## offTabContentChange

offTabContentChange(callback?: ReportTabContentEvent): void

Unregisters the callback for tab content changes.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [ReportTabContentEvent](arkts-apis-avMusicTemplate-t.md#reporttabcontentevent) | No  | Callback used to report the tab content event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    // Unregisters the listener for tab content changes.
    this.controller?.offTabContentChange();
  }
}
```

## onPlaylistChange

onPlaylistChange(callback: Callback&lt;PageMediaEntity&gt;): void

Registers a callback for reporting playlist changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                        |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------------- |
| callback | Callback<[PageMediaEntity](arkts-apis-avMusicTemplate-i.md#pagemediaentity)> | Yes  | Callback used to return the tab media entity information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private playlistChangeCallback: Callback<avMusicTemplate.PageMediaEntity> =
    (pageMediaEntity: avMusicTemplate.PageMediaEntity) => {
      console.info(TAG, 'playlistChangeCallback');
    }

  public registerListener() {
    // Register a listener for playlist changes.
    this.controller?.onPlaylistChange(this.playlistChangeCallback);
  }
}
```

## offPlaylistChange

offPlaylistChange(callback?: Callback&lt;PageMediaEntity&gt;): void

Unregisters the callback for reporting playlist changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                        |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------------- |
| callback | Callback<[PageMediaEntity](arkts-apis-avMusicTemplate-i.md#pagemediaentity)> | No  | Callback used to return the tab media entity information. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    // Unregister the listener for playlist changes.
    this.controller?.offPlaylistChange();
  }
}
```

## onDownloadMediaEntityStatusChange

onDownloadMediaEntityStatusChange(callback: Callback&lt;MediaEntity&gt;): void

Registers a callback for reporting media download status changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                  |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| callback | Callback<[MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity)> | Yes  | Callback used to return the media entity information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private downloadStatusChangeCallback: Callback<avMusicTemplate.MediaEntity> =
    (mediaEntity: avMusicTemplate.MediaEntity) => {
      console.info(TAG, 'downloadStatusChangeCallback');
    };

  public registerListener() {
    // Register the listener for media download status changes.
    this.controller?.onDownloadMediaEntityStatusChange(this.downloadStatusChangeCallback);
  }
}
```

## offDownloadMediaEntityStatusChange

offDownloadMediaEntityStatusChange(callback?: Callback&lt;MediaEntity&gt;): void

Unregisters the callback for reporting media download status changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                  |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| callback | Callback<[MediaEntity](arkts-apis-avMusicTemplate-i.md#mediaentity)> | No  | Callback used to return the media entity information. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    // Unregister the listener for media download status changes.
    this.controller?.offDownloadMediaEntityStatusChange();
  }
}
```

## onCustomElementsChange

onCustomElementsChange(callback: ReportCustomElementsChangeEvent): void

Registers a callback for reporting custom element changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                  |
| -------- | ------------------------------------------------------------ | ---- | ---------------------- |
| callback | [ReportCustomElementsChangeEvent](arkts-apis-avMusicTemplate-t.md#reportcustomelementschangeevent) | Yes  | Callback used to report the custom element change event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private reportCustomElementsChangeEvent: avMusicTemplate.ReportCustomElementsChangeEvent =
    (actionType: avMusicTemplate.ActionType, customType: avMusicTemplate.CustomType,
      customElement: avMusicTemplate.CustomElement) => {
      console.info(TAG, 'reportCustomElementsChangeEvent');
    };

  public registerListener() {
    // Register a listener for custom element changes.
    this.controller?.onCustomElementsChange(this.reportCustomElementsChangeEvent);
  }
}
```

## offCustomElementsChange

offCustomElementsChange(callback?: ReportCustomElementsChangeEvent): void

Unregisters the callback for reporting custom element changes.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                    |
| -------- | ------------------------------------------------------------ | ---- | ------------------------ |
| callback | [ReportCustomElementsChangeEvent](arkts-apis-avMusicTemplate-t.md#reportcustomelementschangeevent) | No  | Callback used to report the custom element change event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    // Unregister the listener for custom element changes.
    this.controller?.offCustomElementsChange();
  }
}
```

## onSettingsChange

onSettingsChange(callback: Callback&lt;SettingItem[]&gt;): void

Registers a callback for reporting setting changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------ |
| callback | Callback<[SettingItem](arkts-apis-avMusicTemplate-i.md#settingitem)[]> | Yes  | Callback used to return the array of setting items.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private settingsChangeCallback: Callback<avMusicTemplate.SettingItem[]> =
    (settingItems: avMusicTemplate.SettingItem[]) => {
      console.info(TAG, 'settingsChangeCallback');
    };

  public registerListener() {
    // Register a listener for setting changes.
    this.controller?.onSettingsChange(this.settingsChangeCallback);
  }
}
```

## offSettingsChange

offSettingsChange(callback?: Callback&lt;SettingItem[]&gt;): void

Unregisters the callback for reporting setting changes. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------ |
| callback | Callback<[SettingItem](arkts-apis-avMusicTemplate-i.md#settingitem)[]> | No  | Callback used to receive and process the array of setting items. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    // Unregister the listener for setting changes.
    this.controller?.offSettingsChange();
  }
}
```

## onReportExecuteAction

onReportExecuteAction(callback: ReportExecuteActionEvent): void

Registers a callback for reporting execution actions. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------- |
| callback | [ReportExecuteActionEvent](arkts-apis-avMusicTemplate-t.md#reportexecuteactionevent) | Yes  | Callback used to report the event of the corresponding button action.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private reportExecuteActionEvent: avMusicTemplate.ReportExecuteActionEvent =
    (actionType: string, customType: string) => {
      console.info(TAG, 'reportExecuteActionEvent');
    };

  public registerListener() {
    // Register a listener for reporting execution actions.
    this.controller?.onReportExecuteAction(this.reportExecuteActionEvent);
  }
}
```

## offReportExecuteAction

offReportExecuteAction(callback?: ReportExecuteActionEvent): void

Unregisters the callback for reporting execution actions.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [ReportExecuteActionEvent](arkts-apis-avMusicTemplate-t.md#reportexecuteactionevent) | No  | Callback used to report the execution action event. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    // Unregister the listener for reporting execution actions.
    this.controller?.offReportExecuteAction();
  }
}
```

## onExtensionAbilityChange

onExtensionAbilityChange(callback: ReportExecuteAbilityEvent): void

Registers a callback for the event triggered when the audio template controller launches the media application UI specified by the user. This API uses an asynchronous callback to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                      |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------------- |
| callback | [ReportExecuteAbilityEvent](arkts-apis-avMusicTemplate-t.md#reportexecuteabilityevent) | Yes  | Callback used to report the event where the audio template controller launches a specified third-party application UI, including the application bundle name and UI name.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';
import { WantAgent } from '@kit.AbilityKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private reportExecuteAbilityEvent: avMusicTemplate.ReportExecuteAbilityEvent = (want: WantAgent) => {
    console.info(TAG, 'reportExecuteAbilityEvent');
  };

  public registerListener() {
    // Register a listener for the event where the media center launches the specified third-party application UI.
    this.controller?.onExtensionAbilityChange(this.reportExecuteAbilityEvent);
  }
}
```

## offExtensionAbilityChange

offExtensionAbilityChange(callback?: ReportExecuteAbilityEvent): void

Unregisters the callback for the event triggered when the audio template controller launches the playback screen of a specified media application.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------- |
| callback | [ReportExecuteAbilityEvent](arkts-apis-avMusicTemplate-t.md#reportexecuteabilityevent) | No  | Callback for the event triggered when the audio template controller launches the specified media application UI. If this parameter is left empty, all callbacks of this type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 801      | capability not supported.                 |
| 35000006 | AVMusicTemplateController does not exist. |
| 35000012 | AVMusicTemplate error.                    |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

  /**
   * Unregister the listener.
   */
  public unregisterListener() {
    // Unregister the listener for the information about the media center starting the specified third-party application screen.
    this.controller?.offExtensionAbilityChange();
  }
}
```

## destroy

destroy(): Promise&lt;void&gt;

Destroys an audio template controller. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ------------------------- |
| 801      | capability not supported. |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

const TAG: string = 'ControllerManager';

export class ControllerManager {
  private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
  private currentBundleName: string | undefined = undefined;

  /**
   * Destroy the controller.
   */
  public destroyController() {
    console.info(TAG, 'destroyController')
    this.controller?.destroy();
    this.controller = undefined;
    this.currentBundleName = undefined;
  }
}
```
