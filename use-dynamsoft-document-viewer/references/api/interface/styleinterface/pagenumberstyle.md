---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface PageNumberStyle
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface PageNumberStyle
breadcrumbText: Interface PageNumberStyle
description: Dynamsoft Document Viewer Documentation API Reference Interface PageNumberStyle Page
permalink: /api/interface/styleinterface/pagenumberstyle.html
---

# PageNumberStyle

## Syntax

```typescript
interface PageNumberStyle {
    visibility?: string; 
    onPage?: boolean;
    width?: string; 
    height?: string;
    border?: string; 
    borderRadius?: string;
    background?: string;
    opacity?: number;
    color?: string;
    fontSize?: string;
    fontFamily?: string; 
    left?: string;
    top?: string; 
    right?: string; 
    bottom?: string; 
    translateX?: string; 
    translateY?: string;
}
```

## Attributes

### visibility

Specify whether to show the page number. 

Supported value: `hidden`, `visible`

### onPage

Specify whether the page number is on page or not.

### width

The width of page number. Supports unit `px` or `%`, for example, `"10px"` or `"10%"`.

### height

The height of page number. Supports unit `px` or `%`, for example, `"10px"` or `"10%"`.

### border

The border style of page number. It contains three parts, borderWidth, borderStyle and borderColor.

Only takes effect when set borderWidth, borderStyle and borderColor at the same time.

borderWidth only supports `px` unit.

borderStyle only supports `dashed`, `solid`.

**Example**

```typescript
border: "2px dashed red", 
```

### borderRadius

The border radius of page number. Supports unit `px` or `%`, for example, `"10px"` or `"10%"`.

### background

The background style.

**Example**

```typescript
background: "rgba(255,255,255,0)", 
```

### opacity

The opacity of the whole page number. The value range is [0,1], value which is greater than 1 will default to 1.

### color

The color of page number font.

### fontSize

The size of page number font.

### fontFamily

The font-family of page number font.

![Page Number](/assets/imgs/pagenumber-1.png)


### left, top, right, bottom

Position the page number. Supports unit `px` or `%`, for example, `"10px"` or `"10%"`.

**Remark**

- To position a page number, one of `left` and `right` and one of `top` and `bottom` must be set, with the remaining positioning attributes should be set to empty strings. For example, 
    ```typescript
    left: "10%",
    top: "10%",
    right: "",
    bottom: "",
    ```
    OR
    ```typescript
    left: "",
    top: "",
    right: "10px",
    bottom: "10px",
    ```
    OR
    ```typescript
    left: "10px",
    top: "",
    right: "",
    bottom: "10px",
    ```
    OR
    ```typescript
    left: "",
    top: "10%",
    right: "10%",
    bottom: "",
    ```
- If both `left` and `right` are set, only `left` takes effect. If both `top` and `bottom` are set, only `top` takes effect.

### translateX

Reposition the page number horizontally. Supports unit `px` or `%`, for example, `"10px"` or `"10%"`.

| number in string                             | page number shifts along x-axis |
| -------------------------------------------- | ------------------------------- |
| positive, for example, `"10px"` or `"10%"`   | →                               |
| negative, for example, `"-10px"` or `"-10%"` | ←                               |

### translateY

Reposition the page number vertically. Supports unit `px` or `%`, for example, `"10px"` or `"10%"`.

| number in string                             | page number shifts along y-axis |
| -------------------------------------------- | ------------------------------- |
| positive, for example, `"10px"` or `"10%"`   | ↓                               |
| negative, for example, `"-10px"` or `"-10%"` | ↑                               |


![Position Page Number when onPage is true](/assets/imgs/positionpagenumber-1.png)

![Position Page Number when onPage is false](/assets/imgs/positionpagenumber-2.png)