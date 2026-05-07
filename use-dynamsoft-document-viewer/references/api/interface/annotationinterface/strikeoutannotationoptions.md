---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface StrikeoutAnnotationOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface StrikeoutAnnotationOptions
breadcrumbText: Interface StrikeoutAnnotationOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface StrikeoutAnnotationOptions Page
---

# StrikeoutAnnotationOptions

## Syntax

```typescript
interface StrikeoutAnnotationOptions {
    borderColor?: string;
    rects: RectXY[];
    opacity?: number;
    flags?: Flags;
}
```

## Attributes

### borderColor

The border color of annotation.

Default value: `#F01314` 

**Example**

```typescript
borderColor: "rgb(255,0,0)", 
```

**Remark**

Supported string value of `borderColor`: 
- Named color, for example, `red`, `green`, etc.
- HEX(`#RRGGBB`), for example, `#ff0000`, `#008000`, etc.
- RGB(`rgb(red, green, blue)`), for example, `rgb(255, 0, 0)`, `rgb(0, 128, 0)`, etc.
- HSL(`hsl(Hue, Saturation, Lightness)`), for example, `hsl(0, 100%, 50%)`, `hsl(120, 100%, 25%)` ,etc.

### rects

An array of rectangles marking where to put the annotations.

Please refer to [`RectXY`](/api/interface/rectxy.md).

### opacity

The opacity of the whole annotation. The value range is [0,1], value which is greater than 1 will default to 1. 

Default value: 1

### flags

The flags of annotation. 

Please refer to [`Flags`]({{ site.api }}interface/annotationinterface/flags.html).

## Related

- [`getOptions()`](/api/class/annotation/strikeout.md#getoptions) under `Strikeout` class
- [`updateOptions()`](/api/class/annotation/strikeout.md#updateoptions) under `Strikeout` class
