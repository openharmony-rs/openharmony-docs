# AIPageCommand

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=dcc0abdade92c0b802a40194e56aabc12b399ebe translatedAt=2026-08-07T04:42:33.598Z pushedAt=2026-08-07T11:04:36.136Z -->

`AIPageCommand` defines the JSON command protocol supported by [executeAIPageCommand](./arkts-apis-webview-WebviewController.md#executeaipagecommand), including the input parameter format and response format of different commands. Before calling this API, the app needs to serialize the command object into a JSON string.

> **NOTE**
>
> - `command` must be a JSON object string.
> - The `method` field value is case-sensitive. Use the values listed in [Command Overview](#command-overview).
> - If the return value is not empty, it is a JSON string. The app can parse it using `JSON.parse`.
> - Different commands have different response formats. When a command cannot be dispatched or no result is returned, the API may return an empty string.

## Command Overview

| method | Function | Input Parameter Format | Return Format | Description |
| ---- | ---- | ---- | ---- | ---- |
| [getFullDom](#getfulldom) | Obtains the complete DOM Tree | [FullDomCommand](#fulldomcommand) | [FullDomResult](#fulldomresult) | Returns a tree structure without filtering nodes by rules. Suitable for scenarios requiring a complete hierarchical structure. |
| [getLiteDom](#getlitedom) | Obtains a lightweight DOM node list | [LiteDomCommand](#litedomcommand) | [LiteDomResult](#litedomresult) | Returns a flat list and supports filtering nodes by rules. |
| [getUrlHistory](#geturlhistory) | Obtains URL history | [GetUrlHistoryCommand](#geturlhistorycommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | Obtains the URL history list, current history item position, and forward/backward status of the current Web component. |
| [goBack](#goback) | Goes backward | [GoBackCommand](#gobackcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | Returns to the previous history page. |
| [goForward](#goforward) | Goes forward | [GoForwardCommand](#goforwardcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | Goes to the next history page. |
| [navigate](#navigate) | Navigates to a specified URL | [NavigateCommand](#navigatecommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | Opens the specified URL. |
| [addPageAnnotation](#addpageannotation) | Adds page annotations | [AddPageAnnotationCommand](#addpageannotationcommand) | [PageAnnotationResult](#pageannotationresult) | Clears existing page annotations and then draws annotation boxes and numeric labels in the current viewport of the top-level page based on node identifiers. |
| [removePageAnnotation](#removepageannotation) | Clears page annotations | [RemovePageAnnotationCommand](#removepageannotationcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | Clears the annotation layer of the current page. |
| [screenCapture](#screencapture) | Obtains web page element screenshots | [ScreenCaptureCommand](#screencapturecommand) | JSON string | Returns a JSON string with image data in Base64 encoding. Supports obtaining a viewport screenshot of the current web page or a screenshot of a target element within the viewport. |
| [getZoomLevel](#getzoomlevel) | Obtains the web page scale ratio | [GetZoomLevelCommand](#getzoomlevelcommand) | [ZoomLevelResult](#zoomlevelresult) | Obtains the scale ratio of the current web page. |

For interaction commands, see [AIPageInteraction](./arkts-apis-webview-AIPageInteraction.md).

## General Command Format

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name. For supported values, see [Command Overview](#command-overview). |
| params | - | - | Object | No | Command parameter. The format of `params` varies depending on the `method`. If not passed, the specific behavior is defined by each command. |

## Common Execution Results

`getUrlHistory`, `goBack`, `goForward`, `navigate`, and `removePageAnnotation` return the [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) format. `goBack`, `goForward`, `navigate`, and `removePageAnnotation` return `{"code":10,"message":"success"}` on success; `getUrlHistory` additionally appends the `result` field on success; command-level failure returns `{"code":error code,"message":"error description"}`.

`addPageAnnotation` returns the [PageAnnotationResult](#pageannotationresult) format.

## getFullDom

Obtains the complete DOM tree structure of the current web page. This command traverses from the document root node and returns a tree node list.

### FullDomCommand

```json
{
  "method": "getFullDom",
  "params": {
    "wants": [
      "rect",
      "visible",
      "xpath"
    ]
  }
}
```

### Input Parameter Description

| Parameter | Sub-parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, which is fixed to `getFullDom`. |
| params | - | - | Object | No | Command parameter. If not passed, the default return fields are used. |
| params | wants | - | Array\<string> | No | Specifies the fields to be additionally returned in the node. Each array item represents a node information field. For field values, see [Field Value Description of params.wants in getFullDom](#field-value-description-of-paramswants-in-getfulldom). `getFullDom` requests `tag`, `text`, and all HTML attributes by default. |

> **NOTE**
>
> `getFullDom` returns the `url`, `title`, and `children_nodes` of the current web page by default. Nodes in `children_nodes` return `tag`, `text`, `attributes`, and `children_nodes` by default. Among them, `text` and `attributes` are not returned when their field values are empty.

### Field Value Description of params.wants in getFullDom

| Value | Return Field | Return Type | Description |
| ---- | ---- | ---- | ---- |
| id | id | string | Requests the return of the node identifier generated by ArkWeb. This does not indicate filtering nodes by the HTML `id` attribute. The value is encoded from the frame identifier, document scope identifier, and DOM node identifier, and is used to distinguish nodes in the returned result. It may change after page reload, frame reconstruction, or DOM reconstruction. Returned only when a node identifier can be generated. To read the HTML `id` attribute, check `attributes.id` of the returned node. |
| tag | tag | string | Node tag name. Returns the lowercase HTML tag name for element nodes, `#text` for text nodes, and `#shadowRoot` for ShadowRoot nodes. |
| text | text | string | Node text content. This field is not returned when the value is empty. |
| title | title | string | Value of the node's `title` attribute. This field is not returned when the value is empty. |
| aria-label | aria-label | string | Value of the node's `aria-label` attribute. This field is not returned when the value is empty. |
| role | role | string | Node semantic role. This field is not returned when the value is empty. |
| aria-description | aria-description | string | Value of the node's `aria-description` attribute. This field is not returned when the value is empty. |
| rect | rect | Object | Node rectangular information, including `x`, `y`, `width`, and `height`. |
| bounds | bounds | Object | Node rectangular information, including `x`, `y`, `left`, `top`, `right`, `bottom`, `width`, and `height`. |
| visible | visible | boolean | Whether the node is visible. true indicates visible, and false indicates not visible. |
| isInViewport | isInViewport | boolean | Whether the node is within the current viewport. true indicates within the current viewport, and false indicates not within the current viewport. |
| clickable | clickable | boolean | Whether the node is clickable. true indicates clickable, and false indicates not clickable. |
| touchable | touchable | boolean | Whether the node is touchable. true indicates touchable, and false indicates not touchable. The current judgment logic is the same as that of `clickable`. |
| scrollable | scrollable | boolean | Whether the node is scrollable. true indicates scrollable, and false indicates not scrollable. |
| inputable | inputable | boolean | Whether the node is inputable. true indicates inputable, and false indicates not inputable. |
| url | url | string | Node associated URL. Read in the order of `href`, `src`, `action`, `data`, and `poster` and converted to a full URL. This field is not returned when the value is empty. |
| xpath | xpath | string | Node XPath. This field is not returned when the value is empty. |
| hover | hover | string | Value of the node's `cursor` style. This field is not returned when the value is empty. |
| mouseover | mouseover | boolean | Whether the node declares a `mouseover` inline event. true indicates declared, and false indicates not declared. |
| mouseenter | mouseenter | boolean | Whether the node declares a `mouseenter` inline event. true indicates declared, and false indicates not declared. |
| value | value | string | When the node is a `select` element, returns the currently selected value. |
| options | options | Array\<Object> | When the node is a `select` element, returns the option list. |
| value_text | value_text | Array\<Object> | When the node is a `select` element, returns the option list. |
| focusable | focusable | boolean | Whether the node can obtain focus. true indicates focusable, and false indicates not focusable. |
| editable | editable | boolean | Whether the node is editable. true indicates editable, and false indicates not editable. |
| settable | settable | boolean | Whether the node is settable. true indicates settable, and false indicates not settable. |
| checked | checked | boolean | Whether the node is in the checked state. true indicates checked, and false indicates not checked. |
| expanded | expanded | boolean | Whether the node is in the expanded state. true indicates expanded, and false indicates not expanded. |
| pressed | pressed | boolean | Whether the node is in the pressed state. true indicates pressed, and false indicates not pressed. |
| selected | selected | boolean | Whether the node is in the selected state. true indicates selected, and false indicates not selected. |
| required | required | boolean | Whether the node is required. true indicates required, and false indicates not required. |
| autocomplete | autocomplete | string | Node autocomplete information. Reads the `aria-autocomplete` attribute first, then the `autocomplete` attribute. This field is not returned when the value is empty. |
| keyshortcuts | keyshortcuts | string | Value of the node's `aria-keyshortcuts` attribute. This field is not returned when the value is empty. |

### FullDomResult

| Field | Subfield | Field Item | Type | Description |
| ---- | ---- | ---- | ---- | ---- |
| url | - | - | string | Current Page URL. |
| title | - | - | string | Current Page Title. |
| children_nodes | - | - | Array\<Object> | List of root nodes in the DOM Tree. |
| children_nodes | - | id | string | Node identifier generated by ArkWeb, not the HTML `id` attribute. Returned only when `wants` includes `id` and the node identifier can be generated. |
| children_nodes | - | tag | string | Node Tag Name. |
| children_nodes | - | text | string | Node Text content. |
| children_nodes | - | title | string | Value of the node's `title` attribute. |
| children_nodes | - | aria-label | string | Value of the node's `aria-label` attribute. |
| children_nodes | - | role | string | Node Semantic Role. |
| children_nodes | - | aria-description | string | Value of the node's `aria-description` attribute. |
| children_nodes | - | rect | Object | Node Rectangular Information. |
| children_nodes | rect | x | number | X-coordinate of the top-left corner of the node rectangle. Unit: px. |
| children_nodes | rect | y | number | Y-coordinate of the top-left corner of the node rectangle, relative to the top-left corner of the viewport of the frame to which the current node belongs. Unit: px. |
| children_nodes | rect | width | number | Width of the node rectangle. Unit: px. |
| children_nodes | rect | height | number | Height of the node rectangle. Unit: px. |
| children_nodes | - | bounds | Object | Node Rectangular Information. |
| children_nodes | bounds | x | number | X-coordinate of the top-left corner of the node rectangle. Unit: px. |
| children_nodes | bounds | y | number | Y-coordinate of the top-left corner of the node rectangle. Unit: px. |
| children_nodes | bounds | left | number | Left boundary of the node rectangle. Unit: px. |
| children_nodes | bounds | top | number | Top boundary of the node rectangle. Unit: px. |
| children_nodes | bounds | right | number | Right boundary of the node rectangle. Unit: px. |
| children_nodes | bounds | bottom | number | Bottom boundary of the node rectangle. Unit: px. |
| children_nodes | bounds | width | number | Width of the node rectangle. Unit: px. |
| children_nodes | bounds | height | number | Height of the node rectangle. Unit: px. |
| children_nodes | - | visible | boolean | Whether the node is visible. true indicates visible, false indicates not visible. |
| children_nodes | - | isInViewport | boolean | Whether the node is within the current viewport. true indicates within the current viewport, false indicates not within the current viewport. |
| children_nodes | - | clickable | boolean | Whether the node is clickable. true indicates clickable, false indicates not clickable. |
| children_nodes | - | touchable | boolean | Whether the node is touchable. true indicates touchable, false indicates not touchable. |
| children_nodes | - | scrollable | boolean | Whether the node is scrollable. true indicates scrollable, false indicates not scrollable. |
| children_nodes | - | inputable | boolean | Whether the node accepts input. true indicates input is accepted, false indicates input is not accepted. |
| children_nodes | - | url | string | Node Associated URL. |
| children_nodes | - | xpath | string | Node XPath. |
| children_nodes | - | hover | string | Value of the node's `cursor` style. |
| children_nodes | - | mouseover | boolean | Whether the node declares an inline `mouseover` event. true indicates declared, false indicates not declared. |
| children_nodes | - | mouseenter | boolean | Whether the node declares an inline `mouseenter` event. true indicates declared, false indicates not declared. |
| children_nodes | - | value | string | Currently selected value of the `select` element. |
| children_nodes | - | options | Array\<Object> | List of options for the `select` element. |
| children_nodes | - | value_text | Array\<Object> | List of options for the `select` element. |
| children_nodes | options/value_text | value | string | Option value of the `select` element. |
| children_nodes | options/value_text | text | string | Option text of the `select` element. |
| children_nodes | - | focusable | boolean | Whether the node can receive focus. true indicates focusable, false indicates not focusable. |
| children_nodes | - | editable | boolean | Whether the node is editable. true indicates editable, false indicates not editable. |
| children_nodes | - | settable | boolean | Whether the node value can be set. true indicates settable, false indicates not settable. |
| children_nodes | - | checked | boolean | Whether the node is in the checked state. true indicates checked, false indicates not checked. |
| children_nodes | - | expanded | boolean | Whether the node is in the expanded state. true indicates expanded, false indicates not expanded. |
| children_nodes | - | pressed | boolean | Whether the node is in the pressed state. true indicates pressed, false indicates not pressed. |
| children_nodes | - | selected | boolean | Whether the node is in the selected state. true indicates selected, false indicates not selected. |
| children_nodes | - | required | boolean | Whether the node is a required field. true indicates required, false indicates not required. |
| children_nodes | - | autocomplete | string | Node Autocomplete Information. |
| children_nodes | - | keyshortcuts | string | Value of the node's `aria-keyshortcuts` attribute. |
| children_nodes | - | attributes | Object | Collection of HTML attributes. |
| children_nodes | attributes | &lt;attributeName&gt; | string | HTML attribute name and its corresponding attribute value. |
| children_nodes | - | children_nodes | Array\<Object> | List of child nodes of the current node. |

> **NOTE**
>
> - The node fields in `children_nodes` are determined by both the default fields and `wants`. When a field value is empty, some string fields and the `attributes` field are not returned.
> - `getFullDom` skips the subtrees of `script`, `noscript`, `style`, `template`, and `slot` elements.
> - `getFullDom` traverses open or closed author Shadow DOM, and does not return user-agent Shadow DOM.
> - For parseable child frames, the root node of the child frame is merged into the `children_nodes` of the corresponding frame owner node.

### Request Example

```json
{
  "method": "getFullDom",
  "params": {
    "wants": [
      "rect",
      "visible",
      "xpath"
    ]
  }
}
```

### Response Example

```json
{
  "url": "https://www.example.com/",
  "title": "Example",
  "children_nodes": [
    {
      "tag": "html",
      "attributes": {
        "lang": "en"
      },
      "rect": {
        "x": 0,
        "y": 0,
        "width": 360,
        "height": 640
      },
      "visible": true,
      "xpath": "/html[1]",
      "children_nodes": [
        {
          "tag": "body",
          "children_nodes": [
            {
              "tag": "button",
              "attributes": {
                "id": "submit"
              },
              "rect": {
                "x": 24,
                "y": 36,
                "width": 96,
                "height": 40
              },
              "visible": true,
              "xpath": "/html[1]/body[1]/button[1]",
              "children_nodes": [
                {
                  "tag": "#text",
                  "text": "Submit",
                  "children_nodes": []
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

## getLiteDom

Obtains the lightweight DOM node list of the current web page. This command first filters nodes based on `rules`, and then returns the specified fields based on `wants`.

### LiteDomCommand

```json
{
  "method": "getLiteDom",
  "params": {
    "rules": {
      "tags": ["button", "a"],
      "isInViewport": true
    },
    "wants": [
      "id",
      "tag",
      "rect",
      "clickable",
      "xpath",
      {
        "attributes": ["id", "class", "href"]
      }
    ]
  }
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed as `getLiteDom`. |
| params | - | - | Object | No | Command parameter. If not passed, nodes are not filtered by rules and default return fields are used. |
| params | rules | - | Object | No | Node filtering rule. If not passed, all element nodes that are not skipped are returned. |
| params | rules | tags | Array\<string> | No | Filters nodes by HTML tag name. Used when specific types of HTML elements need to be filtered (for example, obtaining only buttons or links). If this condition is not passed, nodes are not filtered by tag. |
| params | rules | attributes | Array\<string> \| Object | No | Filters nodes by HTML attribute. When an Array is passed, determines whether the node contains the specified attribute. When an Object is passed, the key indicates the attribute name, and a non-empty string value indicates that the attribute value must contain the string. |
| params | rules | roles | Array\<string> | No | Filters nodes by node semantic role. |
| params | rules | clickable | boolean | No | Filters nodes by whether they are clickable. true filters clickable nodes, and false filters non-clickable nodes. |
| params | rules | scrollable | boolean | No | Filters nodes by whether they are scrollable. true filters scrollable nodes, and false filters non-scrollable nodes. |
| params | rules | isInViewport | boolean | No | Filters nodes by whether they are in the current viewport. true filters nodes in the current viewport, and false filters nodes not in the current viewport. |
| params | wants | - | Array\<string \| Object> | No | Specifies the fields to be additionally returned in the node. `getLiteDom` requests `tag`, `text`, and `xpath` by default. |
| params | wants | - | string | No | When the array item is a string, indicates the node information field to be additionally returned. For field values, see [Field Value Description of params.wants in getLiteDom](#field-value-description-of-paramswants-in-getlitedom). |
| params | wants | attributes | Array\<string> | No | When the array item is an Object and contains `attributes`, specifies the HTML attributes to be returned. |

> **NOTE**
>
> - `getLiteDom` returns the `url`, `title`, and `nodes` of the current web page by default. Nodes in `nodes` return `tag`, `text`, and `xpath` by default. `text` is not returned when the field value is empty.
> - `isInViewport` takes effect in combination with other filtering rules.
> - A node matches if it meets any one of the `tags`, `attributes`, `roles`, `clickable`, or `scrollable` rules.
> - If `tags`, `attributes`, `roles`, `clickable`, and `scrollable` are not set, all element nodes that are not skipped meet the filtering conditions.

### Field Value Description of params.wants in getLiteDom

| Value | Return Field | Return Type | Description |
| ---- | ---- | ---- | ---- |
| id | id | string | Requests the return of the node identifier generated by ArkWeb. This does not indicate filtering nodes by the HTML `id` attribute. The value is encoded from a combination of the frame identifier, document scope identifier, and DOM node identifier, and is used to distinguish nodes in the returned result. It may change after page reload, frame reconstruction, or DOM reconstruction. Returned only when a node identifier can be generated. To read the HTML `id` attribute, request the `id` attribute through an `attributes` object item in `wants` and check `attributes.id` of the returned node. |
| tag | tag | string | Node tag name. Returns the lowercase HTML tag name. |
| text | text | string | Node text content. `getLiteDom` returns only element nodes. This field is not returned when the text of the current element node is empty. |
| title | title | string | Value of the node's `title` attribute. This field is not returned when its value is empty. |
| aria-label | aria-label | string | Value of the node's `aria-label` attribute. This field is not returned when its value is empty. |
| role | role | string | Node semantic role. This field is not returned when its value is empty. |
| aria-description | aria-description | string | Value of the node's `aria-description` attribute. This field is not returned when its value is empty. |
| rect | rect | Object | Node rectangular information, including `x`, `y`, `width`, and `height`. |
| bounds | bounds | Object | Node rectangular information, including `x`, `y`, `left`, `top`, `right`, `bottom`, `width`, and `height`. |
| visible | visible | boolean | Whether the node is visible. `true` indicates visible, and `false` indicates not visible. |
| isInViewport | isInViewport | boolean | Whether the node is within the current viewport. `true` indicates within the current viewport, and `false` indicates not within the current viewport. |
| clickable | clickable | boolean | Whether the node is clickable. `true` indicates clickable, and `false` indicates not clickable. |
| touchable | touchable | boolean | Whether the node is touchable. `true` indicates touchable, and `false` indicates not touchable. The current judgment logic is the same as that of `clickable`. |
| scrollable | scrollable | boolean | Whether the node is scrollable. `true` indicates scrollable, and `false` indicates not scrollable. |
| inputable | inputable | boolean | Whether the node is inputable. `true` indicates inputable, and `false` indicates not inputable. |
| url | url | string | Node associated URL. Read in the order of `href`, `src`, `action`, `data`, and `poster` and converted to a full URL. This field is not returned when its value is empty. |
| xpath | xpath | string | Node XPath. This field is not returned when its value is empty. |
| hover | hover | string | Value of the node's `cursor` style. This field is not returned when its value is empty. |
| mouseover | mouseover | boolean | Whether the node declares a `mouseover` inline event. `true` indicates declared, and `false` indicates not declared. |
| mouseenter | mouseenter | boolean | Whether the node declares a `mouseenter` inline event. `true` indicates declared, and `false` indicates not declared. |
| value | value | string | When the node is a `select` element, returns the currently selected value. |
| options | options | Array\<Object> | When the node is a `select` element, returns the option list. |
| value_text | value_text | Array\<Object> | When the node is a `select` element, returns the option list. |
| focusable | focusable | boolean | Whether the node is focusable. `true` indicates focusable, and `false` indicates not focusable. |
| editable | editable | boolean | Whether the node is editable. `true` indicates editable, and `false` indicates not editable. |
| settable | settable | boolean | Whether the node is settable. `true` indicates settable, and `false` indicates not settable. |
| checked | checked | boolean | Whether the node is in the checked state. `true` indicates in the checked state, and `false` indicates not in the checked state. |
| expanded | expanded | boolean | Whether the node is in the expanded state. `true` indicates in the expanded state, and `false` indicates not in the expanded state. |
| pressed | pressed | boolean | Whether the node is in the pressed state. `true` indicates in the pressed state, and `false` indicates not in the pressed state. |
| selected | selected | boolean | Whether the node is in the selected state. `true` indicates in the selected state, and `false` indicates not in the selected state. |
| required | required | boolean | Whether the node is required. `true` indicates required, and `false` indicates not required. |
| autocomplete | autocomplete | string | Node autocomplete information. Reads the `aria-autocomplete` attribute first, and then the `autocomplete` attribute. This field is not returned when its value is empty. |
| keyshortcuts | keyshortcuts | string | Value of the node's `aria-keyshortcuts` attribute. This field is not returned when its value is empty. |

### LiteDomResult

| Field | Sub-field | Field Item | Type | Description |
| ---- | ---- | ---- | ---- | ---- |
| url | - | - | string | Current Page URL. |
| title | - | - | string | Current Page Title. |
| nodes | - | - | Array\<Object> | Node list that matches the filter rules. |
| nodes | - | id | string | Node identifier generated by ArkWeb, not the HTML `id` attribute. Returned only when `wants` includes `id` and the node identifier can be generated. |
| nodes | - | tag | string | Node Tag Name. |
| nodes | - | text | string | Node text content. `getLiteDom` returns only element nodes. This field is not returned when the current element node text is empty. |
| nodes | - | title | string | Value of the node's `title` attribute. |
| nodes | - | aria-label | string | Value of the node's `aria-label` attribute. |
| nodes | - | role | string | Node Semantic Role. |
| nodes | - | aria-description | string | Value of the node's `aria-description` attribute. |
| nodes | - | rect | Object | Node Rectangular Information. |
| nodes | rect | x | number | X-coordinate of the upper-left corner of the node rectangle. Unit: px. |
| nodes | rect | y | number | Y-coordinate of the upper-left corner of the node rectangle, relative to the upper-left corner of the viewport of the frame to which the current node belongs. Unit: px. |
| nodes | rect | width | number | Width of the node rectangle. Unit: px. |
| nodes | rect | height | number | Height of the node rectangle. Unit: px. |
| nodes | - | bounds | Object | Node Rectangular Information. |
| nodes | bounds | x | number | X-coordinate of the upper-left corner of the node rectangle. Unit: px. |
| nodes | bounds | y | number | Y-coordinate of the upper-left corner of the node rectangle. Unit: px. |
| nodes | bounds | left | number | Left edge of the node rectangle. Unit: px. |
| nodes | bounds | top | number | Top edge of the node rectangle. Unit: px. |
| nodes | bounds | right | number | Right edge of the node rectangle. Unit: px. |
| nodes | bounds | bottom | number | Bottom edge of the node rectangle. Unit: px. |
| nodes | bounds | width | number | Width of the node rectangle. Unit: px. |
| nodes | bounds | height | number | Height of the node rectangle. Unit: px. |
| nodes | - | visible | boolean | Node Visibility. true indicates visible, and false indicates invisible. |
| nodes | - | isInViewport | boolean | Whether the node is in the current viewport. true indicates in the current viewport, and false indicates not in the current viewport. |
| nodes | - | clickable | boolean | Whether the node is clickable. true indicates clickable, and false indicates not clickable. |
| nodes | - | touchable | boolean | Whether the node is touchable. true indicates touchable, and false indicates not touchable. |
| nodes | - | scrollable | boolean | Whether the node is scrollable. true indicates scrollable, and false indicates not scrollable. |
| nodes | - | inputable | boolean | Whether the node is inputable. true indicates inputable, and false indicates not inputable. |
| nodes | - | url | string | Node Associated URL. |
| nodes | - | xpath | string | Node XPath. |
| nodes | - | hover | string | Value of the node's `cursor` style. |
| nodes | - | mouseover | boolean | Whether the node declares the `mouseover` inline event. true indicates declared, and false indicates not declared. |
| nodes | - | mouseenter | boolean | Whether the node declares the `mouseenter` inline event. true indicates declared, and false indicates not declared. |
| nodes | - | value | string | Currently selected value of the `select` element. |
| nodes | - | options | Array\<Object> | Option list of the `select` element. |
| nodes | - | value_text | Array\<Object> | Option list of the `select` element. |
| nodes | options/value_text | value | string | Option value of the `select` element. |
| nodes | options/value_text | text | string | Option text of the `select` element. |
| nodes | - | focusable | boolean | Whether the node can receive focus. true indicates focusable, and false indicates not focusable. |
| nodes | - | editable | boolean | Whether the node is editable. true indicates editable, and false indicates not editable. |
| nodes | - | settable | boolean | Whether the node is settable. true indicates settable, and false indicates not settable. |
| nodes | - | checked | boolean | Whether the node is in the checked state. true indicates checked, and false indicates not checked. |
| nodes | - | expanded | boolean | Whether the node is in the expanded state. true indicates expanded, and false indicates not expanded. |
| nodes | - | pressed | boolean | Whether the node is in the pressed state. true indicates pressed, and false indicates not pressed. |
| nodes | - | selected | boolean | Whether the node is in the selected state. true indicates selected, and false indicates not selected. |
| nodes | - | required | boolean | Whether the node is required. true indicates required, and false indicates not required. |
| nodes | - | autocomplete | string | Node Autocomplete Information. |
| nodes | - | keyshortcuts | string | Value of the node's `aria-keyshortcuts` attribute. |
| nodes | - | attributes | Object | HTML attribute set. |
| nodes | attributes | &lt;attributeName&gt; | string | HTML attribute name and its corresponding value. |

> **NOTE**
>
> - The node fields in `nodes` are determined by both the default fields and `wants`. When a field value is empty, some string fields and the `attributes` field are not returned.
> - `getLiteDom` returns only element nodes, not text nodes.
> - `getLiteDom` skips the subtrees of `script`, `noscript`, `style`, `template`, and `slot` elements.
> - `getLiteDom` traverses open or closed author Shadow DOM, and does not return user-agent Shadow DOM.
> - The result includes nodes in resolvable child frames. Nodes maintain the DOM traversal order within each frame, and child frame nodes are appended as a whole after the current frame node list. The merge order of multiple child frames is determined by the internal frame token set.

### Request Example

```json
{
  "method": "getLiteDom",
  "params": {
    "rules": {
      "tags": ["button", "a"],
      "isInViewport": true
    },
    "wants": [
      "id",
      "tag",
      "rect",
      "clickable",
      "xpath",
      {
        "attributes": ["id", "class", "href"]
      }
    ]
  }
}
```

### Response Example

```json
{
  "url": "https://www.example.com/",
  "title": "Example",
  "nodes": [
    {
      "id": "frameToken|documentToken|12",
      "tag": "button",
      "rect": {
        "x": 24,
        "y": 36,
        "width": 96,
        "height": 40
      },
      "clickable": true,
      "xpath": "/html[1]/body[1]/button[1]",
      "attributes": {
        "id": "submit",
        "class": "primary"
      }
    }
  ]
}
```

## getUrlHistory

Obtains the URL history list of the current Web component, along with the current history item position and forward/backward state.

### GetUrlHistoryCommand

```json
{
  "method": "getUrlHistory",
  "params": {}
}
```

### Input Parameter Description

| Name | Sub-parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, which is fixed to `getUrlHistory`. |
| params | - | - | Object | No | Command parameter. Currently has no sub-fields. You can pass `{}` or omit it. |

### Response Description

If the operation is successful, [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) is returned, and the following fields are carried in `result`.

| Field | Subfield | Type | Description |
| ---- | ---- | ---- | ---- |
| result | currentIndex | number | Index of the current history item in the URL history list. The value is `-1` if the current history item is not found. |
| result | canGoBack | boolean | Whether the current page can go back. |
| result | canGoForward | boolean | Whether the current page can go forward. |
| result | entries | Array\<Object> | History item list. |
| result.entries | index | number | Index of this history item in the URL history list. For the current history item, this field value is the same as `currentIndex`. |
| result.entries | url | string | URL of the history item. |
| result.entries | title | string | Title of the history item. |

The failure result is as follows:

| Error code | Trigger Condition |
| ---- | ---- |
| 132 | The browser or browser host is empty. |

### Request Example

```json
{
  "method": "getUrlHistory",
  "params": {}
}
```

### Response Example

```json
{
  "code": 10,
  "message": "success",
  "result": {
    "currentIndex": 1,
    "canGoBack": true,
    "canGoForward": false,
    "entries": [
      {
        "index": 0,
        "url": "https://www.example.com/",
        "title": "Example"
      },
      {
        "index": 1,
        "url": "https://www.example.com/form",
        "title": "Form"
      }
    ]
  }
}
```

## goBack

Goes back to the previous history page.

### GoBackCommand

```json
{
  "method": "goBack",
  "params": {}
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed as `goBack`. |
| params | - | - | Object | No | Command parameter. Currently has no sub-fields. You can pass `{}` or omit it. |

### Response Description

If the command is executed successfully, `{"code":10,"message":"success"}` is returned.

The following are failure results:

| Error codes | Trigger Condition |
| ---- | ---- |
| 11 | The current page has no history item to go back to. |
| 132 | The browser is empty. |

### Response Example

Returned when going back is possible:

```json
{
  "code": 10,
  "message": "success"
}
```

Returned when going back is not possible:

```json
{
  "code": 11,
  "message": "Cannot go back"
}
```

## goForward

Navigates forward to the next history page.

### GoForwardCommand

```json
{
  "method": "goForward",
  "params": {}
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed as `goForward`. |
| params | - | - | Object | No | Command parameter. Currently has no sub-fields. You can pass `{}` or omit it. |

### Response Description

If the command is executed successfully, `{"code":10,"message":"success"}` is returned.

The following are failure results:

| Error codes | Trigger Condition |
| ---- | ---- |
| 11 | The current page has no forward history item. |
| 132 | The browser is empty. |

### Response Example

Returned when forward navigation is possible:

```json
{
  "code": 10,
  "message": "success"
}
```

Returned when forward navigation is not possible:

```json
{
  "code": 11,
  "message": "Cannot go forward"
}
```

## navigate

Opens the specified URL.

### NavigateCommand

```json
{
  "method": "navigate",
  "params": {
    "url": "https://www.example.com/"
  }
}
```

### Input Parameter Description

| Name | Sub-parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, which is fixed to `navigate`. |
| params | - | - | Object | Yes | Command parameter. |
| params | url | - | string | Yes | Target URL. Supports `http`, `https`, `file`, and `about` protocols. |

> **NOTE**
>
> - When `params.url` is missing or is an empty string, `{"code":391,"message":"params.url is required"}` is returned.
> - When `params.url` is not a string, is not a valid URL, or uses an unsupported protocol, `{"code":392,"message":"params.url is invalid"}` is returned.
> - The `resource`, `javascript`, `data`, and `ftp` protocols are not supported.

### Response Description

When the command is executed successfully, `{"code":10,"message":"success"}` is returned.

The failure results are as follows:

| Error Code | Trigger Condition |
| ---- | ---- |
| 132 | The browser is empty. |
| 160 | The browser exists, but the main frame is empty. |
| 391 | `params` is missing or is not an Object, or `url` is missing or is an empty string. |
| 392 | `url` is passed but is not a string, or is a non-empty string but is not a valid URL or the protocol is not within the range of `http`, `https`, `file`, or `about`. |

### Request Example

```json
{
  "method": "navigate",
  "params": {
    "url": "about:blank"
  }
}
```

### Response Example

Returned on success:

```json
{
  "code": 10,
  "message": "success"
}
```

Returned when the URL is invalid:

```json
{
  "code": 392,
  "message": "params.url is invalid"
}
```

## addPageAnnotation

Clears existing page annotations, obtains element positions based on the node identifiers in `elementList`, and draws fixed-position annotation boxes and numeric labels in the current viewport of the top-level page.

> **NOTE**
>
> - Node identifiers can be obtained from the `id` field returned by [getFullDom](#getfulldom) or [getLiteDom](#getlitedom), in the format of `frameToken|documentScopeToken|domNodeId`.
> - Annotations only reflect the current viewport position at the time of invocation. After the page is scrolled, annotations are not automatically recalculated. To update positions, obtain the node identifiers again and call this command again.
> - The annotation layer uses fixed positioning, is displayed above the page content, and does not intercept page input events.

### AddPageAnnotationCommand

```json
{
  "method": "addPageAnnotation",
  "params": {
    "elementList": ["frameToken|documentScopeToken|12"],
    "style": {
      "maxMarks": 350,
      "border": {
        "color": "#dc2626",
        "width": 1
      },
      "label": {
        "fontSize": 11,
        "fontColor": "#ffffff",
        "backgroundColor": "#dc2626",
        "avoidCover": false
      }
    }
  }
}
```

### Input Parameter Description

| Parameter | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed as `addPageAnnotation`. |
| params | - | - | Object | Yes | Command parameter. Returns `{"code":110,"message":"params is invalid"}` when missing or not an Object. |
| params | - | elementList | Array\<string> | Yes | List of node identifiers to annotate, must be a non-empty string array. Returns `{"code":391,"message":"missing elementList"}` when missing; returns `{"code":392,"message":"invalid elementList"}` when not an array, empty array, array item not a string, or empty string. |
| params | - | style | Object | No | Annotation style. Uses default values when not passed or the field is invalid. |
| style | - | maxMarks | number | No | Maximum number of annotation rectangles. Default value: `350`, upper limit: `1000`. Uses the default value when the value is less than or equal to `0` or not a number; capped at `1000` when the value is greater than or equal to `1000`; positive decimals are rounded down, and treated as `1` when the rounded result is less than `1`. |
| style | border | color | string | No | Annotation border color. Supports `#RGB`, `#RRGGBB`, and `#RRGGBBAA` formats. Default value: `#dc2626`. |
| style | border | width | number | No | Annotation border width. Default value: `1`, value range: `1` to `8`. Clipped to the boundary value when out of range; uses the default value when not a number. |
| style | label | fontSize | number | No | Number label font size. Default value: `11`, value range: `8` to `32`. Clipped to the boundary value when out of range; uses the default value when not a number. |
| style | label | fontColor | string | No | Number label text color. Supports `#RGB`, `#RRGGBB`, and `#RRGGBBAA` formats. Default value: `#ffffff`. |
| style | label | backgroundColor | string | No | Number label background color. Supports `#RGB`, `#RRGGBB`, and `#RRGGBBAA` formats. Follows the annotation border color when not set; the default border color is `#dc2626`. |
| style | label | avoidCover | boolean | No | Whether the number label avoids covering the annotation border and placed labels as much as possible. Default value: `false`. |

### Execution Rules

- During annotation, one or more layout rectangles of the element in the current viewport are obtained. If the element has no layout rectangle with a positive area, the element's bounding rectangle is used instead.

- Hit testing uses the horizontal center point of the rectangle and a sampling point at `3/5` of its height. The element hit by the sampling point must be the target element or its descendant; otherwise, the rectangle is not drawn.

- Elements in embedded frames are drawn after their coordinates are converted to the top-level page viewport coordinates.

- Rectangles are clipped to the current viewport. An element is not drawn and is counted in `missingElementIds` if it is completely outside the viewport, its total visible area after clipping is less than `20px²`, it is occluded, the element cannot be found, or its coordinates cannot be converted.

- An element may correspond to multiple rectangles. Annotation boxes are drawn per rectangle, while numeric labels are drawn per element. The text indicates the actual drawing order, starting from `1`.

- `maxMarks` limits the number of rectangles, not the number of elements. After the limit is reached, `truncated` is returned as `true`. Elements that are not further processed are not guaranteed to be included in `missingElementIds`.

### PageAnnotationResult

The following JSON string is returned when the command is executed successfully:

```json
{
  "code": 10,
  "message": "success",
  "renderedCount": 1,
  "truncated": false,
  "missingElementIds": [],
  "invalidElementIds": []
}
```

| Name | Type | Description |
| ---- | ---- | ---- |
| code | number | Result code. `10` indicates that the command is executed successfully. For other values, see [Command Execution Result Code Description](./arkts-apis-webview-AIPageResult.md#command-execution-result-code-description). |
| message | string | Result description. `"success"` when the execution is successful. |
| renderedCount | number | Number of elements for which at least one valid rectangle is actually drawn. |
| truncated | boolean | Whether the result is truncated due to reaching the `maxMarks` limit. |
| missingElementIds | Array\<string> | List of node identifiers that are in correct format but failed to be drawn. |
| invalidElementIds | Array\<string> | List of node identifiers that are in invalid format. |

> **NOTE**
>
> `missingElementIds` and `invalidElementIds` are diagnostic fields. When there are undrawn elements or invalid node identifiers, the command as a whole may still return `{"code":10,"message":"success"}`.

### Common Response Examples

Some nodes are not drawn successfully:

```json
{
  "code": 10,
  "message": "success",
  "renderedCount": 2,
  "truncated": false,
  "missingElementIds": ["frameToken|documentScopeToken|404"],
  "invalidElementIds": []
}
```

Invalid node identifier format:

```json
{
  "code": 10,
  "message": "success",
  "renderedCount": 0,
  "truncated": false,
  "missingElementIds": [],
  "invalidElementIds": ["invalidNodeId"]
}
```

Parameter error:

```json
{
  "code": 392,
  "message": "invalid elementList"
}
```

Common failure results are as follows:

| Error Code | Trigger Condition |
| ---- | ---- |
| 11 | The annotation command failed to execute. |
| 110 | `params` is missing or is not an Object. |
| 130 | The annotation command execution timed out. |
| 132 | The browser, main page frame, or ArkWeb page frame is null. |
| 391 | `elementList` is missing. |
| 392 | `elementList` is not an array, is an empty array, or contains items that are not strings or are empty strings. |

## removePageAnnotation

Clears the annotation layer of the current page.

### RemovePageAnnotationCommand

```json
{
  "method": "removePageAnnotation"
}
```

### Input Parameter Description

| Name | Sub-parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, which is fixed to `removePageAnnotation`. |

### Response Description

If the command is executed successfully, the following JSON string is returned:

```json
{
  "code": 10,
  "message": "success"
}
```

Common failure results are as follows:

| Error codes | Trigger Condition |
| ---- | ---- |
| 11 | The current page does not have an annotation layer that can be cleaned, or the annotation cleanup command failed. |
| 130 | The annotation cleanup command timed out. |
| 132 | The browser, main page frame, or ArkWeb page frame is empty. |

## screenCapture

Obtains a screenshot of the current web page viewport, a target element within the viewport, or a target area within the viewport, and returns the image data in Base64 encoding.

### ScreenCaptureCommand

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed as `screenCapture`. |
| params | - | - | Object | No | Command parameter. When not passed or empty, obtains the current web page viewport screenshot. |
| params | nodeid | - | string | No | Node identifier of the target element, which can be obtained from the `id` field returned by [getFullDom](#getfulldom) or [getLiteDom](#getlitedom). |
| params | xpath | - | string | No | XPath of the target element, which can be obtained from the `xpath` field returned by [getFullDom](#getfulldom) or [getLiteDom](#getlitedom). |
| params | clip | - | Object | No | Target screenshot area information based on the current web page viewport, including `x`, `y`, `width`, `height`, and `scale`. |
| params | clip | x | number | Yes | X-coordinate of the upper-left corner of the target screenshot area rectangle.<br>Unit: vp. The input parameter must be greater than or equal to 0. When the input parameter is greater than the width of the current web page viewport, blank pixel image data is returned. |
| params | clip | y | number | Yes | Y-coordinate of the upper-left corner of the target screenshot area rectangle.<br>Unit: vp. The input parameter must be greater than or equal to 0. When the input parameter is greater than the height of the current web page viewport, blank pixel image data is returned. |
| params | clip | width | number | Yes | Width of the target screenshot area rectangle.<br>Unit: vp. The input parameter must be greater than 0. When the input parameter is greater than the width of the current web page viewport, the screenshot continues from the beginning based on the excess width and stitches the images. If the x parameter is set to a value greater than 0, the pixels in the first x width range of the stitched image are blank. |
| params | clip | height | number | Yes | Height of the target screenshot area rectangle.<br>Unit: vp. The input parameter must be greater than 0. When the input parameter is greater than the height of the current web page viewport, the screenshot continues from the beginning based on the excess height and stitches the images. If the y parameter is set to a value greater than 0, the pixels in the first y height range of the stitched image are blank. |
| params | clip | scale | number | Yes | Specifies the scale ratio of the screenshot result. The input parameter must be greater than 0. When the input parameter is 1, the scale ratio is the default for loading the web page. When the input parameter is less than 1, the screenshot is scaled down. When the input parameter is greater than 1, the screenshot is scaled up. |

> **NOTE**
>
> - `nodeid`, `xpath`, and `clip` cannot take effect simultaneously. When two or more are set, the priority is `nodeid` > `xpath` > `clip`. When none of the three is set, the current web page viewport screenshot is obtained by default.
> - Screenshots of iframe elements are supported, but cross-origin screenshots of elements inside iframes are not supported. Screenshots of same-layer rendered ArkUI components are not supported.

### Response Description

| Name | Type | Description |
| ---- | ---- | ---- |
| code | number | Execution result code. For details, see [Command Execution Result Code Description](./arkts-apis-webview-AIPageResult.md#command-execution-result-code-description). |
| message | string | Execution result description. `"success"` if successful; error description if failed. |
| data | string | Base64-encoded string in PNG format. Returned when successful. |

When the command is executed successfully, `{"code":10,"message":"success","data":"Base64-encoded string in PNG format"}` is returned; when failed, an error code JSON is returned. Common error codes are listed in the table below:

| Error Code | Trigger Condition |
| ---- | ---- |
| 11  | Failed to obtain or encode the screenshot data. |
| 131 | The target element is not within the current web page viewport. |
| 132 | browser or host is empty, which usually indicates that the Web instance is unavailable. |
| 160 | The page is not ready. |
| 350 | Failed to deliver the screenshot capture command. |
| 351 | Failed to initialize the screenshot capture channel. |
| 352 | Failed to execute screenshot capture (including XPath failed to locate the target element, or the target element is not within the current web page). |
| 353 | Failed to parse the screenshot capture response. |
| 392 | The `nodeid` format is incorrect, `frameToken` or `documentToken` does not match, the DOM node does not exist in the current web page, or any of the five parameters in `clip` has an incorrect format or is not set. |

### Request Example

Obtain a screenshot of the target element by node identifier:

```json
{
  "method": "screenCapture",
  "params": {
    "nodeid": "frameToken|documentToken|12"
  }
}
```

Obtain a screenshot of the target element by XPath:

```json
{
  "method": "screenCapture",
  "params": {
    "xpath": "/html/body/div/p[2]/a"
  }
}
```

Obtain a screenshot of the target area by clip:

```json
{
  "method": "screenCapture",
  "params": {
    "clip": {
      "x": 0,
      "y": 0,
      "width": 200,
      "height": 200,
      "scale": 1
    }
  }
}
```

> **NOTE**
>
> - Developers need to replace `nodeid` or `xpath` with actual values. These can be obtained from the `id` field or `xpath` field returned by [getFullDom](#getfulldom) or [getLiteDom](#getlitedom).

### Response Example

On success:

```json
{
  "code": 10,
  "message": "success",
  "data": "Base64-encoded string in PNG format"
}
```

On failure:

`131` (the target element is not in the viewport of the current web page):

```json
{
  "code": 131,
  "message": "element not in viewport"
}
```

`392`: invalid `nodeid` format.

```json
{
  "code": 392,
  "message": "invalid param: nodeid"
}
```

### Sample Code

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

interface ClipParams {
  x: number;
  y: number;
  width: number;
  height: number;
  scale: number;
}

interface CaptureParams {
  xpath?: string;
  nodeid?: string;
  clip?: ClipParams;
}

interface PageCommand {
  method: string;
  params?: CaptureParams;
}

interface AiCommandResponse {
  code: number;
  message?: string;
  data?: string;
}

@Entry
@Component
struct Index {
  private controller: webview.WebviewController = new webview.WebviewController();
  @State imgData: string = '';
  @State statusMsg: string = '';

  async capture() {
    this.imgData = '';
    this.statusMsg = '';

    try {
      const cmd: PageCommand = {
        method: 'screenCapture',
        params: {
          xpath: '/html/body/div/p[2]/a'
        }
      };

      const res = await this.controller.executeAIPageCommand(JSON.stringify(cmd)) as string;

      if (!res || res.length === 0) {
        this.statusMsg = `❌ Error: The kernel returned an empty response.`;
        return;
      }

      const responseObj = JSON.parse(res) as AiCommandResponse;

      if (responseObj.code === 10) {
        const base64Result = responseObj.data ?? '';
        this.imgData = base64Result.replace(/\s/g, '');
        this.statusMsg = '✅ Screenshot captured successfully.';
      } else {
        const errorMsg = responseObj.message ?? 'Unknown kernel error.';
        this.statusMsg = `❌ Screenshot failed (Code: ${responseObj.code}): ${errorMsg}`;
      }

    } catch (e) {
      const error = e as BusinessError;
      this.statusMsg = `❌ API call or parsing failed: ${error.message}`;
    }
  }

  build() {
    Row() {
      Web({ src: 'https://www.example.com', controller: this.controller })
        .width('75%')
        .height('100%')

      Column({ space: 10 }) {
        Button('Take Screenshot')
          .width('100%')
          .onClick(() => this.capture())

        Image(this.imgData ? `data:image/png;base64,${this.imgData}` : '')
          .width('100%')
          .aspectRatio(1)
          .backgroundColor('#F0F0F0')
          .objectFit(ImageFit.Contain)
          .border({ width: 1, color: '#DCDCDC' })

        if (this.statusMsg) {
          Text(this.statusMsg)
            .width('100%')
            .fontSize(12)
            .fontColor(this.statusMsg.includes('✅') ? '#4CAF50' : '#F44336')
            .textAlign(TextAlign.Center)
            .padding(8)
            .backgroundColor(this.statusMsg.includes('✅') ? '#E8F5E9' : '#FFEBEE')
            .borderRadius(4)
        }
      }
      .width('25%')
      .padding(10)
      .height('100%')
    }
    .width('100%')
    .height('100%')
  }
}
```

## getZoomLevel

Obtains the scale ratio of the current web page. This command is a pure query operation and is not restricted by [zoomControlAccess](./arkts-basic-components-web-attributes.md#zoomcontrolaccess22).

### GetZoomLevelCommand

```json
{
  "method": "getZoomLevel",
  "params": {}
}
```

### Input Parameter Description

| Name | Sub-Parameter | Parameter Item | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | Yes | Command name, fixed as `getZoomLevel`. |
| params | - | - | Object | No | Command parameter. This command does not read the `params` content. An empty object can be passed or the parameter can be omitted. |

> **NOTE**
>
> - The returned `zoomLevel` field is the scale ratio of the current web page (1.0 = 100%), consistent with the semantics of the value passed to [setZoomLevel](./arkts-apis-webview-AIPageInteraction.md#setzoomlevel).
> - After setting any valid value via [setZoomLevel](./arkts-apis-webview-AIPageInteraction.md#setzoomlevel), reading through this command yields a return value with an error not exceeding 0.001.
> - If the user first zooms via CTRL+Wheel and then calls this command, the current user zoom ratio is returned.

### ZoomLevelResult

| Name | Type | Description |
| ---- | ---- | ---- |
| code | number | Execution result code. For values, see [Command Execution Result Code Description](./arkts-apis-webview-AIPageResult.md#command-execution-result-code-description). |
| message | string | Execution result description. `"success"` when successful. |
| zoomLevel | number | Current web page scale ratio. Returned on success. |

### Test Page

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
  <body>
    <h1>Zoom Level Demo</h1>
    <p>The current zoom level can be queried via getZoomLevel and modified via setZoomLevel (see AIPageInteraction for details).</p>
  </body>
</html>
```

### Request Example

```json
{
  "method": "getZoomLevel",
  "params": {}
}
```

### Response Example

On success (the current page scale ratio is 1.5):

```json
{
  "code": 10,
  "message": "success",
  "zoomLevel": 1.5
}
```

On failure:

`132` (browser or host is null, usually indicating that the Web instance is unavailable):

```json
{
  "code": 132,
  "message": "browser or host is null"
}
```
<!--no_check-->