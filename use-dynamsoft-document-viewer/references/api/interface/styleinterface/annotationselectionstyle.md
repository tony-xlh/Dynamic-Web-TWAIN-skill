---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface AnnotationSelectionStyle
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface AnnotationSelectionStyle
breadcrumbText: Interface AnnotationSelectionStyle
description: Dynamsoft Document Viewer Documentation API Reference Interface AnnotationSelectionStyle Page
permalink: /api/interface/styleinterface/annotationselectionstyle.html
---

# AnnotationSelectionStyle

## Syntax

```typescript
interface AnnotationSelectionStyle {
    border?: string; 
    background?: string; 
    ctrlBorderRadius?: string; 
    ctrlBorder?: string; 
    ctrlWidth?: string; 
    ctrlHeight?: string; 
    ctrlBackground?: string; 
}
```

## Attributes

### border

The border style of selection.

The border style contains three parts, borderWidth, borderStyle and borderColor.

Only takes effect when set borderWidth, borderStyle and borderColor at the same time.

borderWidth only supports `px` unit.

borderStyle only supports `dashed`, `solid`.

**Example**

```typescript
border: "2px dashed red", 
```

### background

The background style of selection.

**Example**

```typescript
background: "rgba(220, 220, 220, 0.5)", 
```

### ctrlBorderRadius

The border radius of Control Points. Supports `pt` and `%`.

### ctrlBorder

The border style of Control Points.

```typescript
ctrlBorder: "1pt solid green", 
```

### ctrlWidth

The width of Control Points. Only supports `px` unit.

### ctrlHeight

The height of Control Points. Only supports `px` unit.

### ctrlBackground

The backgroud style of Control Points.