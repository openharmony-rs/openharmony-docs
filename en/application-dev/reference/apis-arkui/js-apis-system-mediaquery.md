# @system.mediaquery (Media Query)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zju_ljz-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

The **mediaquery** module provides different styles for different media types.


> **NOTE**
>
> - The APIs of this module are no longer maintained since API version 7. You are advised to use [`@ohos.mediaquery`](js-apis-mediaquery.md) instead.
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import


```ts
import mediaquery from '@system.mediaquery';
```

## MediaQuery

Defines the MediaQuery API.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### matchMedia

matchMedia(condition: string): MediaQueryList

Creates a **MediaQueryList** object based on the query condition.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type    | Mandatory  | Description      |
| --------- | ------ | ---- | -------- |
| condition | string | Yes   | Query condition.|

**Return value**

| Type          | Description                                      |
| -------------- | ---------------------------------------- |
| [MediaQueryList](./js-apis-system-mediaquery.md#mediaquerylist) | Attributes of the **MediaQueryList** object created. For details, see the descriptions below.|

**Example**

```ts
let mMediaQueryList = mediaquery.matchMedia('(max-width: 466)');    
```

## MediaQueryEvent

Defines a media query event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type   | Read-Only| Optional  | Description   |
| ------- | ------- | ---- | ---- | ----- |
| matches | boolean | No|No   | Matching result. The value **true** means that the query condition is met, and **false** means the opposite.|

## MediaQueryList

Represents media query list information.

### Properties

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type   | Read-Only| Optional  | Description               |
| ------- | ------- | ---- |---- | ----------------- |
| media   | string  | No|  Yes   | Serialized media query condition. This parameter is read-only.|
| matches | boolean | No|  Yes    | Matching result. The value **true** means that the query condition is met, and **false** means the opposite.           |
| onchange | (matches: boolean) => void | No|  Yes    | Callback invoked when the match result changes. **matches** indicates whether the media query condition is met. The value **true** means that the query condition is met, and **false** means the opposite.|


### MediaQueryList.addListener

addListener(callback: (event: MediaQueryEvent) => void): void

Adds a listener for this **MediaQueryList** object. The listener must be added before **onShow** is called, that is, it must be added in the **onInit** or **onReady** API.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                              | Mandatory  | Description            |
| -------- | -------------------------------- | ---- | -------------- |
| callback | (event: MediaQueryEvent) => void | Yes   | Callback invoked when the query condition changes.|

**Example**

```ts
import mediaquery, { MediaQueryEvent } from '@system.mediaquery';
let mMediaQueryList = mediaquery.matchMedia('(max-width: 466)');

function maxWidthMatch(e: MediaQueryEvent): void {
  if(e.matches){
    // do something
  }
}
mMediaQueryList.addListener(maxWidthMatch);
```


### MediaQueryList.removeListener

removeListener(callback: (event: MediaQueryEvent) => void): void

Removes the listener for this **MediaQueryList** object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                               | Mandatory  | Description            |
| -------- | --------------------------------- | ---- | -------------- |
| callback | (event: MediaQueryEvent) => void | Yes   | Callback invoked when the query condition changes.|

**Example**

```ts
import mediaquery, { MediaQueryEvent } from '@system.mediaquery';
let mMediaQueryList = mediaquery.matchMedia('(max-width: 466)');

function maxWidthMatch(e: MediaQueryEvent): void {
  if(e.matches){
    // do something
  }
}
mMediaQueryList.removeListener(maxWidthMatch);
```
