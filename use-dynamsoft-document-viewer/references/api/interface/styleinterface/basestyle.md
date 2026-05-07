---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface BaseStyle
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface BaseStyle
breadcrumbText: Interface BaseStyle
description: Dynamsoft Document Viewer Documentation API Reference Interface BaseStyle Page
permalink: /api/interface/styleinterface/basestyle.html
---

# BaseStyle

## Syntax

```typescript
interface BaseStyle {
    border?: string; 
    background?: string;
}
```

## Attributes

### border

The border style contains three parts, borderWidth, borderStyle and borderColor.

Only takes effect when set borderWidth, borderStyle and borderColor at the same time.

borderWidth only supports `px` unit.

borderStyle only supports `dashed`, `solid`.

**Example**

```typescript
border: "2px dashed red", 
```

### background

The background style.

**Example**

```typescript
background: "rgba(255,255,255,0)", 
```