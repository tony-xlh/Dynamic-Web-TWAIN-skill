---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Features - Annotation
keywords: Documentation, Dynamsoft Document Viewer, Features, Annotation
breadcrumbText: Edit Viewer
description: Dynamsoft Document Viewer Documentation Features, Annotation
permalink: /features/viewers/annotation.html
---

# Annotation

Starting from DDV 2.0, Annotation functionality is supported. This guide introduces some of the key Annotation features. The following functionalities can all be achieved through bulit-in Elements which are related to annotation functionality, this guide only focuses on programming methods.

It is important to note that annotations on the page can be displayed in the UI of either the EditViewer or the BrowseViewer, but they can only be processed through the UI in the EditViewer. Additionally, [built-in Elements related to annotation functionality]({{ site.ui }}default_elements.html#edit-viewer) can only be configured within the UiConfig of the EditViewer.

## Supported annotation types

Up to now, the annotation types supported by DDV are as follows:

- [Rectangle]({{ site.api }}class/annotation/rectangle.html)
- [Ellipse]({{ site.api }}class/annotation/ellipse.html)
- [Polygon]({{ site.api }}class/annotation/polygon.html)
- [Polyline]({{ site.api }}class/annotation/polyline.html)
- [Line]({{ site.api }}class/annotation/line.html)
- [Ink]({{ site.api }}class/annotation/ink.html)
- [TextBox]({{ site.api }}class/annotation/textbox.html)
- [TextTypewriter]({{ site.api }}class/annotation/texttypewriter.html)
- [Stamp]({{ site.api }}class/annotation/stamp.html)

## Create a specified type annotation instance

To add an annotation to the page, first of all, you need to create an annotation instance. Take the rectangle annotation as an example,

```typescript
// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const pageUid = editViewer.indexToUid(0);
const rect = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "rectangle"); // Create a default Rectangle annotation instance.
```

The following properties of the annotation can be accessed from the created instance.

- Annotation Uid
    
    Each annotation possesses a unique annotation uid. 
    
    ```typescript
    const annotUid = rect.uid;
    ```

    if the annotation is deleted, the `uid` will return `''`.

- Page uid where the annotation is located

    ```typescript
    const annotPageUid = rect.pageUid;
    ```

    if the annotation is deleted, the `pageUid` will return `''`.
{% comment %}

- Axis-aligned bounding box (AABB)

    ```typescript
    const annotAabb = rect.aabb;
    ```
{% endcomment %}

- Creation date & Modification date

    ```typescript
    const creationDate = rect.creationDate; //D:YYYYMMDDHHmmSSOHH'mm'
    const modificationDate = rect.modificationDate; //D:YYYYMMDDHHmmSSOHH'mm'
    ```

    if the annotation is deleted, the `creationDate` will return `''`.

    If the annotation is not be modified after creating, `modificationDate` equals to `creationDate`.

## Modify the annotation options while creating

If no specific options are passed during the creation of the annotation instance, the generated annotation will have default options.

If you wish to create a custom-configured annotation, you can pass in the specified configuration during creation.

For example, to create a rectangle annotation whose border color is red and background is green.

```typescript
const rectOptions = {
    borderColor: "red",
    background: "green",
};

// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const pageUid = editViewer.indexToUid(0);

const rect = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "rectangle", rectOptions);
```

## Modify the annotation options dynamically after creating

After creating the annotation, if you want to dynamically modify its configuration, you can use `updateOptions()` method.

For example, to modify an existing rectangle annotation. 

```typescript
const newRectOptions = {
    borderWidth: 2.66,
};

rect.updateOptions(newRectOptions);
```

Even after the annotation has been created by [`createAnnotation()`]({{ site.api }}class/annotationmanager.html#createAnnotation), updating the options will lead to instant changes in the displayed annotation on the page.

### Create an annotation instance after image cropping

After cropping, if no specific options are passed during the creation of the annotation instance, the generated annotation will use default options, which might result in it being invisible.

If you want the annotation to be visible, you can pass specific configurations during its creation.

For example, after cropping an image, if you wish to create a rectangle annotation at position (10, 10) within the visible area.

```typescript
const pageData = await editViewer.currentDocument.getPageData(editViewer.getCurrentPageUid());

const rectOptions = {
    x: pageData.cropBox.left + 10,
    y: pageData.cropBox.top + 10,
};

// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const pageUid = editViewer.indexToUid(0);

const rect = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "rectangle", rectOptions);
```

## More features

### Add image to the page by using Stamp Annotation

Observing the structure of [`StampAnnotationOptions`]({{ site.api }}interface/annotationinterface/stampannotationoptions.html), the data type of stamp is `EnumStampIcon` or `Blob`. When stamp is set to `EnumStampIcon`, it indicates that the generated annotation will be displayed as a standard business stamp icon, with the default value being `DRAFT`. When stamp is set to a Blob, such as the blob of a custom image, it means the annotation will be displayed as an image.


The supported types of standard business stamps are as follows:

| EnumStampIcon | Corresponding stamp |
| ------------- | ------------------- |
| REJECTED      |                     |
| ACCEPTED      |                     |
| INITAL_HERE   |                     |
| SIGN_HERE     |                     |
| WITNESS       |                     |
| APPROVED      |                     |
| NOT_APPROVED  |                     |
| DRAFT         |                     |
| FINAL         |                     |
| COMPLETED     |                     |
| CONFIDENTIAL  |                     |
| VOID          |                     |


### Configure the styling for the part content of text within TextBox annotation or TextTypewriter annotation

The `textContents` attribute in the [`TextBoxAnnotationOptions`]({{ site.api }}interface/annotationinterface/textboxannotationoptions.html) and [`TextTypewriterAnnotationOptions`]({{ site.api }}interface/annotationinterface/texttypewriterannotationoptions.html) accepts an array of [`TextContent`]({{ site.api }}interface/annotationinterface/textcontent.html), which means that even within the same text annotation, you can configure specified text content with different styles.

For example,

```typescript
const testTextContents = [
    {
        content: "Dynamsoft Document Viewer ",
        color: "red",
    },
    {
        content: "Annotation feature",
        color: "green",
        underline: true,
    }
];

const textBoxAnnotationOptions = {
    textContents: testTextContents,
};

// Given that editViewer is an existing instance of EditViewer and a document is currently open.
const pageUid = editViewer.indexToUid(0);

const textBox = Dynamsoft.DDV.annotationManager.createAnnotation(pageUid, "textBox", textBoxAnnotationOptions);
```

## Add the created annotation to the specified page

Please refer to [Annoatation management]({{ site.features }}datamanagement/annotmanagement.html).