---
layout: default
title: Display Note
parent: OGM Aardvark
nav_order: 4.5
---

## Description

| Label                 | Description             |
|:----------------------|:------------------------|
| URI                   | `gbl_displayNote_sm`    |
| Obligation            | Optional                |
| Multivalued           | true                    |
| Field type            | array of strings        |
| Purpose               | To highlight additional information about a resource, such as warnings or tips for using the data. |
| Entry Guidelines      | Prefix the string with "Warning:", "Info:", or "Tip:" to specify the type of note.  Future versions of GeoBlacklight will use such prefixes to control the style of the displayed note.  Styles and additional prefixes (for example, in other languages) can be added in the GeoBlacklight config. |
| Commentary            | This field is currently only supported by customizations to the GeoBlacklight application.  On the item page, text in this field will be prominently displayed in a shaded box just after the title. |
| Controlled Vocabulary | no                      |
| Example value         | ```[```<br>```   "Warning: This text (starting with 'This text') will be displayed in a red box",```<br>```    "Info: This text (starting with 'This text') will be displayed in a blue box",```<br>```    "Tip: This text (starting with 'This text') will be displayed in a green box",```<br>```    "This is text without a tag and it will be assigned the default 'note' style"```<br>```  ]``` |
| Element Set           | DCMI                    |
| Group                 | Bibliographic - general |
