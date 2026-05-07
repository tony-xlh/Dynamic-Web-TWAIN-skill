---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface CanvasStyle
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface CanvasStyle
breadcrumbText: Interface CanvasStyle
description: Dynamsoft Document Viewer Documentation API Reference Interface CanvasStyle Page
permalink: /api/interface/styleinterface/canvasstyle.html
---

# CanvasStyle

## Syntax

```typescript
interface CanvasStyle {
    border?: string;
    background?: string;
    cursor?: Cursor;
}
```

## Attributes

### border

The border style of canvas.

The border style contains three parts, borderWidth, borderStyle and borderColor.

Only takes effect when set borderWidth, borderStyle and borderColor at the same time.

borderWidth only supports `px` unit.

borderStyle only supports `dashed`, `solid`.

**Example**

```typescript
border: "2px dashed red", 
```

### background

The background style of canvas.

**Example**

```typescript
background: "rgba(255,255,255,0)", 
```

### cursor

The cursor style.

A `Cursor` can be one of types below. For detailed info, please refer to [CSS-cursor](https://developer.mozilla.org/en-US/docs/Web/CSS/cursor).

```typescript
type Cursor = "auto" | "default" | "none" | "context-menu" | "help" | "pointer" | "progress" | "wait" | "cell" | "crosshair" | "text" | "vertical-text" | "alias" | "copy" | "move" | "no-drop" | "not-allowed" | "e-resize" | "n-resize" | "ne-resize" | "nw-resize" | "s-resize" | "se-resize" | "sw-resize" | "w-resize" | "ns-resize" | "ew-resize" | "nesw-resize" | "col-resize" | "nwse-resize" | "row-resize" | "all-scroll" | "zoom-in" | "zoom-out" | "grab" | "grabbing";
```