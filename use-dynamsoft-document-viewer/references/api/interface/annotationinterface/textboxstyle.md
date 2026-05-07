---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface TextBoxStyle
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface TextBoxStyle
breadcrumbText: Interface TextBoxStyle
description: Dynamsoft Document Viewer Documentation API Reference Interface TextBoxStyle Page
permalink: /api/interface/annotationinterface/textboxstyle.html
---

# TextBoxStyle

## Syntax

```typescript
interface TextBoxStyle {
    borderWidth?: number;
    borderColor?: string;
    background?: string;
    opacity?: number;
    lineDash?: number[];
    textAlign?: string; 
    textContent?: TextContent;
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

### background

The backgroud style of annotation.

Default value: `''`, it means no fill.

**Example**

```typescript
background: "rgb(255,255,255)", 
```

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

The style of annotation border. The unit is point.

Default value: `[0, 0]`

**Example**

```typescript
lineDash: [10, 10], 
```

### textAlign

The text alignment.

Supported values: `left`, `right`, `center`, `justify`

Default value: `left`

### textContent

The text content of the text box/text typewriter annotation. Please refer to [`TextContent`]({{ site.api }}interface/annotationinterface/textcontent.html).

## Related

- [`EditViewerConstructorOptions`]({{ site.api }}interface/editviewerconstructoroptions.html)