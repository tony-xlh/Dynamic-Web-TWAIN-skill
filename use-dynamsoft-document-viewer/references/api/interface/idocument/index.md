---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface IDocument
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface IDocument
breadcrumbText: Interface IDocument
description: Dynamsoft Document Viewer Documentation API Reference Interface IDocument Page
permalink: /api/interface/idocument/index.html
---

# IDocument

This interface that defines a document object.

## Members

| API Name            | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| [`name`](#name)                | Return the name of current document.                         |
| [`author`](#author)              | Return the author of current document.                       |
| [`creationDate`](#creationdate)       | Return the creation date of current document.                |
| [`uid`](#uid)                 | Return the docUid of current document.                       |
| [`pages`](#pages)               | Return the array of pageUids of current document.                        |
| [`loadSource()`](#loadsource)        | Load file(s) to current document.                            |
| [`getPageData()`](#getpagedata)       | Get the data of specified page.                              |
| [`updatePage()`](#updatepage)       | Update a page specified by the pageUid with the new data.    |
| [`setPageCustomData()`](#setpagecustomdata) | Set the custom data to the specified page.                   |
| [`getPageCustomData()`](#getpagecustomdata) | Get the custom data of the specified page.                   |
| [`deletePages()`](#deletepages)       | Delete the specified pages from current document.            |
| [`deleteAllPages()`](#deleteallpages)    | Delete all pages in current document.                        |
| [`movePages()`](#movepages)         | Move specified page(s) to the target position in current document. |
| [`switchPage()`](#switchpage)        | Swap the position of two pages in current document.          |
| [`insertBlankPage()`](#insertblankpage)          | Insert a blank page to current document. |
| [`isPageModified()`](#ispagemodified)          | Check if a page is modified. |
| [`rename()`](#rename)            | Rename current document.                                     |
| [`saveToPng()`](#savetopng)         | Save specified page or current page in current document to a PNG file. |
| [`saveToJpeg()`](#savetojpeg)        | Save specified page or current page in current document to a JPEG file. |
| [`saveToTiff()`](#savetotiff)        | Save specified page(s) or all pages in current document to a TIFF file. |
| [`saveToPdf()`](#savetopdf)        | Save specified page(s) or all pages in current document to a PDF file. |
| [`print()`](#print)             | Use the browser’s built-in print feature to print the specified image(s). |
| [`createTextSearcher()`](#createtextsearcher)             | Create a text searcher. |

### name

Return the name of current document.

**Syntax**

```typescript
readonly name: string;
```

**Remark**

- It can be set while creating the document by using [`createDocument()`]({{ site.api }}class/documentmanager.html#createdocument). If it is not set, return the name which is auto generated.

### author

Return the author of current document.

**Syntax**

```typescript
readonly author: string;
```

**Remark**

- It can be set while creating the document by using [`createDocument()`]({{ site.api }}class/documentmanager.html#createdocument). If it is not set, return `''`.

### creationDate

Return the creation date of current document.

**Syntax**

```typescript
readonly creationDate: string;
```

**Remark**

- It can be set while creating the document by using [`createDocument()`]({{ site.api }}class/documentmanager.html#createdocument). If it is not set, return the actual creation date of the document.

### uid

Return the docUid of current document.

**Syntax**

```typescript
readonly uid: string;
```

### pages

Return the array of pageUids of current document. 

**Syntax**

```typescript
readonly pages: string[];
```

**Remark**

- Returns an array of pageUids.

**Code Snippet**

```typescript
const firstDoc = Dynamsoft.DDV.documentManager.createDocument({
    name: "first_document",
    author: "DDV",
    creationDate: "D:20230101085959-08'00'",
    });

const docName = firstDoc.name;
const docAuthor = firstDoc.author;
const docCreationDate = firstDoc.creationDate;
const docUid = firstDoc.uid;
const docPages = firstDoc.pages;
```


### loadSource()

Load file(s) to current document.

**Syntax**

```typescript
loadSource(fileData: Blob | Blob[], index?: number): Promise<string[]>;
loadSource(sources: Source | PdfSource | (Source | PdfSource)[], index?: number): Promise<string[]>;
```

**Parameters**

`fileData`: The blob of the file to be loaded.

`sources`: The target files, it could be a file or a file array. Please refer to [`Source`](/api/interface/idocument/source.md). `Source` can be extended to [`PdfSource`](/api/interface/idocument/pdfsource.md).

`index`: The position in the document where the file(s) will be loaded to. If not set or out of the maximum range, the loaded file(s) will be added from the end of the document.

**Return Value**

A Promise object which will be resolved with the page uids of the loaded pages when the file(s) are successfully loaded.

**Code Snippet**

```typescript
const firstDoc = Dynamsoft.DDV.documentManager.createDocument({
    name: "first_document",
    author: "DDV",
    creationDate: "D:20230101085959-08'00'",
    });
const source = {
    fileData: /*sampleBlob*/;
};
await firstDoc.loadSource([source]);
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------                               
 -80001 | License string is invalid.                              
 -80002 | *XXX(LicenseModuleName)* module license has expired.                                                               
 -80003 | *XXX(LicenseModuleName)* module license is missing.                         
 -80004 | *XXX(LicenseModuleName)* module license version does not match.                                 
 -80005 | Domain does not match the domain bound to the *XXX(LicenseModuleName)* module license. 
 -80050 | DDV.Core.init() has not been set up yet.  
 -80051 | DDV.Core.init() has not been completed.   
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80200 | File type is not supported. 
 -80202 | Failed to read the PDF file because it's encrypted and the correct password is not provided.
 -80203 | Failed to read some annotations because they are not supported by Dynamsoft Document Viewer so far.
 -80204 | PDFs containing XFA (XML Forms Architecture) forms are not supported.

### getPageData()

Get the data of specified page.

**Syntax**

```typescript
getPageData(pageUid: string): IPageData;
```

**Parameters**

`pageUid`: The uid of the page.

**Return Value**

[`IPageData`](/api/interface/ipagedata.md) object.

**Code Snippet**

```typescript
const pageData = firstDoc.getPageData(firstDoc.pages[0]);
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80105 | *XXX(API)*: The specified page(s) do not exist.


### updatePage()

Update a page specified by the pageUid with the new data.

**Syntax**

```typescript
updatePage(pageUid: string, source: UpdatedSource | UpdatedPdfSource): Promise<boolean>;
```

**Parameters**

`pageUid`: The uid of the page to be updated.

`source`: The new data. Please refer to [`UpdatedSource`](/api/interface/updatedsource.md) and [`UpdatedPdfSource`](/api/interface/updatedpdfsource.md).

**Return Value**

A Promise object which will be resolved with a boolean value.

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
const source = {
    fileIndex: 1, // Using the second page of the new multi-page file, such as PDF or TIFF.
    fileData: /*sample blob*/
};

await firstDoc.updatePage(firstDoc.pages[0], source);
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80001 | License string is invalid.                              
 -80002 | *XXX(LicenseModuleName)* module license has expired.                                                               
 -80003 | *XXX(LicenseModuleName)* module license is missing.                         
 -80004 | *XXX(LicenseModuleName)* module license version does not match.                                 
 -80005 | Domain does not match the domain bound to the *XXX(LicenseModuleName)* module license. 
 -80050 | DDV.Core.init() has not been set up yet.  
 -80051 | DDV.Core.init() has not been completed.   
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80200 | File type is not supported. 
 -80202 | Failed to read the PDF file because it's encrypted and the correct password is not provided.
 -80203 | Failed to read some annotations because they are not supported by Dynamsoft Document Viewer so far.
 -80204 | PDFs containing XFA (XML Forms Architecture) forms are not supported.


### setPageCustomData()

Set the custom data to the specified page.

**Syntax**

```typescript
setPageCustomData(pageUid: string, data: any): Promise<boolean>;
```

**Parameters**

`pageUid`: The uid of the page.

`data`: The custom data to set.

**Return Value**

A Promise object which will be resolved with a boolean value.

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
const customData ={
    hasBarcode: true; // sample custom data
};
await firstDoc.setPageCustomData(firstDoc.pages[0], customData);
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80105 | *XXX(API)*: The specified page(s) do not exist.

### getPageCustomData()

Get the custom data of the specified page.

**Syntax**

```typescript
getPageCustomData(pageUid: string): Promise<any>;
```

**Parameters**

`pageUid`: The uid of the page.

**Return Value**

A Promise object which will be resolved with the custom data.

**Code Snippet**

```typescript
const customdata = await firstDoc.getPageCutomData(firstDoc.pages[0]);
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80105 | *XXX(API)*: The specified page(s) do not exist.

### deletePages()

Delete the specified pages from current document.

**Syntax**

```typescript
deletePages(indices: number[]): boolean;
```

**Parameters**

`indices`: The array of page indices which will be removed. 

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
// Delete the first and second page.
firstDoc.deletePages([0,1]);
```

**Warning**

 Error Code  | Error Message                                   | API return value     
-------------|------------------------------------------------|---------------     
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  | `false`

### deleteAllPages()

Delete all pages in current document.

**Syntax**

```typescript
deleteAllPages(): boolean;
```

**Parameters**

None.

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
// Delete all pages from the doc.
firstDoc.deleteAllPages();
```

### movePages()

Move specified page(s) to the target position in current document.

**Syntax**

```typescript
movePages(indices: number[], insertBeforeIndex?: number): void;
```

**Parameters**

`indices`: The array of page(s) indices to be moved.

`insertBeforeIndex`: Moved pages will be placed before this index. If not set or out of the maximum range, the specified page(s) will be moved after the last page.

**Code Snippet**

```typescript
// Move the second, fourth, sixth pages to the begining of the doc
// The moved pages are in (original sixth, fourth, second) order.
firstDoc.movePages([5,3,1], 0);
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  


### switchPage()

Swap the position of two pages in current document.

**Syntax**

```typescript
switchPage(oneIndex: number, anotherIndex: number): void;
```

**Parameters**

`oneIndex`: The index of one page.

`anotherIndex`: The index of another page.

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
// Switch the third and sixth pages.
firstDoc.switchPage(2, 5);
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80101 | *XXX(API)*: *XXX(ParameterName)* is out of range.    
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  

### insertBlankPage()

Insert a blank page to current document.

**Syntax**

```typescript
insertBlankPage(
  pageWidth: number;
  pageHeight: number;
  insertBeforeIndex?: number;
):string;
```

**Parameters**

`pageWidth`: The page width of the blank page to insert. The unit is point.

`pageHeight`: The page height of the blank page to insert. The unit is point. 

`insertBeforeIndex`: The blank page will be inserted before this index. If not set or out of the maximum range, the blank page will be added after the last page.

*Common page sizes:*

 Page size | pageWidth (pt) | pageHeight (pt) 
-----------|------------------|-------------------
 Letter    | 612              | 792                
 Legal     | 612              | 1008                
 A4        | 597.6              | 842.4              
 A3        | 842.4             | 1188             

**Return value**

The page uid of the inserted blank page.

**Exception**

 Error Code  | Error Message                                        
-------------|-----------------------------------------------------
 -80050      | DDV.Core.init() has not been set up yet.  
 -80051      | DDV.Core.init() has not been completed.
 -80100      | *XXX(API)*: *XXX(ParameterName)* is invalid. 
 -80101      | *XXX(API)*: *XXX(ParameterName)* is out of range. 
 -80102      | *XXX(API)*: *XXX(ParameterName)* is missing.

### isPageModified()

Check if a page is modified.

**Syntax**

```typescript
isPageModified(index: number): boolean;
```

**Parameters**

`index`: The page index.

**Return value**

A boolean value which indicates whether the page is modified.

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80101 | *XXX(API)*: *XXX(ParameterName)* is out of range.    
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  

### rename()

Rename current document.

**Syntax**

```typescript
rename(name: string): boolean;
```

**Parameters**

`name`: The new name of current document.

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
const firstDoc = Dynamsoft.DDV.documentManager.createDocument({
    name: "first_document",
    author: "DDV",
    creationDate: "D:20230101085959-08'00'",
    });
firstDoc.rename("my_doc");
```

**Warning**

 Error Code  | Error Message                                  | API return value     
--------|-----------------------------------------------------|---------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  | `false`

### saveToPng()

Save specified page or current page in current document to a PNG file.

**Syntax**

```typescript
saveToPng(index: number, savePngSettings?: SavePngSettings): Promise<Blob>;
```

**Parameters**

`index`: Specify index of the page to be saved.

`savePngSettings`: Specify the save settings. Please refer to [`SavePngSettings`]({{ site.api }}interface/idocument/savepngsettings.html).

**Return Values**

A Promise object which will be resolved with `Blob` of the saved image.

**Code Snippet**

```typescript
// Save the first page to a PNG file.
const result = await firstDoc.saveToPng(0);
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------                                    
 -80001 | License string is invalid.                              
 -80002 | *XXX(LicenseModuleName)* module license has expired.                                                               
 -80003 | *XXX(LicenseModuleName)* module license is missing.                         
 -80004 | *XXX(LicenseModuleName)* module license version does not match.                                 
 -80005 | Domain does not match the domain bound to the *XXX(LicenseModuleName)* module license.  
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80101 | *XXX(API)*: *XXX(ParameterName)* is out of range.    
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  

### saveToJpeg()

Save specified page or current page in current document to a JPEG file.

**Syntax**

```typescript
saveToJpeg(index: number, saveJpegSettings?: SaveJpegSettings): Promise<Blob>;
```

**Parameters**

`index`: Specify index of the page to be saved.

`saveJpegSettings`: Specify the save settings. Please refer to [`SaveJpegSettings`]({{ site.api }}interface/idocument/savejpegsettings.html).

**Return Values**

A Promise object which will be resolved with `Blob` of the saved image.

**Code Snippet**

```typescript
// Save the first page as a JPEG file with a JPEG compression quality of 100, and the annotations are saved as part of the JPEG.
const settings = {
    quality: 100,
    saveAnnotation: false,
};
const result = await firstDoc.saveToJpeg(0, settings);
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------                                          
 -80001 | License string is invalid.                              
 -80002 | *XXX(LicenseModuleName)* module license has expired.                                                               
 -80003 | *XXX(LicenseModuleName)* module license is missing.                         
 -80004 | *XXX(LicenseModuleName)* module license version does not match.                                 
 -80005 | Domain does not match the domain bound to the *XXX(LicenseModuleName)* module license.  
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80101 | *XXX(API)*: *XXX(ParameterName)* is out of range.    
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  

### saveToTiff()

Save specified page(s) or all pages in current document to a TIFF file. 

**Syntax**

```typescript
saveToTiff(indices: number[], saveTiffSettings?: SaveTiffSettings): Promise<Blob>;
saveToTiff(saveTiffSettings?: SaveTiffSettings): Promise<Blob>;
```

**Parameters**

`indices`: The array of page indices which will be saved. If not set, will save all pages to a TIFF file by default.

`saveTiffSettings`: Specify the save settings. Please refer to [`SaveTiffSettings`]({{ site.api }}interface/idocument/savetiffsettings.html). 

**Return Values**

A Promise object which will be resolved with `Blob` of the saved TIFF file.

**Code Snippet**

```typescript
// Set custom tag
const customTag1 = {
    id: 700,
    content: "Created By Dynamsoft",
    contentIsBase64: false,
}

// Set SaveTiffSettings
const tiffSettings = {
    customTag: [customTag1],
    compression: "tiff/auto",
}

// Save the fifth, sixth, seventh pages to a multi-page TIFF file with the specified tiff settings.
const result1 = await firstDoc.saveToTiff([4,5,6], tiffSettings);

// Save the whole document to a multi-page TIFF file with the specified tiff settings.
const result2 = await firstDoc.saveToTiff(tiffSettings);
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------                                      
 -80001 | License string is invalid.                              
 -80002 | *XXX(LicenseModuleName)* module license has expired.                                                               
 -80003 | *XXX(LicenseModuleName)* module license is missing.                         
 -80004 | *XXX(LicenseModuleName)* module license version does not match.                                 
 -80005 | Domain does not match the domain bound to the *XXX(LicenseModuleName)* module license.  
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80305 | There is no image in the current document.

### saveToPdf()

Save specified page(s) or all pages in current document to a PDF file.

**Syntax**

```typescript
saveToPdf(indices: number[], savePdfSettings?: SavePdfSettings): Promise<Blob>;
saveToPdf(savePdfSettings?: SavePdfSettings): Promise<Blob>;
```

**Parameters**

`indices`: The array of page indices which will be saved. 

`savePdfSettings`: Specify the save settings. Please refer to [`SavePdfSettings`]({{ site.api }}interface/idocument/savepdfsettings.html). If not set, will save all pages to a PDF file by default.

**Return Values**

A Promise object which will be resolved with `Blob` of the saved PDF file.

**Code Snippet**

```typescript
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
    password: "dynamsoft",
    saveAnnotation: "annotation",
    imageScaleFactor: 1,
};

// Save the fifth, sixth, seventh pages to a multi-page PDF file with the specified pdf settings.
const result1 = await firstDoc.saveToPdf([4,5,6], pdfSettings);

// Save the whole document to a multi-page PDF file with the specified pdf settings.
const result2 = await firstDoc.saveToPdf(pdfSettings);
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------                                     
 -80001 | License string is invalid.                              
 -80002 | *XXX(LicenseModuleName)* module license has expired.                                                               
 -80003 | *XXX(LicenseModuleName)* module license is missing.                         
 -80004 | *XXX(LicenseModuleName)* module license version does not match.                                 
 -80005 | Domain does not match the domain bound to the *XXX(LicenseModuleName)* module license.  
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80305 | There is no image in the current document.
 -80318 | The document contains unsupported fonts, which may result in font loss after saving.

### print()

Use the browser’s built-in print feature to print the specified image(s) and whether printable annotations can be printed

**Syntax**

```typescript
print(printSettings?: PrintSettings);
print(indices: number[], printSettings?: PrintSettings);
```

**Parameters**

`indices`: The array of page indices which will be printed. If not set, will export all pages to the browser’s built-in print window.

`printSettings`: Specify the print settings. Please refer to [`PrintSettings`]({{ site.api }}interface/idocument/printsettings.html).

**Return Values**

`true`: Successfully.

`false`: Failed.

---

**Code Snippet**

```typescript
// To print the whole doc pages
firstDoc.print();

// To print the second and third pages
firstDoc.print([1,2]);

// To print the whole doc pages, including printable annotations.
firstDoc.print({
    printAnnotation: true;
});
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80305 | There is no image in the current document.

### createTextSearcher()

Create a text searcher.

**Syntax**

```typescript
createTextSearcher(text: string, options?: SearchTextOptions): IDocTextSearcher;
```

**Parameters**

`text`: Text to search

`options`: Please refer to [`SearchTextOptions`](/api/interface/searchtextoptions.md).

**Return Values**

An [`IDocTextSearcher`](/api/interface/idocument/idoctextsearcher.md) object.

---

**Code Snippet**

```typescript
const searcher = firstDoc.createTextSearcher("text",{caseSensitive:false})
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  

