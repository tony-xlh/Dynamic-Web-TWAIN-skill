---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface UiConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface UiConfig
breadcrumbText: Interface UiConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface UiConfig Page
permalink: /api/interface/uiconfig.html
---

# UiConfig

## Syntax

```typescript
interface UiConfig {
    type: string; 
    flexDirection?: string; 
    id?: string; 
    className?: string; 
    style?: CSSStyleDeclaration;  
    tooltip?: string; 
    events?: Record<string, string>;
    children?: (UiConfig | string)[]; 
}
```

## Attributes

### type

The type of the element.

Supported value: `Dynamsoft.DDV.Elements.Layout`, `Dynamsoft.DDV.Elements.Button` and [built-in elements]({{ site.ui }}default_elements.html).

### flexDirection

The flexDirection of the element. Only takes effect when [`type`](#type) is `Dynamsoft.DDV.Elements.Layout`.

Supported value: `column`, `row`

Default value is `row`.

### id

The id of Dom Element. If it is not specified, a random string will be generated.

### className

The className of CSS.

### style

The style which will cover CSS.

### tooltip

The tooltip of the element. Only takes effect when [`type`](#type) is `Dynamsoft.DDV.Elements.Button` and [built-in elements]({{ site.ui }}default_elements.html).

### events

The event of the element. Only takes effect when [`type`](#type) is `Dynamsoft.DDV.Elements.Button` and [built-in elements]({{ site.ui }}default_elements.html).

### children

Only takes effect when [`type`](#type) is `Dynamsoft.DDV.Elements.Layout`.

## Related

- [`getDefaultUiConfig()`]({{ site.api }}namespace/ddv.html#static-getdefaultuiconfig)
- `getUiConfig()` in 
    - [EditViewer Class]({{ site.api }}class/editviewer.html#getuiconfig)
    - [CaptureViewer Class]({{ site.api }}class/captureviewer.html#getuiconfig)
    - [PerspectiveViewer Class]({{ site.api }}class/perspectiveviewer.html#getuiconfig)
    - [BrowseViewer Class]({{ site.api }}class/browseviewer.html#getuiconfig)
    - [CustomViewer Class]({{ site.api }}class/customviewer.html#getuiconfig)
- `updateUiConfig()` in
    - [EditViewer Class]({{ site.api }}class/editviewer.html#updateuiconfig)
    - [CaptureViewer Class]({{ site.api }}class/captureviewer.html#updateuiconfig)
    - [PerspectiveViewer Class]({{ site.api }}class/perspectiveviewer.html#updateuiconfig)
    - [BrowseViewer Class]({{ site.api }}class/browseviewer.html#updateuiconfig)
    - [CustomViewer Class]({{ site.api }}class/customviewer.html#updateuiconfig)