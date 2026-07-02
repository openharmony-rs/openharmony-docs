# ArkUI Glossary

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--Designer: @jiangdayuan-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=5c79674ef648bfd10808cff71ec48d5a31ed9b31 translatedAt=2026-07-02T03:15:35.350Z pushedAt=2026-07-02T03:33:02.634Z -->

## A

### Accessibility Virtual Node

When you use self-drawing components for custom rendering, the content inside these components (such as drawn graphics and text) is usually not directly perceivable by accessibility services. An accessibility virtual node is an invisible accessibility node supplemented for self-drawing components, used to enable assistive applications to identify perceivable content within the self-drawn area.

## E

### Entity Node

A native node created by the backend, serving as the actual underlying carrier of a frontend node object. The frontend node is bound to the entity node through a reference relationship. When dispose is called to unbind them, the frontend node no longer corresponds to any entity node, and calling the API again may cause a crash or return a default value.

## I

### Imperative Node

A node created directly through constructors such as **new FrameNode()**. An imperative node can modify its own attributes and the structure of its child nodes.

## N

### Named Route

A routing method that performs page navigation through name-based identification rather than URL paths, primarily used for redirecting to pages within a package across packages (HAR or HSP shared packages).

## P

### Page Stack

The page navigation stack structure managed by the **Router** module, which records the order in which pages are pushed and popped, and can hold a maximum of 32 pages.

### Pre-loading Area

In lazy loading mode, the area immediately adjacent to the display range of a container component. Child components within this area are created and laid out in advance when the system is idle to improve list scrolling performance.

## R

### Route Map

A configuration mapping in **Navigation** that defines page route names, source file paths, and custom fields, used for finding target pages during route navigation.

### Route Stack

The stack structure of **NavDestination** pages, managed by **NavPathStack** in the **Navigation** component, which controls the entry and exit order of pages. It is a different navigation model from the page stack managed by **Router**.

## T

### Theme Skinning

A visual theme switching mechanism within an application, which can customize the application's global color scheme style and local color scheme style.

## Component Coordinate System

A coordinate system that takes the top‑left corner of the component as the origin, where the positive x‑axis points to the right and the positive y‑axis points downward. If the coordinate system is a three-dimensional coordinate system, the positive z‑axis points outward from the screen.

![coordinates](../reference/apis-arkui/arkui-ts/figures/coordinates.png)