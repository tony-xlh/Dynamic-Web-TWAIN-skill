---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface CheckboxStyle
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface CheckboxStyle
breadcrumbText: Interface CheckboxStyle
description: Dynamsoft Document Viewer Documentation API Reference Interface CheckboxStyle Page
permalink: /api/interface/styleinterface/checkboxstyle.html
---

# CheckboxStyle

## Syntax

```typescript
interface CheckboxStyle {
    visibility?: string; 
    width?: string; 
    height?: string; 
    border?: string; 
    borderRadius?: string; 
    background?: string;
    opacity?: number;
    checkMarkColor?: string;
    checkMarkLineWidth?: string; 
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

Specify whether to show the checkbox. 

Supported value: `hidden`, `visible`

### width

The width of checkbox. Supports unit `px` or `%`, for example, `"10px"` or `"10%"`.

### height

The height of checkbox. Supports unit `px` or `%`, for example, `"10px"` or `"10%"`.

### border

The border style of checkbox. It contains three parts, borderWidth, borderStyle and borderColor.

Only takes effect when set borderWidth, borderStyle and borderColor at the same time.

borderWidth only supports `px` unit.

borderStyle only supports `dashed`, `solid`.

**Example**

```typescript
border: "2px dashed red", 
```

### borderRadius

The border radius of checkbox. Supports unit `px` or `%`, for example, `"10px"` or `"10%"`.

### background

The background style.

**Example**

```typescript
background: "rgba(255,255,255,0)", 
```

### opacity

The opacity of the whole checkbox. The value range is [0,1], value which is greater than 1 will default to 1.

### checkMarkColor

The color of check mark.

### checkMarkLineWidth

The width of check mark. For example, `"1px"`.

![Checkbox](/assets/imgs/checkbox.png)

### left, top, right, bottom

Position the checkbox. Supports unit `px` or `%`, for example, `"10px"` or `"10%"`.

**Remark**

- To position a checkbox, one of `left` and `right` and one of `top` and `bottom` must be set, with the remaining positioning attributes should be set to empty strings. For example, 
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

Reposition the checkbox horizontally. Supports unit `px` or `%`, for example, `"10px"` or `"10%"`.

| number in string                             | checkbox shifts along x-axis    |
| -------------------------------------------- | ------------------------------- |
| positive, for example, `"10px"` or `"10%"`   | →                               |
| negative, for example, `"-10px"` or `"-10%"` | ←                               |

### translateY

Reposition the checkbox vertically. Supports unit `px` or `%`, for example, `"10px"` or `"10%"`.

| number in string                             | checkbox shifts along y-axis    |
| -------------------------------------------- | ------------------------------- |
| positive, for example, `"10px"` or `"10%"`   | ↓                               |
| negative, for example, `"-10px"` or `"-10%"` | ↑                               |

![Position Checkbox](/assets/imgs/positioncheckbox.png)