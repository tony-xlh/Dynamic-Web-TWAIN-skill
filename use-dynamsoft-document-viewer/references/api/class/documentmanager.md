---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - DocumentManager Class
keywords: Documentation, Dynamsoft Document Viewer, API Reference, DocumentManager Class
breadcrumbText: DocumentManager Class
description: Dynamsoft Document Viewer Documentation API Reference DocumentManager Class Page
permalink: /api/class/documentmanager.html
---

# DocumentManager Class

The `Dynamsoft.DDV.documentManager` instance will be created automatically as soon as DDV is initialized. Please refer to [`documentManager`]({{ site.api }}namespace/ddv.html#static-documentmanager).

## API Index

**Methods**

| API Name              | Description                                               |
| --------------------- | --------------------------------------------------------- |
| [`createDocument()`](#createdocument)     | Create an empty document.                                 |
| [`deleteDocuments()`](#deletedocuments)     | Delete the specified document(s) by the document uid(s).  |
| [`deleteAllDocuments()`](#deletealldocuments)  | Delete all documents.                                     |
| [`getDocument()`](#getdocument)         | Get the specified document object with the document uid.  |
| [`getAllDocuments()`](#getalldocuments)     | Get all documents' objects.                               |
| [`mergeDocuments()`](#mergedocuments)      | Merge specified documents to a new document.              |
| [`copyPagesToDocument()`](#copypagestodocument) | Copy pages from a specified document to another document. |
| [`movePagesToDocument()`](#movepagestodocument) | Move pages from a specified document to another document. |

**Events**

| API Name | Description                                        |
| -------- | -------------------------------------------------- |
| [`on()`](#on)     | Bind a listener to the specified event.            |
| [`off()`](#off)    | Unbind event listener(s) from the specified event. |

***Integrated Events***

| Event Name      | Description                               |
| --------------- | ----------------------------------------- |
| [`documentCreated`](#documentcreated) | Triggered when a new document is created. |
| [`documentDeleted`](#documentdeleted) | Triggered when a document is deleted.     |

## Methods

### createDocument()

Create an empty document.

**Syntax**

```typescript
createDocument(createDocumentOptions?: CreateDocumentOptions): IDocument;
```

**Parameters**

`createDocumentOptions`: The configuration used to create a document. Please refer to [`CreateDocumentOptions`]({{ site.api }}interface/createdocumentoptions.html).

**Return value**

The object of the created document. Please refer to [`IDocument`]({{ site.api }}interface/idocument/index.html).

**Code Snippet**

```typescript
const firstDoc = Dynamsoft.DDV.documentManager.createDocument({
    name: "first_document",
    author: "DDV",
    creationDate: "D:20230101085959-08'00'",
    });
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   


### deleteDocuments()

Delete the specified document(s) by the document uid(s).

**Syntax**

```typescript
deleteDocuments(docUids: string[]): boolean;
```

**Parameters**

`docUids`: The array of document uids for the specified docunments.

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

const docUid = firstDoc.uid;

Dynamsoft.DDV.documentManager.deleteDocuments([docUid]);
```

**Warning**

 Error Code  | Error Message                                           | API return value     
-------------|--------------------------------------------------------|---------------    
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.           | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.          | `false`
 -80104 | *XXX(API)*: The specified document(s) do not exist.   | `false`

### deleteAllDocuments()

Delete all documents.

**Syntax**

```typescript
deleteAllDocuments(): boolean;
```

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
Dynamsoft.DDV.documentManager.deleteAllDocuments();
```

### getDocument()

Get the document object with the document uid.

**Syntax**

```typescript
getDocument(docUid: string): IDocument;
```

**Parameters**

`docUid`: The docUid of the specified document.

**Return Value**

The object of the specified document. Please refer to [`IDocument`]({{ site.api }}interface/idocument/index.html).

**Code Snippet**

```typescript
Dynamsoft.DDV.documentManager.getDocument("lnn0ll9o124");
```

### getAllDocuments()

Get all documents' objects.

**Syntax**

```typescript
getAllDocuments(): IDocument[];
```

**Return Value**

The array of all documents' objects. Please refer to [`IDocument`]({{ site.api }}interface/idocument/index.html).

**Code Snippet**

```typescript
Dynamsoft.DDV.documentManager.getAllDocuments();
```

**Remark**

- If there is no document, returns `[]`.


### mergeDocuments()

Merge specified documents to a new document.

**Syntax**

```typescript
mergeDocuments(docUids: string[], mergeDocumentOptions?: MergeDocumentOptions): IDocument;
```

**Parameters**

`docUids`: The array of specified documents' uids.

`mergeDocumentOptions`: The merge document options. Please refer to [`MergeDocumentOptions`]({{ site.api }}interface/mergedocumentoptions.html).

**Return Value**

The object of the new document. Please refer to [`IDocument`]({{ site.api }}interface/idocument/index.html).

**Code Snippet**

```typescript
const firstDoc = Dynamsoft.DDV.documentManager.createDocument({
    name: "first_document",
    author: "DDV",
    creationDate: "D:20230101085959-08'00'",
    });

const source1 = {
    fileData: /*sampleBlob1*/;
};
await firstDoc.loadSource([source1]);

const secondDoc = Dynamsoft.DDV.documentManager.createDocument({
    name: "second_document",
    });

const source2 = {
    fileData: /*sampleBlob2*/;
};
await secondDoc.loadSource([source2]);

const docUid1 = firstDoc.uid; //"lnn0ll9o124"
const docUid2 = secondDoc.uid; //"lnn0iai110t"

const mergeOptions = {
    name: "mergedDoc", // Specify the name of the new document.
    author: "DDV", // Specify the author of the new document.
    creationDate: "D:20230101085959-08'00'", // Specify the creation date. Note that the argument should be D:YYYYMMDDHHmmSSOHH'mm', like D:20230101085959-08'00'.
    deleteOriginal: true, // Whether to delete the original documents.
};

//Merge these two docs
Dynamsoft.DDV.documentManager.mergeDocuments([docUid1, docUid2], mergeOptions);

//OR
Dynamsoft.DDV.documentManager.mergeDocuments(["lnn0ll9o124", "lnn0iai110t"], mergeOptions);
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.   
 -80104 | *XXX(API)*: The specified document(s) do not exist.  
 -80201 | docUid does not allow duplicate.     

### copyPagesToDocument()

Copy pages from a specified document to another document.

**Syntax**

```typescript
copyPagesToDocument(sourceDocUid: string, targetDocUid: string, transferOptions?: TransferOptions): void;
```

**Parameters**

`sourceDocUid`: The uid of source document.

`targetDocUid`: The uid of target document.

`transferOptions`: The transfer options. Please refer to [`TransferOptions`]({{ site.api }}interface/transferoptions.html).

**Code Snippet**

```typescript
// Copy the first and second pages of doc "lnn0ll9o124" to doc "lnn0iai110t" and put them before the first page.
const copyOptions = {
    sourceIndices: [0,1],
    insertBeforeIndex: 0,
};

Dynamsoft.DDV.documentManager.copyPagesToDocument("lnn0ll9o124", "lnn0iai110t", copyOptions);
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.   
 -80104 | *XXX(API)*: The specified document(s) do not exist.  


### movePagesToDocument()

Move pages from a specified document to another document.

**Syntax**

```typescript
movePagesToDocument(sourceDocUid: string, targetDocUid: string, transferOptions?: TransferOptions): void;
```

**Parameters**

`sourceDocUid`: The uid of source document.

`targetDocUid`: The uid of target document.

`transferOptions`: The transfer options. Please refer to [`TransferOptions`]({{ site.api }}interface/transferoptions.html).

**Code Snippet**

```typescript
// Move the first and second pages of doc "lnn0ll9o124" to doc "lnn0iai110t" and put them before the first page.
const moveOptions = {
    sourceIndices: [0,1],
    insertBeforeIndex: 0,
}
Dynamsoft.DDV.documentManager.movePagesToDocument("lnn0ll9o124", "lnn0iai110t", moveOptions);
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.   
 -80104 | *XXX(API)*: The specified document(s) do not exist.  

## Events

### on()

Bind a listener to the specified event. 

**Syntax**

```typescript
on(eventName: EventName, listener:(event:EventObject)=>void): void;
```

**Parameters**

`eventName`: Specify the event name. It should be [an integrated event name](#integrated-events).

`listener`: Specify the listener.

**Code Snippet**

```typescript
// Bind a listener to the integrated event documentCreated.
const eventFunc = (e)=>{
    console.log(e);
    console.log(e.docUid);
    console.log(e.docName);
};

Dynamsoft.DDV.documentManager.on("documentCreated", eventFunc);
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80103 | *XXX(API)*: The value for *XXX(ParameterName)* is not supported.

### off()

Unbind event listener(s) from the specified event. 

**Syntax**

```typescript
off(eventName: EventName, listener?:(event:EventObject)=>void): void;
```

**Parameters**

`eventName`: Specify the event name. It should be [an integrated event name](#integrated-events).

`listener`: Specify the listener. If no listener is specified, unbind all event listeners from the specified event

**Code Snippet**

```typescript
const eventFunc = (e)=>{
    console.log(e);
    console.log(e.docUid);
    console.log(e.docName);
};

Dynamsoft.DDV.documentManager.on("documentCreated", eventFunc);

// Unbind the specified event listener.
Dynamsoft.DDV.documentManager.off("documentCreated", eventFunc);
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80103 | *XXX(API)*: The value for *XXX(ParameterName)* is not supported.
 
### Integrated Events

#### documentCreated

Triggered when a new document is created.

**Callback**

 `DocumentEvent`: An EventObject.

**Attributes**

 `docUid`: The docUid of the created document.

 `docName`: The name of the created document.

#### documentDeleted

Triggered when a document is deleted.

**Callback**

 `DocumentEvent`: An EventObject.

**Attributes**

 `docUid`: The docUid of the deleted document.

 `docName`: The name of the deleted document.

{% comment %} 

#### pagesAdded

Triggered when the page(s) are added.

**Callback**

 `PageAddedEvent`: An EventObject.

**Attributes**

 `docUid`: The uid of the document which adds page(s).

 `indices[]`: The array of the added page(s) index(ices).

 `pageUids[]`: The array of the added page(s) uids.

#### pagesDeleted

Triggered when the page(s) are deleted.

**Callback**

 `PageDeletedEvent`: An EventObject.

**Attributes**

 `docUid`: The uid of the document  which removes page(s).

 `indices[]`: The array of the deleted page(s) indices.

 `pageUids[]`: The array of the deleted page(s) uids. 
 
 {% endcomment %}