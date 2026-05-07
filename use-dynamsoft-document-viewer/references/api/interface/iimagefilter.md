---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface IImageFilter
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface IImageFilter
breadcrumbText: Interface IImageFilter
description: Dynamsoft Document Viewer Documentation API Reference Interface IImageFilter Page
permalink: /api/interface/iimagefilter.html
---


# IImageFilter

It is implemented by [`ImageFilter`]({{ site.api }}class/advanced/imagefilter.html) Class.

## Members

### querySupported()

**Syntax**

```typescript
querySupported(): ImageFilterItem[];
```

**Return Value**

Please refer to [`ImageFilterItem`]({{ site.api }}interface/imagefilteritem.html).

### `get` defaultFilterType()

**Syntax**

```typescript
get defaultFilterType(): EnumImageFilterType;
```

**Return Value**

Please refer to [`EnumImageFilterType`]({{ site.api }}enumeration-type/enumimagefiltertype.html).

### applyFilter()

**Syntax**

```typescript
applyFilter(image: VImageData, type: EnumImageFilterType): Promise<Blob>;
```

**Parameters**

`image`: The image which will be filtered. Please refer to [`VImageData`]({{ site.api }}interface/vimagedata.html).
`type`: The image filter type. Please refer to [`EnumImageFilterType`]({{ site.api }}enumeration-type/enumimagefiltertype.html).

**Return Value**

A Promise object which will be resolved with `Blob` of the filtered image.

### destroy()

**Syntax**

```typescript
destroy(): void;
```
