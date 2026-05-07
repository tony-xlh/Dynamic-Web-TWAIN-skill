---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - ImageFilter Class
keywords: Documentation, Dynamsoft Document Viewer, API Reference, ImageFilter Class
breadcrumbText: ImageFilter Class
description: Dynamsoft Document Viewer Documentation API Reference ImageFilter Class Page
permalink: /api/class/advanced/imagefilter.html
---

# ImageFilter

`ImageFilter` implements [`IImageFilter`]({{ site.api }}interface/iimagefilter.html). 

This class is used to configure `Dynamsoft.DDV.Elements.Filter`. Please refer to [How to configure image filter]({{ site.features }}advanced/imagefilter.html).

The APIs for this class include:

 API Name            | Description                                             
---------------------|-----------------------------------------------------------
 [`constuctor() `](#constuctor)       | Constuctor of `ImageFilter` instance.
 [`defaultFilterType`](#defaultfiltertype)   | Configure the default image filter type.
 [`querySupported()`](#querysupported)    | Query supported image filter types and their label string, then create the completed Filter Element.
 [`applyFilter()`](#applyfilter)       | Apply the specified image filter type to image(s).
 [`destroy()`](#destroy)           | Destroy the instance.

## constuctor()

Constuctor of `ImageFilter` instance.

**Syntax**

```typescript
constuctor(image?: VImageData);
```

**Parameters**

`image`: The image which will be filtered. Please refer to [`VImageData`]({{ site.api }}interface/vimagedata.html).

## defaultFilterType

Configure the default image filter type.

```typescript
readonly defaultFilterType: string;
```

**Return Value**

The image filter type. Please refer to [`EnumImageFilterType`]({{ site.api }}enumeration-type/enumimagefiltertype.html).

## querySupported()

Query supported image filter types and their label string, then create the completed Filter Element.

**Syntax**

```typescript
querySupported(): ImageFilterItem[];
```
**Return Value**

The array of image filter method. Please refer to [`ImageFilterItem`]({{ site.api }}interface/imagefilteritem.html).

## applyFilter()

Apply the specified image filter type to image(s).

**Syntax**

```typescript
applyFilter(type: string): Promise<Blob>;
applyFilter(image: VImageData, type: string): Promise<Blob>;
```

**Parameters**

`type`: The image filter type. Please refer to [`EnumImageFilterType`]({{ site.api }}enumeration-type/enumimagefiltertype.html).
`image`: The image which will be filtered. Please refer to [`VImageData`]({{ site.api }}interface/vimagedata.html).

**Return Value**

A Promise object which will be resolved with `Blob` of the filtered image.

## destroy()

Destroy the instance.

**Syntax**

```typescript
destroy(): void;
```
