---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface InkStyle
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface InkStyle
breadcrumbText: Interface InkStyle
description: Dynamsoft Document Viewer Documentation API Reference Interface InkStyle Page
permalink: /api/interface/annotationinterface/inkstyle.html
---

# InkStyle

## Syntax

```typescript
interface InkStyle {
    borderWidth?: number;
    borderColor?: string;
    opacity?: number;
}
```

## Attributes


### borderWidth

The border width of annotation. The unit is point. 

Default value: 1

### borderColor

The border color of annotation.

Default value: `rgb(0,0,0)` 

**Remark**

Supported string value of `borderColor` and `background`: 
- Named color, for example, `red`, `green`, etc.
- HEX(`#RRGGBB`), for example, `#ff0000`, `#008000`, etc.
- RGB(`rgb(red, green, blue)`), for example, `rgb(255, 0, 0)`, `rgb(0, 128, 0)`, etc.
- HSL(`hsl(Hue, Saturation, Lightness)`), for example, `hsl(0, 100%, 50%)`, `hsl(120, 100%, 25%)` ,etc.

### opacity

The opacity of the whole annotation. The value range is [0,1], value which is greater than 1 will default to 1. 

Default value: 1

## Related

- [`EditViewerConstructorOptions`]({{ site.api }}interface/editviewerconstructoroptions.html)