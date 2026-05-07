---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface LineAnnotationOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface LineAnnotationOptions
breadcrumbText: Interface LineAnnotationOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface LineAnnotationOptions Page
permalink: /api/interface/annotationinterface/lineannotationoptions.html
---

# LineAnnotationOptions

## Syntax

```typescript
interface LineAnnotationOptions {
    startPoint?:Point;
    endPoint?: Point;
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

### startPoint

The start point of the line annotation to draw. Please refer to [`Point`]({{ site.api }}interface/annotationinterface/point.html).

Default value: `{x: 10, y: 10}`

### endPoint

The end point of the line annotation to draw. Please refer to [`Point`]({{ site.api }}interface/annotationinterface/point.html).

Default value: `{x: 110, y: 80}`

![Line Location](/assets/imgs/linelocation.png)

### lineEnding

The line ending style of the line annotation.

#### start

Specify the start point style of the line annotation. Please refer to [`EnumLineEnding`]({{ site.api }}enumeration-type/enumlineending.html).

Default value: `Dynamsoft.DDV.EnumLineEnding.NONE`

#### end

Specify the end point style of the line annotation. Please refer to [`EnumLineEnding`]({{ site.api }}enumeration-type/enumlineending.html).

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

![Line BorderStyle](/assets/imgs/lineborderstyle.png)

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

The style of line annotation border. The unit is point.

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

- [`Line()`]({{ site.api }}class/annotation/line.html#line)
- [`getOptions()`]({{ site.api }}class/annotation/line.html#getoptions) under `Line` class
- [`updateOptions()`]({{ site.api }}class/annotation/line.html#updateoptions) under `Line` class