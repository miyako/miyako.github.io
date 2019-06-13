---
layout: simple
title: Code signature invalid!
tags: plugin  
---

It seems like some 4D plugins have stopped working since yesterday, possibly because of ``codesign`` issues.

<!--more-->

---

So far, the list includes:

- [x] 4d-plugin-4d-for-oracle
- [x] 4d-plugin-address-book 
- [x] 4d-plugin-apple-file-promises   
- [x] 4d-plugin-apple-window-title-bar  
- [x] 4d-plugin-bookmark-manager  
- [x] 4d-plugin-curl-ftp  
- [x] 4d-plugin-curl-http
- [x] 4d-plugin-curl-v2  
- [x] 4d-plugin-custom-window  
- [x] 4d-plugin-float  
- [x] 4d-plugin-jwt  
- [x] 4d-plugin-mecab-v2  
- [x] 4d-plugin-notes  
- [x] 4d-plugin-prevent-app-nap  
- [x] 4d-plugin-purge  
- [x] 4d-plugin-tesseract-v2  
- [x] 4d-plugin-text-convert  
- [x] 4d-plugin-virtual-key  
- [x] 4d-plugin-xslt  
- [x] 4d-plugin-zip  

I think the cause of the problem might have been that the certificates were revoked (by me), since expired certificates are not supposed to prevent code execution.
