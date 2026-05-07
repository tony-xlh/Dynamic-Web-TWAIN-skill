---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface InkAnnotationOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface InkAnnotationOptions
breadcrumbText: Interface InkAnnotationOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface InkAnnotationOptions Page
permalink: /api/interface/annotationinterface/inkannotationoptions.html
---

# InkAnnotationOptions

## Syntax

```typescript
interface InkAnnotationOptions {
    points?: Point[][];
    borderWidth?: number;
    borderColor?: string;
    opacity?: number;
    flags?: Flags;
    rotation?: number;
}
```

### points

The points of the ink annotation to draw. An ink annotation can include multiple strokes. Please refer to [`Point`]({{ site.api }}interface/annotationinterface/point.html).

Default value: `[[{ x: 10, y: 10 }, { x: 110, y: 80 }], [{ x: 110, y: 10 }, { x: 10, y: 80 }]]`

### borderWidth

The border width of annotation. The unit is point. 

Default value: 1

### borderColor

The border color of annotation.

Default value: `rgb(0,0,0)` 

**Remark**

Supported string value of `borderColor`: 
- Named color, for example, `red`, `green`, etc.
- HEX(`#RRGGBB`), for example, `#ff0000`, `#008000`, etc.
- RGB(`rgb(red, green, blue)`), for example, `rgb(255, 0, 0)`, `rgb(0, 128, 0)`, etc.
- HSL(`hsl(Hue, Saturation, Lightness)`), for example, `hsl(0, 100%, 50%)`, `hsl(120, 100%, 25%)` ,etc.

### opacity

The opacity of the whole annotation. The value range is [0,1], value which is greater than 1 will default to 1. 

Default value: 1

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

- [`Ink()`]({{ site.api }}class/annotation/ink.html#ink)
- [`getOptions()`]({{ site.api }}class/annotation/ink.html#getoptions) under `Ink` class
- [`updateOptions()`]({{ site.api }}class/annotation/ink.html#updateoptions) under `Ink` class