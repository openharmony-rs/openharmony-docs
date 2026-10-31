# Basic Concepts

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lanshouren-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=93458ca6cb2d2618da5fc6bdfa2819210775aa38 translatedAt=2026-06-23T07:35:17.033Z pushedAt=2026-06-23T11:15:47.878Z -->

Grid components layout elements in a grid system which is built based on **\<grid-container>**, **\<grid-row>**, and **\<grid-col>** containers.

As a layout-auxiliary positioning tool, the grid system plays an essential role in graphic design, website design, and the UI design of mobile devices. The grid system offers the following advantages for mobile devices:

1. Provides rules for layout design and resolves issues of dynamic layout across devices with different sizes.

2. Provides a unified positioning method for the system to ensure layout consistency among modules on different devices.

3. Provides a flexible spacing adjustment method for applications to keep up with layout in special scenarios.

## Concepts

A grid system consists of three attributes: margins, gutters, and columns.

1. Margins:

   Margins are used to control the distances between elements and edges of a screen. You can define different margins based on the screen sizes to serve as the unified specifications for breakpoints.

2. Gutters:

   Gutters are used to control the distances between elements. You can define different gutter values based on the screen sizes to serve as the unified specifications for breakpoints. To achieve a good visual effect, set the values of gutters not greater than the margin values.

3. Columns:

   Columns are used for positioning in the layout. The positioning for different screen sizes is determined by the numbers of columns. The column width is automatically calculated based on the actual device width and the number of columns when the margins and gutters meet the specifications.

   ![Columns](figures/Columns.png)

   **Breakpoint System**

The grid system defines the mapping between the number of columns and the width of devices, which is known as the rules in the breakpoint system.

The grid system uses the horizontal virtual pixels (vps) to determine the breakpoints. Different devices display different numbers of columns based on their horizontal vps (**autoDesignWidth** is set to **true**) within different breakpoint ranges.

**xs**: 2 columns for 0 &lt; horizontal vp &lt; 320

**sm**: 4 columns for 320 &le; horizontal vp &lt; 600

**md**: 8 columns for 600 &le; horizontal vp &lt; 840

**lg**: 12-column for 840 &le; horizontal vp