---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface PolylineAnnotationOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface PolylineAnnotationOptions
breadcrumbText: Interface PolylineAnnotationOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface PolylineAnnotationOptions Page
permalink: /api/interface/annotationinterface/polylineannotationoptions.html
---

# PolylineAnnotationOptions

## Syntax

```typescript
interface PolylineAnnotationOptions {
    points?: Point[];
    lineEnding?: {
        start?: EnumLineEnding;
        end?: EnumLineEnding;
    };
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

The points of the polyline annotation to draw. Please refer to [`Point`]({{ site.api }}interface/annotationinterface/point.html).

Default value: `[{x: 10, y: 40}, {x: 50, y: 80}, {x: 110, y: 10}]`

![Polyline Location](/assets/imgs/polylinelocation.png)

**Remark**

The number of elements in the array must be greater than or equal to two.

### lineEnding

The line ending style of the polyline annotation.

#### start

Specify the start point style of the polyline annotation. Please refer to [`EnumLineEnding`]({{ site.api }}enumeration-type/enumlineending.html).

Default value: `Dynamsoft.DDV.EnumLineEnding.NONE`

#### end

Specify the end point style of the polyline annotation. Please refer to [`EnumLineEnding`]({{ site.api }}enumeration-type/enumlineending.html).

Default value: `Dynamsoft.DDV.EnumLineEnding.NONE`

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

![Polyine BorderStyle](/assets/imgs/polylineborderstyle.png)

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

The style of polyline annotation border. The unit is point.

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

- [`Polyline()`]({{ site.api }}class/annotation/polyline.html#polyline)
- [`getOptions()`]({{ site.api }}class/annotation/polyline.html#getoptions) under `Polyline` class
- [`updateOptions()`]({{ site.api }}class/annotation/polyline.html#updateoptions) under `Polyline` class