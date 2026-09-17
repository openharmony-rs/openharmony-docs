# Typical Scenarios of Immersive Light Sensing
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @tsj_20201-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=52a5cbcada092819266319713cb8ac383c813472 translatedAt=2026-08-31T02:55:43.515Z pushedAt=2026-09-01T03:18:38.219Z -->

This document provides development guidance for two typical scenarios of immersive light sensing, including the search box title bar effect and enabling immersive light sensing for the content area title bar.

## Search Box Title Bar Effect

In information browsing applications (such as news, forums, and novel reading applications), when you swipe up the home page content area, the title bar display range shrinks accordingly, while Immersive Light Sensing enhances the interactive experience of the title bar.

1. Set the bottom Tabs to float and enable immersive light sensing for the Tabs component. Also use [ExpandSafeArea](../reference/apis-arkui/arkui-ts/ts-universal-attributes-expand-safe-area.md#expandsafearea) to extend the displayed content to the status bar area, making the overall application experience more consistent.

   ```ts
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
       Navigation(this.exploreStack, {name: 'explore'})
         .hideTitleBar(true)
         .expandSafeArea([SafeAreaType.SYSTEM])
     }

     @Builder
     tabGameContent() {
       // Configure the corresponding page navigation through the system route table.
       Navigation(this.gameStack, {name: 'game'})
         .hideTitleBar(true)
         .expandSafeArea([SafeAreaType.SYSTEM])
     }

     build() {
       Tabs({ index: this.currentTab }) {
         TabContent() {
           this.tabExploreContent()
         }.tabBar(this.BottomTabBarItem('Explore', $r('sys.symbol.compass'), 0))
         // Extend the content area to the status bar area to create a unified interactive experience.
         .expandSafeArea([SafeAreaType.SYSTEM])

         TabContent() {
           this.tabGameContent()
         }.tabBar(this.BottomTabBarItem('Games', $r('sys.symbol.gamecontroller'), 1))
         .expandSafeArea([SafeAreaType.SYSTEM])

         TabContent() {
         }.tabBar(this.BottomTabBarItem('Apps', $r('sys.symbol.grid'), 2))

         TabContent() {
         }.tabBar(this.BottomTabBarItem('Atomic services', $r('sys.symbol.gearshape'), 3))
       }
       .barPosition(BarPosition.End)
       .barMode(BarMode.Fixed)
       .barOverlap(true)
       .barHeight(56)
       .barFloatingStyle({ barBottomMargin: 8, systemMaterial: new uiMaterial.ImmersiveMaterial({}) })
       .scrollable(true)
       .expandSafeArea([SafeAreaType.SYSTEM])
       .onChange((index: number) => {
         this.currentTab = index
       })
     }
   }
   ```

2. For the target page to navigate to, enable immersive light sensing for the title bar area of the corresponding tab page through [NavigationTitleOptions](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationtitleoptions11). It is recommended that you set the `BarStyle` of the `Navigation` component to `STACK` mode so that the content area is displayed below the title bar, thereby achieving a see-through effect. The following code implements the following effects:

- Immersive light sensing is enabled for the title bar and its child components.

- When swiping up, the search box is hidden while the category list is retained and highlighted. Immersive light sensing is enabled for the category list items to improve user interaction experience and content exposure.

  ```ts
  @ComponentV2
  struct ExploreHomePage {
    @Local currentIndex: number = 0
    @Local searchOpacity: number = 1
    @Local classifyType: Array<string> = [
       'Strategy', 'Action', 'Competitive', 'Shooting', 'Card', 'Sports', 'Casual', 'Music'
     ]
    titleHeight:number = 150
    @Local scrollOffset: number = 0
    @Local titleOffset: number = 0
    @Builder
    exploreTitleBar() {
      Column() {
        Row() {
          Text('Explore').fontSize(28).fontWeight(FontWeight.Bold).fontColor('#1A1A1A')
          Blank()
          Search({ placeholder: 'Explore Explore' })
            .searchButton('Search')
            .height(40)
            .width(220)
            .systemMaterial(new uiMaterial.ImmersiveMaterial({}))
        }.expandSafeArea([SafeAreaType.SYSTEM])
        .width('100%')
        .opacity(this.searchOpacity)
        .height(50)

        List({space: 12}) {
          ForEach(this.classifyType, (item: string, index: number) => {
            ListItem() {
              Row() {
                SymbolGlyph($r('sys.symbol.star_fill'))
                  .fontSize(20)
                  .fontColor(['#d3d3d3'])
                  .margin({left: 16})
                Text(item)
                  .fontSize(16)
                  .fontColor(this.currentIndex === index ? Color.White : '#666666')
                  .padding({ left: 4, right: 12, top: 6, bottom: 6})
              }.borderRadius(16)
              .systemMaterial(new uiMaterial.ImmersiveMaterial({
                materialColor: this.currentIndex === index ? '#333333' : undefined,
                lightEffect: {color: Color.White}
              }))
            }
          })
        }.listDirection(Axis.Horizontal)
        .width('100%')
        .scrollBar(BarState.Off)
        .margin(5)
      }.expandSafeArea([SafeAreaType.SYSTEM])
      .width('100%')
      .height(this.titleHeight)
      .padding({ left: 20, right: 20})
      .position({x: 0, y: -this.titleOffset})
      // Enable immersive light sensing for the Column component.
      .systemMaterial(new uiMaterial.ImmersiveMaterial({}))
    }

    build() {
      NavDestination() {
        Scroll() {
          // Specific content of the scroll area.
          Column() {
            Image($r('app.media.startIcon')).width('100%').height(180)
              .borderRadius(12)
              .backgroundColor('#e0e0e0')
              .objectFit(ImageFit.Cover)

            List() {
              // You need to customize the listItems parameter. The data structure in the example is interface ListItemData { name: string; image: Resource; id: string }.
              ForEach(listItems, (item: ListItemData) => {
                ListItem() {
                  Row() {
                    SymbolGlyph(item.image).fontSize(36)
                      .fontColor(['#007dff'])
                      .margin({ right: 16})
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
        .contentStartOffset(this.titleHeight)
        .scrollable(ScrollDirection.Vertical)
        .scrollBar(BarState.Off)
        .edgeEffect(EdgeEffect.Spring)
        .width('100%')
        .height('100%')
        .onDidScroll((xOffset: number, yOffset: number, state: ScrollState) => {
          this.scrollOffset += yOffset
          // Within the search box size range.
          if (this.scrollOffset <= 50) {
            this.titleOffset = this.scrollOffset;
            this.searchOpacity = 1 - this.titleOffset / 50
          }
        })
      }.title(
        { builder: this.exploreTitleBar, height: this.titleHeight },
        { barStyle: BarStyle.STACK,
          systemMaterial: new uiMaterial.ImmersiveMaterial({})
       }
     ).hideBackButton(true)
      .expandSafeArea([SafeAreaType.SYSTEM])
    }
  }
  ```
<!--RP1--><!--RP1End-->

## Enabling Immersive Light Sensing for the Content Area Title Bar

Immersive light sensing is currently subject to certain constraints. For details, see [Immersive Light Sensing Power Optimization](./arkts-immersive-light-sense-constraints.md). In scenarios where the content area scrolls and contains multiple levels of titles, when a content area title scrolls to the title bar area, you can embed the corresponding content into the title bar for display, so that the content area title is shown in the NavDestination title bar area, thereby improving the user interaction experience.

1. Extract the subtitles in the content area as independent components.

   ```ts
   @ComponentV2
   export struct ClassifyComponent {
     classifyType: Array<string> = [
       'Strategy', 'Action', 'Competitive', 'Shooting', 'Card', 'Sports', 'Casual', 'Music'
     ]
  
     @Local currentIndex: number = 0
  
     build() {
       List({space: 12}) {
         ForEach(this.classifyType, (item: string, index) => {
           ListItem() {
             Row() {
               SymbolGlyph($r('sys.symbol.star_fill'))
                 .fontSize(20)
                 .fontColor(['#d3d3d3'])
                 .margin({ left: 16})
               Text(item)
                 .fontColor(this.currentIndex === index ? Color.White : '#666666')
                 .fontSize(16)
                 .padding({ left: 4, right: 12, top: 6, bottom: 6})
             }.borderRadius(16)
             .systemMaterial(new uiMaterial.ImmersiveMaterial({
               materialColor: this.currentIndex === index ? '#333333' : undefined,
               lightEffect: { color: Color.White }
             }))
             .onClick(() => {
               this.currentIndex = index
             })
           }
         })
       }.listDirection(Axis.Horizontal)
       .width('100%')
       .scrollBar(BarState.Off)
       .expandSafeArea([SafeAreaType.SYSTEM])
       .margin(5)
       .alignListItem(ListItemAlign.Center)
     }
   }
   ```

2. Scroll the content area. When the content area title scrolls to the title bar area, switch it to display in the title bar.

   ```ts
   // Add the system route table entry.
   @ComponentV2
   struct GamePage {
     @Local titleHeight: number = 100
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
         }.borderRadius(180).width(40).height(40)
           .systemMaterial(new uiMaterial.ImmersiveMaterial({
             lightEffect: { color: Color.White },
             materialColor: '#d3d3d3'
         }))
         .backgroundColor(Color.Transparent)
       }.expandSafeArea([SafeAreaType.SYSTEM])
       .width('100%')
       .height('100%')
       .padding({ left: 20, right: 20 })
       .systemMaterial(new uiMaterial.ImmersiveMaterial({}))
       .alignItems(VerticalAlign.Center)
     }

     build() {
       NavDestination() {
         Scroll() {
           Column() {
             // Replace this with the actual resource file.
             Image($r('app.media.background'))
               .width('100%')
               .height(180)
               .borderRadius(12)
               .backgroundColor('#fff3e0')
               .objectFit(ImageFit.Cover)
             ClassifyComponent().id('content').visibility(this.showTitle ? Visibility.Hidden : Visibility.Visible)
             List() {
               // Customize the listItems parameter. The data structure in the example is interface ListItemData { name: string; image: Resource; id: string}.
               ForEach(listItems, (item: ListItemData) => {
                 ListItem() {
                   Row() {
                     SymbolGlyph(item.image).fontSize(36).fontColor(['#ff6d00']).margin({ right: 16 })
                     Text(item.name).fontSize(16).fontColor('#333333')
                   }.width('100%')
                   .padding({ left: 20, right: 20, top: 14, bottom: 14 })
                 }
               }, (item: ListItemData) => item.id)
             }.width('100%')
             .margin({top: 8})
             .nestedScroll({scrollForward: NestedScrollMode.PARENT_FIRST, scrollBackward: NestedScrollMode.SELF_FIRST})
             .divider({strokeWidth: 5, color: '#e0e0e0', startMargin: 72, endMargin: 20})
           }.padding({left: 16, right: 16, top: 8, bottom: 16})
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
             this.showTitle = false;
             this.listVisible = Visibility.Hidden
             return
           }
           if (curOffset < this.titleEnd) {
             this.showTitle = true;
             this.listVisible = Visibility.Visible
             return
           }
           this.titleHeight = (curOffset - this.titleEnd) / (this.titleHeight - this.titleEnd)
         })
       }.onShown(() => {
         let titleInfo = this.getUIContext().getComponentUtils().getRectangleById('text');
         this.titleStart = this.getUIContext().px2vp(titleInfo.windowOffset.y)
         this.titleEnd = this.getUIContext().px2vp(titleInfo.size.height)
         this.contentOffset = this.getUIContext().px2vp(this.getUIContext().getComponentUtils().getRectangleById('content').windowOffset.y)
       })
       .expandSafeArea([SafeAreaType.SYSTEM])
       .hideBackButton(true)
       .title({ builder: this.gameTitleBar, height: this.titleHeight }, {
         barStyle: BarStyle.STACK,
         systemMaterial: new uiMaterial.ImmersiveMaterial({})
       })
     }
   }
   ```

<!--RP2--><!--RP2End-->