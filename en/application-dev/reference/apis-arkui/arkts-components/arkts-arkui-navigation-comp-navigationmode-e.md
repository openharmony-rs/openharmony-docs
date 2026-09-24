# NavigationMode

```TypeScript
declare enum NavigationMode
```

Display mode of the navigation page. When **Navigation** is displayed in split-column mode, a divider is displayed between the navigation page and the content area.

> **NOTE:** 
> 
> For simplicity, **calcNavBarWidth** is defined as follows: Component width �C minContentWidth �C Divider width (1 px)

**Table 1** Relationship between actual navBarWidth and the developer-defined value

| Developer-defined navBarWidth| calcNavBarWidth Value| Actual navBarWidth|  
| --- | --- | --- |  
| navBarWidth &lt; minNavBarWidth | NA | minNavBarWidth |
| navBarWidth  
> maxNavBarWidth | calcNavBarWidth
> maxNavBarWidth | maxNavBarWidth |

| navBarWidth  
> maxNavBarWidth | calcNavBarWidth &lt; minNavBarWidth | minNavBarWidth |

| navBarWidth  
> maxNavBarWidth | minNavBarWidth �� calcNavBarWidth �� maxNavBarWidth | calcNavBarWidth |

| minNavBarWidth �� navBarWidth �� maxNavBarWidth | calcNavBarWidth �� minNavBarWidth | minNavBarWidth |  
| minNavBarWidth �� navBarWidth �� maxNavBarWidth | minNavBarWidth &lt; calcNavBarWidth &lt;= navBarWidth | calcNavBarWidth |  
| minNavBarWidth �� navBarWidth �� maxNavBarWidth | calcNavBarWidth  
> navBarWidth | navBarWidth |

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Stack

```TypeScript
Stack
```

The navigation page and content area are displayed independently of each other, which are equivalent to two pages.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Split

```TypeScript
Split
```

The navigation page and content area are displayed in different columns.

**1.** Table 1 describes the relationship between the actual resulting **navBarWidth** and the value set by you.

**2.** When the component size is decreased, the content area is shrunk until its width reaches the value defined by **minContentWidth**, and then the navigation page is shrunk until its width reaches the value defined by **minNavBarWidth**. if the component size is further decreased, the content area is further shrunk until it disappears, and then navigation page is shrunk.

**3.** When the navigation page is set to a fixed size and the component size is continuously decreased, the navigation page is shrunk.

**4.** If only **navBarWidth** is set, the width of the navigation page is fixed at the value of **navBarWidth**, and the divider cannot be dragged.

**5.** The touch target of the divider is 2 vp on each side (left and right). Therefore, it is recommended that you keep a minimum distance of 4 vp from this area to avoid unintended interactions.

**6.** In Split mode, if there is only one page in the content area, the back button will not be displayed in the upper left corner of the page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Auto

```TypeScript
Auto
```

In API version 9 and earlier versions: If the window width is greater than or equal to 520 vp, the Split mode is used; otherwise, the Stack mode is used.

In API version 10 and later versions: If the window width is greater than or equal to 600 vp, the Split mode is used; otherwise, the Stack mode is used. 600 vp = minNavBarWidth (240 vp) + minContentWidth (360 vp).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AUTO_WITH_ASPECT_RATIO

```TypeScript
AUTO_WITH_ASPECT_RATIO
```

If the navigation width is greater than the sum of minNavBarWidth and minContentWidth, and the navigation component's aspect ratio (height to width) is less than or equal to 1.2, the navigation component is displayed in split mode. Otherwise it's displayed in stack mode.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
