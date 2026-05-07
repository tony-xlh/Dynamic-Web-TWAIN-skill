---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface SavePdfSettings
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface SavePdfSettings
breadcrumbText: Interface SavePdfSettings
description: Dynamsoft Document Viewer Documentation API Reference Interface SavePdfSettings Page
permalink: /api/interface/idocument/savepdfsettings.html
---

# SavePdfSettings

## Syntax

```typescript
interface SavePdfSettings {
    author?: string;
    compression?: EnumPDFCompressionType;
    pageType?: EnumPDFPageType; 
    creator?: string;
    creationDate?: string;
    keyWords?: string;
    modifiedDate?: string;
    producer?: string;
    subject?: string;
    title?: string;
    version?: string;
    quality?: number;
    password?: string;
    saveAnnotation?: SaveAnnotation;
    imageScaleFactor?: number;
}
```

## Attributes

### author

Specify the author.

### compression

Specify the pdf compression type. Please refer to [`EnumPdfCompressionType`]({{ site.api }}enumeration-type/enumpdfcompressiontype.html).

Default value: `PDF_AUTO`

### pageType

Specify the pdf page type. Please refer to [`EnumPdfPageType`]({{ site.api }}enumeration-type/enumpdfpagetype.html).

Default value: `PAGE_DEFAULT`

### creator

Specify the creator.

### creationDate

Specify the creation date.

Please note that the parameter should be in the format `D:YYYYMMDDHHmmSSOHH'mm'`, such as `D:20230101085959-08'00'`. It also supports the older format `D:YYYYMMDDHHmmSS`, like `D:20230101085959`; in this case, the system will automatically add the corresponding time zone information, for example, `D:20230101085959-08'00'`.

### keyWords

Specify the keywords.

### modifiedDate

Specify the modified date.

Please note that the parameter should be in the format `D:YYYYMMDDHHmmSSOHH'mm'`, such as `D:20230101085959-08'00'`. It also supports the older format `D:YYYYMMDDHHmmSS`, like `D:20230101085959`; in this case, the system will automatically add the corresponding time zone information, for example, `D:20230101085959-08'00'`.

### producer

Specify the producer.

### subject

Specify the subject.

### title

Specify the title.

### version

Specify the PDF version. For example, 1.5. The allowed values are 1.1 ~ 1.7.

If the [`compression`] is set to `PDF_JBig2`, the lowest version is 1.4.

If the [`compression`] is set to `PDF_JP2000`, the lowest version is 1.5

### quality

Specify the quality of the images in the file.

The value range is [0, 100], default value is 80.

Only takes effect when the [`compression`](#compression) is set to `PDF_JPEG` or `PDF_JP2000`.

### password

Specify the saved PDF owner password. Default value: `''`.

Maximum of 32 characters.

### saveAnnotation

Specify how to save annotation(s) in pdf file. Default value: `none`.

A `SaveAnnotation` can be one of four types.

```typescript
type SaveAnnotation = "none" | "image" | "annotation" | "flatten";
```
- `none`: not saving annotations. 

- `image`: saving annotations as a part of image. 

- `annotation`: saving annotations as pdf annotations.

- `flatten`: saving annotations as page content.

### imageScaleFactor

Specify the scale factor of the images in the file.

The value ranges from greater than 0 to less than or equal to 1.

Default is 1.

## Related

- [`saveToPdf()`]({{ site.api }}interface/idocument/index.html#savetopdf)