---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Getting Started - Adding the dependency
keywords: Documentation, Dynamsoft Document Viewer, Getting Started, Adding the dependency
breadcrumbText: Adding the dependency
description: Dynamsoft Document Viewer Documentation Getting Started, Adding the dependency
permalink: /gettingstarted/add_dependency.html
---

# Adding the dependency

To use the SDK, we need to include the package below.

- `dynamsoft-document-viewer`: Required, it provides functions to create the viewers.


## Use a CDN

The simplest way to include the SDK is to use either the [jsDelivr](https://jsdelivr.com/) or [UNPKG](https://unpkg.com/) CDN.

- jsDelivr

  ```html
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/ddv.js"></script>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/ddv.css">
  ```

- UNPKG

  ```html
  <script src="https://unpkg.com/dynamsoft-document-viewer@latest/dist/ddv.js"></script>
  <link rel="stylesheet" href="https://unpkg.com/dynamsoft-document-viewer@latest/dist/ddv.css">
  ```

## Host the SDK yourself

Besides using the CDN, you can also download the Solution and host related files on your own website/server before including it in your application.

Options to download the SDK:

- From the website

  [Download the JavaScript ZIP package](https://www.dynamsoft.com/document-viewer/downloads)

- yarn

  ```cmd
  yarn add dynamsoft-document-viewer@latest
  ```

- npm

  ```cmd
  npm install dynamsoft-document-viewer@latest
  ```

Depending on how you downloaded the SDK and where you put it, you can typically include it like this:

  ```html
  <!-- Upon extracting the zip package into your project, you can generally include it in the following manner -->
  <script src="./Your-Folder/dist/ddv.js"></script>
  <link rel="stylesheet" href="./Your-Folder/dist/ddv.css">
  ```

or

  ```html
  <script src="./node_modules/dynamsoft-document-viewer/dist/ddv.js"></script>
  <link rel="stylesheet" href="./node_modules/dynamsoft-document-viewer/dist/ddv.css">
  ```

or

  ```typescript
  import { DDV } from 'dynamsoft-document-viewer';
  import "dynamsoft-document-viewer/dist/ddv.css";
  ```