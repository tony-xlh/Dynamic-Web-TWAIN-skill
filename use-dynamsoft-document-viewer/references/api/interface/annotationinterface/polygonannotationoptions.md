---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface PolygonAnnotationOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface PolygonAnnotationOptions
breadcrumbText: Interface PolygonAnnotationOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface PolygonAnnotationOptions Page
permalink: /api/interface/annotationinterface/polygonannotationoptions.html
---

# PolygonAnnotationOptions

## Syntax

```typescript
interface PolygonAnnotationOptions {
    points?: Point[];
    borderWidth?: number;
    borderColor?: string;
    background?: string;
    opacity?: number;
    lineDash?: number[];
    flags?: Flags;
}
```

## Attributes

### points

The points of the polygon annotation to draw. Please refer to [`Point`]({{ site.api }}interface/annotationinterface/point.html).

Default value: `[{x: 60, y: 10}, {x: 10, y: 55}, {x: 30, y: 110}, {x: 90, y: 110}, {x: 110, y: 55}]`

![Polygon Location](/assets/imgs/polygonlocation.png)

**Remark**

The number of elements in the array must be greater than or equal to two.

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

### background

The backgroud style of annotation.

Default value: `''`, it means no fill.

**Example**

```typescript
background: "rgb(255,255,255)", 
```

![Polygon BorderStyle](/assets/imgs/polygonborderstyle.png)

**Remark**

Supported string value of `borderColor` and `background`: 
- Named color, for example, `red`, `green`, etc.
- HEX(`#RRGGBB`), for example, `#ff0000`, `#008000`, etc.
- RGB(`rgb(red, green, blue)`), for example, `rgb(255, 0, 0)`, `rgb(0, 128, 0)`, etc.
- HSL(`hsl(Hue, Saturation, Lightness)`), for example, `hsl(0, 100%, 50%)`, `hsl(120, 100%, 25%)` ,etc.

If set to `''`, it means no fill.

### opacity

The opacity of the whole annotation. The value range is [0,1], value which is greater than 1 will default to 1. 

Default value: 1

### lineDash

The style of polygon annotation border. The unit is point.

Default value: `[0, 0]`

**Example**

```typescript
lineDash: [10, 10], 
```

<!--
### author

The author of annotation.

Default value: `''`

### subject

The subject of annotation.

Default value: `''`  -->

### flags

The flags of annotation. 

Please refer to [`Flags`]({{ site.api }}interface/annotationinterface/flags.html).

## Related

- [`Polygon()`]({{ site.api }}class/annotation/polygon.html#polygon)
- [`getOptions()`]({{ site.api }}class/annotation/polygon.html#getoptions) under `Polygon` class
- [`updateOptions()`]({{ site.api }}class/annotation/polygon.html#updateoptions) under `Polygon` class