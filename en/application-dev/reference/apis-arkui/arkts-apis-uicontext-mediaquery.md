# Class (MediaQuery)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu; @song-song-song-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=45ec2d938cfede23d9ca90fe41c0d1f3e7b2b01d translatedAt=2026-10-29T09:09:58.247Z pushedAt=2026-10-30T03:17:48.652Z nl=1 -->

Provides different styles for different media types.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 10.
>
> - In the following API examples, you must first use [getMediaQuery()](arkts-apis-uicontext-uicontext.md#getmediaquery) in **UIContext** to obtain a **MediaQuery** instance, and then call the APIs using the obtained instance.

## matchMediaSync

matchMediaSync(condition: string): mediaQuery.MediaQueryListener

Sets the media query criteria and returns the corresponding listening handle.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type    | Mandatory  | Description                                      |
| --------- | ------ | ---- | ---------------------------------------- |
| condition | string | Yes | Media query condition. For details, see [Syntax](../../ui/arkts-layout-development-media-query.md#syntax). |

**Return value**

| Type                                                        | Description                                        |
| ------------------------------------------------------------ | -------------------------------------------- |
| [mediaQuery.MediaQueryListener](js-apis-mediaquery.md#mediaquerylistener) | Listening handle to a media event, which is used to register or unregister the listening callback.|

**Example**

See the example for [mediaquery](js-apis-mediaquery.md#example).
