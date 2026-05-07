---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface StampAnnotationOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface StampAnnotationOptions
breadcrumbText: Interface StampAnnotationOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface StampAnnotationOptions Page
permalink: /api/interface/annotationinterface/stampannotationoptions.html
---

# StampAnnotationOptions

## Syntax

```typescript
interface StampAnnotationOptions{
    x?: number;
    y?: number;
    width?: number;
    height?: number; 
    stamp?: EnumStampIcon | string | Blob; 
    opacity?: number; 
    flags?: Flags;
    rotation?: number;
}
```

## Attributes

### x

The x-coordinate of the upper-left corner of the stamp annotation to draw. The unit is point.

Default value: 10

### y

The y-coordinate of the upper-left corner of the stamp annotation to draw. The unit is point.

Default value: 10

### width

The width of the stamp annotation to draw. The unit is point.

Default value: `undefined`, means the original width of the standard bussiness stamp or the custom image.

### height

The height of the stamp annotation to draw. The unit is point.

Default value: `undefined`, means the original height of the standard bussiness stamp or the custom image.

![Stamp Location](/assets/imgs/stamplocation.png)

### stamp

Specify the standard business stamp or the blob of a custom image to be drawn. Please refer to [`EnumStampIcon`]({{ site.api }}enumeration-type/enumstampicon.html) for standard business stamp.

Default value: `Dynamsoft.DDV.EnumStampIcon.DRAFT`

If set to `blob`, the custom image will be added as the stamp.

Supported image formats: PNG, JPEG

The value of type `string` is readonly and only suitable for incomplete annotation.

### opacity

The opacity of the whole annotation. The value range is [0,1], value which is greater than 1 will default to 1. 

Default value: 1

<!--
### author

The author of annotation.

Default value: `''`

### subject

The subject of annotation.

Default value: `''` -->

### flags

The flags of annotation. 

Please refer to [`Flags`]({{ site.api }}interface/annotationinterface/flags.html).

### rotation

The rotation angle of annotation.

Default value: 0

**Remark**

- Positive value means clockwise rotation, negative value means counterclockwise rotation.

## Related

- [`Stamp()`]({{ site.api }}class/annotation/stamp.html#stamp)
- [`getOptions()`]({{ site.api }}class/annotation/stamp.html#getoptions) under `Stamp` class
- [`updateOptions()`]({{ site.api }}class/annotation/stamp.html#updateoptions) under `Stamp` class