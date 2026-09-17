# PanelInfo

Defines attributes of the word selection panel, including its type, position, and size. You can specify the panel type (menu panel or main panel) using **panelType**, set the coordinates of the upper left corner of the panel using **x** and **y**, and set the panel size using **width** and **height**. These attributes collectively define the display form of the panel.

**Since:** 24

**System capability:** SystemCapability.SelectionInput.Selection

## Modules to Import

```TypeScript
import { PanelInfo, PanelType } from '@kit.BasicServicesKit';
```

## height

```TypeScript
height: number
```

Height of the word selection panel, in px. The value range is (0, +∞). If **0** or a negative value is passed, the panel cannot be created.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.SelectionInput.Selection

## panelType

```TypeScript
panelType: PanelType
```

Word selection panel types, which include two options. For details, see [PanelType](arkts-basicservices-selectioninput-selectionpanel-paneltype-e.md).

**Type:** [PanelType](arkts-basicservices-selectioninput-selectionpanel-paneltype-e.md)

**Default:** MENU_PANEL

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.SelectionInput.Selection

## width

```TypeScript
width: number
```

Width of the word selection panel, in px. The value range is (0, +∞). If **0** or a negative value is passed, the panel cannot be created.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.SelectionInput.Selection

## x

```TypeScript
x: number
```

X-coordinate of the upper left corner of the word selection panel, in px. The upper left corner of the main screen is the origin, and the positive direction of the X axis is rightward. The value range is [0, +∞). If a negative value is passed, the panel cannot be created.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.SelectionInput.Selection

## y

```TypeScript
y: number
```

Y-coordinate of the upper left corner of the word selection panel, in px. The upper left corner of the main screen is the origin, and the positive direction of the Y axis is downward. The value range is [0, +∞). If a negative value is passed, the panel cannot be created.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.SelectionInput.Selection
