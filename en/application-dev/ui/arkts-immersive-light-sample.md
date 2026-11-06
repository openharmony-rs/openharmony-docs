# Typical Scenarios of Immersive Light Sensing
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @tsj_20201-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=09072f550e95bcc48e2e25f1892f09e5275416b8 translatedAt=2026-11-05T03:22:32.428Z pushedAt=2026-11-05T08:31:34.345Z nl=1 -->

This document provides development guidance for two typical scenarios of immersive light sensing, including the search box title bar effect and enabling immersive light sensing for the content area title bar.

## Search Box Title Bar Effect

In information browsing applications (such as news, forums, and novel reading applications), when you swipe up the home page content area, the title bar display range shrinks accordingly, while Immersive Light Sensing enhances the interactive experience of the title bar.

1. Set the bottom Tabs to float and enable immersive light sensing for the Tabs component. Also use [ExpandSafeArea](../reference/apis-arkui/arkui-ts/ts-universal-attributes-expand-safe-area.md#ignorelayoutsafearea20) to extend the displayed content to the status bar area, making the overall application experience more consistent.
   <!-- @[immersive_tabs](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ImmersiveLightSense/entry/src/main/ets/pages/immersiveLightSense/BestPractice.ets) -->
   ```TypeScript
   @Entry
   @ComponentV2
   struct BestPractise {
     @Local currentTab: number = 0
     exploreStack: NavPathStack = new NavPathStack()
     gameStack: NavPathStack = new NavPathStack()

     @Builder
     BottomTabBarItem(title: string, icon: Resource, index: number) {
       Column() {
         SymbolGlyph(icon)
           .fontSize(22)
           .fontColor(this.currentTab === index ? ['#007dff'] : ['#999999'])
         Text(title)
           .fontSize(10)
           .fontColor(this.currentTab === index ? '#007dff' : '#999999')
           .margin({ top: 2 })
       }.justifyContent(FlexAlign.Center)
       .width('100%')
       .height('100%')
     }

     @Builder
     tabExploreContent() {
       // Configure the corresponding page navigation through the system route table.
       Navigation(this.exploreStack, { name: 'explore' })
         .hideTitleBar(true)
     }

     @Builder
     tabGameContent() {
       // Configure the corresponding page navigation through the system route table.
       Navigation(this.gameStack, { name: 'game' })
         .hideTitleBar(true)
     }

     build() {
       Tabs({ index: this.currentTab }) {
         TabContent() {
           this.tabExploreContent()
         }.tabBar(this.BottomTabBarItem('Explore', $r('sys.symbol.compass'), 0))

         TabContent() {
           this.tabGameContent()
         }.tabBar(this.BottomTabBarItem('Games', $r('sys.symbol.gamecontroller'), 1))

         TabContent() {
         }.tabBar(this.BottomTabBarItem('Apps', $r('sys.symbol.grid'), 2))

         TabContent() {
         }.tabBar(this.BottomTabBarItem('Atomic services', $r('sys.symbol.gearshape'), 3))
       }
       .barPosition(BarPosition.End)
       .barMode(BarMode.Fixed)
       .barOverlap(true)
       .barFloatingStyle({ systemMaterial: new uiMaterial.ImmersiveMaterial({ style: uiMaterial.ImmersiveStyle.THIN }) })
       .ignoreLayoutSafeArea([LayoutSafeAreaType.SYSTEM], [LayoutSafeAreaEdge.BOTTOM])
       .height(LayoutPolicy.matchParent)
       .onChange((index: number) => {
         this.currentTab = index
       })
     }
   }
   ```

2. For the target page to navigate to, enable immersive light sensing for the title bar area of the corresponding tab page through [NavigationTitleOptions](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationtitleoptions11). It is recommended to set the `BarStyle` of the `Navigation` component to `STACK` mode so that the content area is displayed below the title bar, achieving a see-through effect. The following code implements the following effects: immersive light sensing is enabled for the title bar and its child components. When swiping up, the search box is hidden while the category list is retained and highlighted. Immersive light sensing is enabled for the category list items to improve user interaction experience and content exposure.
   <!-- @[explore_home_page](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ImmersiveLightSense/entry/src/main/ets/pages/immersiveLightSense/ExploreHomePage.ets) -->
   ```TypeScript
   @ComponentV2
   struct ExploreHomePage {
     @Local currentIndex: number = 0
     @Local searchOpacity: number = 1
     @Local classifyType: Array<string> = []
     totalTitleHeight = 110
     @Local scrollOffset: number = 0
     @Local titleOffset: number = 0

     @Builder
     exploreTitleBar() {
       Column() {
         Row() {
           Text('Explore')
             .fontSize(28)
             .fontWeight(FontWeight.Bold)
             .fontColor('#1A1A1A')
           Blank()
           Search({ placeholder: 'Explore Explore' })
             .searchButton('Search')
             .height(40)
             .width(220)
             .systemMaterial(new uiMaterial.ImmersiveMaterial({}))
         }
         .width('100%')
         .opacity(this.searchOpacity)
         .height(50)

         ClassifyComponent()
       }
       .width('100%')
       .padding({ left: 20, right: 20 })
       .position({ x: 0, y: -this.titleOffset })
     }

     build() {
       NavDestination() {
         Scroll() {
           // Content of the sliding area.
           Column() {
             Image($r('app.media.startIcon')).width('100%').height(180)
               .borderRadius(12)
               .backgroundColor('#e0e0e0')
               .objectFit(ImageFit.Cover)

             List() {
               ForEach(listItems, (item: ListItemData) => {
                 ListItem() {
                   Row() {
                     SymbolGlyph(item.image).fontSize(36)
                       .fontColor(['#007dff'])
                       .margin({ right: 16 })
                     Text(item.name).fontSize(16)
                       .fontColor('#333333')
                   }.width('100%')
                   .padding({ left: 20, right: 20, top: 14, bottom: 14 })
                 }
               }, (item: ListItemData) => item.id)
             }
           }
         }
         // Avoid the title bar display area.
         .contentStartOffset(this.totalTitleHeight)
         .scrollable(ScrollDirection.Vertical)
         .scrollBar(BarState.Off)
         .edgeEffect(EdgeEffect.Spring)
         .width('100%')
         .height('100%')
         .onDidScroll((xOffset: number, yOffset: number, state: ScrollState) => {
           this.scrollOffset += yOffset
           if (this.scrollOffset <= 50) {
             this.titleOffset = this.scrollOffset
             this.searchOpacity = 1 - this.titleOffset / 50
           }
         })
       }.title(
         { builder: this.exploreTitleBar, height: this.totalTitleHeight },
         { barStyle: BarStyle.STACK,
           // Set the title bar blur.
           scrollEffectOptions: {
             scrollEffectType: ScrollEffectType.GRADUAL_BLUR
           }
         }
       ).hideBackButton(true)
     }
   }
   ```
<!--RP1--><!--RP1End-->

## Enabling Immersive Light Sensing for the Content Area Title Bar

Immersive light sensing is currently subject to certain constraints. For details, see [Immersive Light Sensing Power Optimization](./arkts-immersive-light-sense-constraints.md). In scenarios where the content area scrolls and contains multiple levels of titles, when a content area title scrolls to the title bar area, you can embed the corresponding content into the title bar for display, so that the content area title is shown in the NavDestination title bar area, thereby improving the user interaction experience.

1. Extract the subtitles in the content area as independent components.
   <!-- @[classify_component](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ImmersiveLightSense/entry/src/main/ets/pages/immersiveLightSense/Utils.ets) -->

   ``` TypeScript
   @ComponentV2
   export struct ClassifyComponent {
     @Local selectedIndexes: Array<number> = [0]
     info: Array<ChipGroupItemOptions> = []

     aboutToAppear(): void {
       let classifyType: string[] = ['Strategy', 'Action', 'Competitive', 'Shooting', 'Card', 'Sports', 'Casual', 'Music']

       for (let index: number = 0; index < classifyType.length; index++) {
         this.info.push({
           label: { text: classifyType[index] },
           prefixSymbol: {
             activated: new SymbolGlyphModifier($r('sys.symbol.star_fill')).fontSize(20).fontColor(['#d3d3d3']),
             normal: new SymbolGlyphModifier($r('sys.symbol.star_fill')).fontSize(20).fontColor([Color.Black])
           }
         })
       }
     }

     build() {
       ChipGroup({
         items: this.info,
         itemStyle: {
           backgroundColor: Color.Transparent,
           selectedFontColor: '#d3d3d3'
         },
         backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
           colorInvert: true,
           interactive: true
         }),
         selectedIndexes: this.selectedIndexes,
         onChange: (activeIndexes: Array<number>) => {
           this.selectedIndexes = activeIndexes
         }
       })
     }
   }
   ```

2. Scroll the content area. When the content area title scrolls to the title bar area, switch it to display in the title bar.

   <!-- @[game_page](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ImmersiveLightSense/entry/src/main/ets/pages/immersiveLightSense/GamePage.ets) -->
  
   ``` TypeScript
   @ComponentV2
   struct GamePage {
     @Local titleHeight: number = 60
     @Local scrollOffset: number = 0
     @Local showTitle: boolean = false
     @Local titleOpacity: number = 1
     @Local contentOffset: number = 0
     totalOffset: number = 0
     @Local textOffset: number = 0
     titleEnd: number = 0
     titleStart: number = 0
     @Local listVisible: Visibility = Visibility.Visible

     @Builder
     gameTitleBar() {
       Row() {
         if (this.showTitle) {
           ClassifyComponent()
         } else {
           Text('Game')
             .fontSize(28)
             .fontWeight(FontWeight.Bold)
             .fontColor('#1A1A1A')
             .opacity(this.titleOpacity)
             .id('text')
           Blank()
         }
         Button() {
           SymbolGlyph($r('sys.symbol.AI_search')).fontSize(20)
         }.borderRadius(180)
         .width(40)
         .height(40)
         .backgroundColor(Color.Transparent)
         .systemMaterial(new uiMaterial.ImmersiveMaterial({
           lightEffect: { color: Color.White },
           materialColor: '#80d3d3d3'
         }))
       }
       .width('100%')
       .height('100%')
       .padding({ left: 20, right: 20 })
       .alignItems(VerticalAlign.Center)
     }

     build() {
       NavDestination() {
         Scroll() {
           Column() {
             Image($r('app.media.startIcon'))
               .width('100%')
               .height(180)
               .borderRadius(12)
               .backgroundColor('#fff3e0')
               .objectFit(ImageFit.Cover)
             ClassifyComponent()
               .id('content')
               .visibility(this.showTitle ? Visibility.Hidden : Visibility.Visible)
             List() {
               ForEach(listItems, (item: ListItemData) => {
                 ListItem() {
                   Row() {
                     SymbolGlyph(item.image)
                       .fontSize(36)
                       .fontColor(['#ff6d00'])
                       .margin({ right: 16 })
                     Text(item.name).fontSize(16).fontColor('#333333')
                   }.width('100%')
                   .padding({ left: 20, right: 20, top: 14, bottom: 14 })
                 }
               }, (item: ListItemData) => item.id)
             }.width('100%')
             .margin({ top: 8 })
             .nestedScroll({
               scrollForward: NestedScrollMode.PARENT_FIRST,
               scrollBackward: NestedScrollMode.SELF_FIRST
             })
             .divider({ strokeWidth: 5, color: '#e0e0e0', startMargin: 72, endMargin: 20 })
           }.padding({ left: 16, right: 16, top: 8, bottom: 16 })
         }
         .contentStartOffset(this.titleHeight)
         .scrollable(ScrollDirection.Vertical)
         .scrollBar(BarState.Off)
         .edgeEffect(EdgeEffect.Spring)
         .width('100%')
         .height('100%')
         .onDidScroll((xOffset: number, yOffset: number) => {
           this.totalOffset += yOffset
           let curOffset = this.contentOffset - this.totalOffset
           if (curOffset > this.titleEnd) {
             this.showTitle = false
             this.listVisible = Visibility.Hidden
             return
           }
           if (curOffset < this.titleEnd) {
             this.showTitle = true
             this.listVisible = Visibility.Visible
             return
           }
           this.titleHeight = (curOffset - this.titleEnd) / (this.titleHeight - this.titleEnd)
         })
       }.onShown(() => {
         let titleInfo = this.getUIContext().getComponentUtils().getRectangleById('text')
         this.titleStart = this.getUIContext().px2vp(titleInfo.windowOffset.y)
         this.titleEnd = this.getUIContext().px2vp(titleInfo.size.height)
         this.contentOffset = this.getUIContext().px2vp(
           this.getUIContext().getComponentUtils().getRectangleById('content').windowOffset.y
         )
       })
       .hideBackButton(true)
       .title({ builder: this.gameTitleBar, height: this.titleHeight }, {
         barStyle: BarStyle.STACK,
         scrollEffectOptions: {
           scrollEffectType: ScrollEffectType.GRADUAL_BLUR
         }
       })
     }
   }
   ```

<!--RP2--><!--RP2End-->
