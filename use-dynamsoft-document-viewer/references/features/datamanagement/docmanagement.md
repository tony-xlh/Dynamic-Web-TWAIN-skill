---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Features - Document Management
keywords: Documentation, Dynamsoft Document Viewer, Features, Document Management
breadcrumbText: Document Management
description: Dynamsoft Document Viewer Documentation Features, Document Management
permalink: /features/datamanagement/docmanagement.html
---

# Document Management

DDV manages document data through the [`DocumentManager`]({{ site.api }}class/documentmanager.html) class, which can implement functions such as creating, deleting, and merging documents.

The `Dynamsoft.DDV.documentManager` instance will be created automatically as soon as DDV is initialized.

## Create a new document

Use [`createDocument()`]({{ site.api }}class/documentmanager.html#createdocument) method to create a new document in DDV, can also specify the document's name, author and creationDate at the same time.

```typescript
const docManager = Dynamsoft.DDV.documentManager;

// Specify the name, author and creationDate
const firstDoc = docManager.createDocument({
    name: "first_document",
    author: "DDV",
    creationDate: "D:20230101085959-08'00'",
    });

// Document's name and creationDate will be generated automatically, and author will be blank, if they are not specified
const secondDoc = docManager.createDocument();
```

`firstDoc` and `secondDoc` above are the document objects, please refer to [Page Management]({{ site.features }}datamanagement/pagemanagement.html) and see how to manage the page data in document.

## Merge documents

DDV provides the method [`mergeDocuments()`]({{ site.api }}class/documentmanager.html#mergedocuments) to merge the specified documents to a new document. 

Take two documents which are created above as an example and merge them to a new document `mergedDoc` and delete the original documents.

```typescript
// Get the documents' docUid
const docUid1 = firstDoc.uid;
const docUid2 = secondDoc.uid;

// Merge options
const mergeOptions = {
    name: "mergedDoc", // Specify the name of the new document.
    author: "DDV", // Specify the author of the new document.
    creationDate: "D:20230101085959-08'00'", // Specify the creation date of the new document.
    deleteOriginal: true, // Delete the original documents after merging.
};

// const docManager = Dynamsoft.DDV.documentManager;
// Merge two documents.
const mergedDoc = docManager.mergeDocuments([docUid1, docUid2], mergeOptions);
```

## Copy or move pages from a specified document to another

Sometimes, may need to copy or move some pages in specified document to another document. DDV has two methods [`copyPagesToDocument()`]({{ site.api }}class/documentmanager.html#copypagestodocument) and [`movePagesToDocument()`]({{ site.api }}class/documentmanager.html#movepagestodocument) which can achieve this scenario.

**Use case**

- Copy the first and second pages of `firstDoc` to `secondDoc` and put them before the first page in `secondDoc`.

    ```typescript
    // Get the documents' docUid
    const docUid1 = firstDoc.uid;
    const docUid2 = secondDoc.uid;

    // Copy Options
    const copyOptions = {
        sourceIndices: [0,1], // Specify the first and second pages
        insertBeforeIndex: 0, // Specify the location of the copied page in the new document
    };

    // const docManager = Dynamsoft.DDV.documentManager;
    // Copy pages
    docManager.copyPagesToDocument(docUid1, docUid2, copyOptions);
    ```

- Move the first and second pages of `firstDoc` to `secondDoc` and put them before the first page in `secondDoc`.

    ```typescript
    // Get the documents' docUid
    const docUid1 = firstDoc.uid;
    const docUid2 = secondDoc.uid;

    // Move Options
    const moveOptions = {
        sourceIndices: [0,1], // Specify the first and second pages
        insertBeforeIndex: 0, // Specify the location of the copied page in the new document
    };

    // const docManager = Dynamsoft.DDV.documentManager;
    // Move pages
    docManager.movePagesToDocument(docUid1, docUid2, moveOptions);
    ```

## Delete Documents

Use [`deleteDocuments()`]({{ site.api }}class/documentmanager.html#deletedocuments) and [`deleteAllDocuments()`]({{ site.api }}class/documentmanager.html#deletealldocuments) methods to delete the existing documents.

**Use case**

- Delete the specified document(s), take `firstDoc` as an example.

    ```typescript
    // Get firstDoc's docUid
    const docUid = firstDoc.uid; 

    // const docManager = Dynamsoft.DDV.documentManager;
    // Delete firstDoc
    docManager.deleteDocuments([docUid]);
    ```

- Delete all documents.

    ```typescript
    // const docManager = Dynamsoft.DDV.documentManager;
    // Delete all documents
    docManager.deleteAllDocuments();
    ```


## References

- [`DocumentManage Class`]({{ site.api }}class/documentmanager.html)
- [`Interface IDocument`]({{ site.api }}interface/idocument/index.html)