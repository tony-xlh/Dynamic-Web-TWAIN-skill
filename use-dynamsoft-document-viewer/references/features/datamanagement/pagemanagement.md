---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Features - Page Management
keywords: Documentation, Dynamsoft Document Viewer, Features, Page Management
breadcrumbText: Page Management
description: Dynamsoft Document Viewer Documentation Features, Page Management
permalink: /features/datamanagement/pagemanagement.html
---

# Page Management

DDV is using [`Interface IDocument`]({{ site.api }}interface/idocument/index.html) to manage the page data. 

## Load pages

[`loadSource()`]({{ site.api }}interface/idocument/index.html#loadsource) is used to load file(s) into the document. 

**Use case**

- Load an image file in order

    ```typescript
    // Create a document
    const docManager = Dynamsoft.DDV.documentManager;
    const firstDoc = docManager.createDocument({
        name: "first_document",
        author: "DDV",
        creationDate: "D:20230101085959-08'00'",
    });

    //Load a file
    var blob = /*Sample image blob*/;
    await firstDoc.loadSource(blob);
    ```

- Load an image file and insert it into the specified order if there are pages in the document.

    ```typescript
    var blob = /*Sample image blob*/;

    // Load and insert to the beginning of the document
    await firstDoc.loadSource(blob, 0);
    ```

- Load multiple files at one time

    ```typescript
    var blobs = /*Sample image blob array*/;
    await firstDoc.loadSource(blobs);
    ```

- Load an image file with [`ExtraPageData`]({{ site.api }}interface/idocument/extrapagedata.html)

    ```typescript
    const extraData = {
        index: 0, // Extra data for the first page
        rotation: 90,
    };

    const testSource = {
        fileData: /*Sample image blob*/,
        extraPageData: [extraData],
    };

    await firstDoc.loadSource(testSource);
    ```

- Load a PDF file and render its annotations using [`PDFSource`]({{ site.api }}interface/idocument/pdfsource.html)

    ```typescript
    const pdfSource = {
        fileData: /*Sample pdf blob*/,
        convertMode: Dynamsoft.DDV.EnumConvertMode.CM_RENDERALL,
        renderOptions: {
            renderAnnotations: Dynamsoft.DDV.EnumAnnotationRenderMode.RENDER_ANNOTATIONS,
        },
    };

    await firstDoc.loadSource(pdfSource);
    ```

- Load a PDF file with it annotations using [`PDFSource`]({{ site.api }}interface/idocument/pdfsource.html)

    ```typescript
    const pdfSource = {
        fileData: /*Sample pdf blob*/,
        convertMode: Dynamsoft.DDV.EnumConvertMode.CM_RENDERALL,
        renderOptions: {
            renderAnnotations: Dynamsoft.DDV.EnumAnnotationRenderMode.LOAD_ANNOTATIONS,
        },
    };

    await firstDoc.loadSource(pdfSource);
    ```

## Save pages

**Use case**

- Save page as a JPEG file using [`saveToJpeg()`]({{ site.api }}interface/idocument/index.html#savetojpeg)

    ```typescript
    // Save the first page in the doc to a JPEG file with JPEG compression quality 60.
    const settings1 = {
        quality: 60, // The default quality is 80.
    };
    const result1 = await firstDoc.saveToJpeg(0, settings1);

    // Save the second page in the doc to a JPEG file with default JPEG compression quality
    const result2 = await firstDoc.saveToJpeg(1);

    // Save the first page with annotations
    const settings2 = {
        saveAnnotation: true, 
    };
    const result3 = await firstDoc.saveToJpeg(0, settings2);
    ```

- Save page(s) as a TIFF file using [`saveToTiff()`]({{ site.api }}interface/idocument/index.html#savetotiff)

    ```typescript
    // Set custom Tag of the tiff file
    const customTag1 = {
    id: 700,
    content: "Created By Dynamsoft",
    contentIsBase64: false,
    };

    // Set SaveTiffSettings
    const tiffSettings = {
        customTag: [customTag1],
        compression: "tiff/auto",
    };

    // Save the fifth, sixth, seventh pages to a multi-page TIFF file with the specified tiff settings.
    const result1 = await firstDoc.saveToTiff([4,5,6], tiffSettings);

    // Save the whole document to a multi-page TIFF file with the specified tiff settings.
    const result2 = await firstDoc.saveToTiff(tiffSettings);

    // Save the whole document to a multi-page TIFF file without any tiff settings.
    const result2 = await firstDoc.saveToTiff();
    ```

- Save page(s) as a PDF file using [`saveToPdf()`]({{ site.api }}interface/idocument/index.html#savetopdf)

    ```typescript
    // Set SavePdfSettings
    const pdfSettings = {
        author: "Dynamsoft",
        compression: "pdf/jpeg",
        pageType: "page/a4",
        creator: "DDV",
        creationDate: "D:20230101085959-08'00'",
        keyWords: "samplepdf",
        modifiedDate: "D:20230101090101-08'00'",
        producer: "Dynamsoft Document Viewer",
        subject: "SamplePdf",
        title: "SamplePdf",
        version: "1.5",
        quality: 90,
    };

    // Save the fifth, sixth, seventh pages to a multi-page PDF file with the specified pdf settings.
    const result1 = await firstDoc.saveToPdf([4,5,6], pdfSettings);

    // Save the whole document to a multi-page PDF file with the specified pdf settings.
    const result2 = await firstDoc.saveToPdf(pdfSettings);

    // Save the whole document to a multi-page PDF file without any pdf settings.
    const result3 = await firstDoc.saveToPdf();
    ```

- Save page(s) as an encrypted PDF file using [`saveToPdf()`]({{ site.api }}interface/idocument/index.html#savetopdf)

    ```typescript
    // Set SavePdfSettings
    const pdfSettings = {
        password: "Dynamsoft-1",
    };

    // Save the whole document to a multi-page PDF file.
    const result = await firstDoc.saveToPdf(pdfSettings);
    ```

- Save page(s) with annotations as a PDF file using [`saveToPdf()`]({{ site.api }}interface/idocument/index.html#savetopdf)

    ```typescript  
    const pdfSettings = {
        saveAnnotation: "annotation",
    };

    // Save the whole document to a multi-page PDF file.
    const result = await firstDoc.saveToPdf(pdfSettings);
    ```

## Move or switch pages

**Use case**

- Move pages to the specified order using [`movePages()`]({{ site.api }}interface/idocument/index.html#movepages)

    ```typescript
    // Move the second, fourth, sixth pages to the begining of the doc. 
    // The moved pages are in (original sixth, fourth, second) order.
    firstDoc.movePages([5,3,1], 0);
    ```

    ![Move pages-1](/assets/imgs/movepages-1.png)

- Move pages to the end

    ```typescript
    // Move the first and second page to the end of the doc.
    firstDoc.movePages([0,1]);
    ```
  ![Move pages-2](/assets/imgs/movepages-2.png)

- Switch the order of two pages using [`switchPage()`]({{ site.api }}interface/idocument/index.html#switchpage)

    ```typescript
    // Switch the order of the first page and third page 
    firstDoc.switchPage(0,2);
    ```

## Get/update page data

**Use case**

- Get [`PageData`]({{ site.api }}interface/idocument/pagedata.html) of the first page using [`getPageData()`]({{ site.api }}interface/idocument/index.html#getpagedata)

    ```typescript
    const pageData = await firstDoc.getPageData(firstDoc.pages[0]);
    ```
- Update the first page in the document with the new page, [`updatePage()`]({{ site.api }}interface/idocument/index.html#updatepage)

    ```typescript
    const updateFirstPage = {
        fileIndex: 0, // using the first page of new file.
    };

    const fileData = /*Sample file blob*/,

    await firstDoc.updatePage(firstDoc.pages[0], fileData, updateFirstPage);
    ```
## Set/get custom data to page

Sometimes, some custom data needs to be set with the specified page, [`setPageCustomData()`]({{ site.api }}interface/idocument/index.html#setpagecustomdata) & [`getPageCustomData()`]({{ site.api }}interface/idocument/index.html#getpagecustomdata) can be used in this case.

**Use case**

- Set custom data (whether has barcode in page) with the first page

    ```typescript
    const customData ={
        hasBarcode: true; // sample custom data
    };
    await firstDoc.setPageCustomData(firstDoc.pages[0], customData);
    ```

- Get custom data from the first page

    ```typescript
    await firstDoc.getPageCustomData(firstDoc.pages[0]);
    ```

## Delete pages

**Use case**

- Delete specified page(s) using [`deletePages()`]({{ site.api }}interface/idocument/index.html#deletepages)

    ```typescript
    // Delete the second and third pages
    firstDoc.deletePages([1,2]);
    ```

- Delete all pages using [`deleteAllPages()`]({{ site.api }}interface/idocument/index.html#deleteallpages)

    ```typescript
    firstDoc.deleteAllPages();
    ```


