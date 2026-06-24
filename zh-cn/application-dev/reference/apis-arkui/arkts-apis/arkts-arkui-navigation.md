# Navigation

Defines Navigation Component instance.


## Navigation

```TypeScript
Navigation()
```

����·�ɵ����ĸ���ͼ������������ʹ��[NavRouter]{@link nav_router}�������ҳ��·�ɡ�

**起始版本：** 8

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为8.

## Navigation

```TypeScript
Navigation(pathInfos: NavPathStack)
```

�󶨵�����������Navigation�����������ʹ��[NavPathStack]{@link NavPathStack}���
[navDestination]{@link NavigationAttribute#navDestination}���Խ���ҳ��·�ɡ�

**起始版本：** 10

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为10.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | NavPathStack | 是 |  |

## Navigation

```TypeScript
Navigation(pathInfos: NavPathStack, homeDestination: HomePathInfo)
```

��·��ջ��Navigation���������ָ��һ��NavDestination��ΪNavigation�ĵ���ҳ����ҳ����������ʹ��[NavPathStack]{@link NavPathStack}���
[navDestination]{@link NavigationAttribute#navDestination}���Ի���ϵͳ·�ɱ�����ҳ��·�ɡ�ʹ��ʾ���ο�
[ʾ��16��Navigationʹ��NavDestination��Ϊ����ҳ��](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#ʾ��16navigationʹ��navdestination��Ϊ����ҳ)��

**起始版本：** 20

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为20.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | NavPathStack | 是 |  |
| homeDestination | HomePathInfo | 是 |  |

## 汇总

- [HomePathInfo](arkts-arkui-navigation-homepathinfo-i.md)
- [MoreButtonOptions](arkts-arkui-navigation-morebuttonoptions-i.md)
- [NavContentInfo](arkts-arkui-navigation-navcontentinfo-i.md)
- [NavigationAnimatedTransition](arkts-arkui-navigation-navigationanimatedtransition-i.md)
- [NavigationCommonTitle](arkts-arkui-navigation-navigationcommontitle-i.md)
- [NavigationConfiguration](arkts-arkui-navigation-navigationconfiguration-i.md)
- [NavigationCustomTitle](arkts-arkui-navigation-navigationcustomtitle-i.md)
- [NavigationDividerStyle](arkts-arkui-navigation-navigationdividerstyle-i.md)
- [NavigationInterception](arkts-arkui-navigation-navigationinterception-i.md)
- [NavigationMenuItem](arkts-arkui-navigation-navigationmenuitem-i.md)
- [NavigationMenuOptions](arkts-arkui-navigation-navigationmenuoptions-i.md)
- [NavigationOptions](arkts-arkui-navigation-navigationoptions-i.md)
- [NavigationTitleOptions](arkts-arkui-navigation-navigationtitleoptions-i.md)
- [NavigationToolbarOptions](arkts-arkui-navigation-navigationtoolbaroptions-i.md)
- [NavigationTransitionProxy](arkts-arkui-navigation-navigationtransitionproxy-i.md)
- [PopInfo](arkts-arkui-navigation-popinfo-i.md)
- [ScrollEffectOptions](arkts-arkui-navigation-scrolleffectoptions-i.md)
- [ToolbarItem](arkts-arkui-navigation-toolbaritem-i.md)
- [InterceptionCallback](arkts-arkui-navigation-interceptioncallback-t.md)
- [InterceptionModeCallback](arkts-arkui-navigation-interceptionmodecallback-t.md)
- [InterceptionShowCallback](arkts-arkui-navigation-interceptionshowcallback-t.md)
- [Material](arkts-arkui-navigation-material-t.md)
- [NavBar](arkts-arkui-navigation-navbar-t.md)
- [SystemBarStyle](arkts-arkui-navigation-systembarstyle-t.md)
- [BarStyle](arkts-arkui-navigation-barstyle-e.md)
- [LaunchMode](arkts-arkui-navigation-launchmode-e.md)
- [NavBarPosition](arkts-arkui-navigation-navbarposition-e.md)
- [NavigationMode](arkts-arkui-navigation-navigationmode-e.md)
- [NavigationOperation](arkts-arkui-navigation-navigationoperation-e.md)
- [NavigationTitleMode](arkts-arkui-navigation-navigationtitlemode-e.md)
- [ScrollEffectType](arkts-arkui-navigation-scrolleffecttype-e.md)
- [ToolbarItemStatus](arkts-arkui-navigation-toolbaritemstatus-e.md)
