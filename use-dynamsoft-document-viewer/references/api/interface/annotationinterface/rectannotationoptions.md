---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface RectAnnotationOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface RectAnnotationOptions
breadcrumbText: Interface RectAnnotationOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface RectAnnotationOptions Page
permalink: /api/interface/annotationinterface/rectannotationoptions.html
---

# RectAnnotationOptions

## Syntax

```typescript
interface RectAnnotationOptions {
    x?: number;
    y?: number;
    width?: number;
    height?: number; 
    borderWidth?: number;
    borderColor?: string;
    background?: string;
    opacity?: number; 
    lineDash?: number[];
    flags?: Flags;
    rotation?: number;
}
```

## Attributes

### x

The x-coordinate of the upper-left corner of the rectangle annotation to draw. The unit is point.

Default value: 10

### y

The y-coordinate of the upper-left corner of the rectangle annotation to draw. The unit is point.

Default value: 10

### width

The width of the rectangle annotation to draw. The unit is point.

Default value: 100

### height

The height of the rectangle annotation to draw. The unit is point.

Default value: 100

![Rectangle Location](/assets/imgs/rectlocation.png)

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

![Rectangle BorderStyle](/assets/imgs/rectborderstyle.png)

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

The style of rectangle annotation border. The unit is point.

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

### rotation

The rotation angle of annotation.

Default value: 0

**Remark**

- Positive value means clockwise rotation, negative value means counterclockwise rotation.

## Related

- [`Rectangle()`]({{ site.api }}class/annotation/rectangle.html#rectangle)
- [`getOptions()`]({{ site.api }}class/annotation/rectangle.html#getoptions) under `Rectangle` class
- [`updateOptions()`]({{ site.api }}class/annotation/rectangle.html#updateoptions) under `Rectangle` class