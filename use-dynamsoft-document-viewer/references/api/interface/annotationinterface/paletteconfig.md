---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface PaletteConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface PaletteConfig
breadcrumbText: Interface PaletteConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface PaletteConfig Page
permalink: /api/interface/annotationinterface/paletteconfig.html
---

# PaletteConfig

## Syntax

```typescript
interface PaletteConfig {
    enabled?: boolean;
    id?: string;
    className?: string;
    style?: cssstyleDeclaration;
    colorList?: string[];
    labels?: {
        text? : string;
        stroke? : string;
        fill?: string;
        opacity?: string;
        style?: string;
        standardBusiness?: string;
    }
}
```

## Attributes

### enabled

Whether or not the toolbar is enabled.

Default value: `true`

### id

The id of Dom Element. If it is not specified, a random string will be generated.

### className

The className of CSS.

### style

The style which will cover CSS.

### colorList

The color list in palette. Supported string value: 
- Named color, for example, `red`, `green`, etc.
- HEX(`#RRGGBB`), for example, `#ff0000`, `#008000`, etc.
- RGB(`rgb(red, green, blue)`), for example, `rgb(255, 0, 0)`, `rgb(0, 128, 0)`, etc.
- HSL(`hsl(Hue, Saturation, Lightness)`), for example, `hsl(0, 100%, 50%)`, `hsl(120, 100%, 25%)` ,etc.

Default value: `["#F01314", "#FD7C10", "#FFEE5F", "#07C37F", "#0E68F5", "#9D3BFE", "#000000","#FF9494", "#87440C", "#B7A514", "#046743", "#50C9FF", "#EBA3ED", "#FFFFFF","#CECECE"]`

![ColorList](/assets/imgs/colorlist.png)


**Example**

```typescript
colorList: ["red", "green", "#0000ff", "#ffff00" , "rgb(0, 0, 0)", "rgb(128, 128, 128)", "hsl(0, 0%, 100%)", "hsl(350, 100%, 88%)"],
```

**Remarks**

- The palette's UI defaults to presenting 27 color circles for display. Consequently, only the first 27 values within the `colorList` array can be utilized and will appear in the UI in a sequential manner. The remaining values in the array will be disregarded.
- If the number of values in the `colorList` array are less than 27, after applying the values configured in the array, the remaining color circles will be replaced by custom color circles. 
- Custom color circles can be set to a specified color by clicking on the circle via the user interface. Similarly, for color circles, the color can be modified by double-clicking on them through the user interface.

### displayText

The display text in palette.

#### text

Default value: `Text`

#### stroke

Default value: `Stroke`

#### fill

Default value: `Fill`

#### opacity

Default value: `Opacity`

#### style

Default value: `Style`

#### standardBusiness

Default value: `StandardBusiness`

## Related

- [`EditViewerConstructorOptions`]({{ site.api }}interface/editviewerconstructoroptions.html)
