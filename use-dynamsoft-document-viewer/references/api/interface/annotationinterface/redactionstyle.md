---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface RedactionStyle
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface RedactionStyle
breadcrumbText: Interface RedactionStyle
description: Dynamsoft Document Viewer Documentation API Reference Interface RedactionStyle Page
---

# RedactionStyle

## Syntax

```typescript
interface RedactionStyle {
    background?: string;
    borderColor?: string;
    overlayBackground?: string;
    overlayText?: {
        text: string;
        color?: string;
        textAlign?: "left" | "center" | "right";
        fontSize?: number;
        fontFamily?: string;
        repeatText?: boolean;
        autoFontSize?: boolean;
    };
}
```

## Attributes

### background

The background style of annotation.

Default value: `''`, it means no fill.

**Example**

```typescript
background: "rgb(255,255,255)", 
```

### borderColor

The border color of annotation.

Default value: `rgb(255,0,0)` 

**Example**

```typescript
borderColor: "rgb(255,0,0)", 
```

### overlayBackground

The background of the annotation after being applied.

Default value: `rgb(0,0,0)`

### overlayText

The text to display after being applied. It is an object for configuration. The following is the default options.

```ts
{
    text: "",                // text
    color: "rgb(255,0,0)", // text color
    textAlign: "left",       // text alignment: left, center, right
    fontSize: 16,            // font size
    fontFamily: "Helvetica", // font family name
    repeatText: false,       // repeat the text to fill the marked area
    autoFontSize: false,     // fit the text to the marked area
}
```

### opacity

The opacity of the whole annotation. The value range is [0,1], value which is greater than 1 will default to 1. 

Default value: 1
