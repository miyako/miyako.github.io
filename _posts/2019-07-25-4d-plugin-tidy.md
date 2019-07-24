---
layout: simple
title: Tidy
tags: plugin html v17
---

4D implementation of [tidy](https://github.com/htacg/tidy-html5).  

[miyako/4d-plugin-tidy-html](https://github.com/miyako/4d-plugin-tidy-html5)

<!--more-->

---

```
status:=Tidy (data{;options})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">data</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8">HTML source</div>  
  <div class="syntax-td cell cell--2">options</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8">see below</div>  
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8">see below</div>      
</div>

#### Options

Property|Type|Description
------------|------|----
accessibilityCheckLevel|LONGINT|
altText|TEXT|
anchorAsName|BOOLEAN|
asciiChars|BOOLEAN|
blockTags|BOOLEAN|
bodyOnly|BOOLEAN|
breakBeforeBR|BOOLEAN|
coerceEndTags|BOOLEAN|
CSSPrefix|BOOLEAN|
decorateInferredUL|BOOLEAN|
doctype|TEXT|
dropEmptyElems|BOOLEAN|
dropEmptyParas|BOOLEAN|
dropPropAttrs|BOOLEAN|
duplicateAttrs|BOOLEAN|
emacs|BOOLEAN|
emptyTags|BOOLEAN|
encloseBlockText|BOOLEAN|
encloseBodyText|BOOLEAN|
escapeCdata|BOOLEAN|
escapeScripts|BOOLEAN|
fixBackslash|BOOLEAN|
fixComments|BOOLEAN|
fixUri|BOOLEAN|
gDocClean|BOOLEAN|
hideComments|BOOLEAN|
htmlOut|BOOLEAN|
indentSpaces|BOOLEAN|
indentAttributes|LONGINT|
indentCdata|LONGINT|
indentContent|LONGINT|
inlineTags|BOOLEAN|
joinClasses|BOOLEAN|
joinStyles|BOOLEAN|
keepFileTimes|BOOLEAN|
keepTabs|BOOLEAN|
literalAttribs|BOOLEAN|
logicalEmphasis|BOOLEAN|
lowerLiterals|BOOLEAN|
makeBare|BOOLEAN|
makeClean|BOOLEAN|
mark|BOOLEAN|
mergeDivs|BOOLEAN|
mergeEmphasis|BOOLEAN|
mergeSpans|BOOLEAN|
metaCharset|BOOLEAN|
NCR|BOOLEAN|
newline|BOOLEAN|
numEntities|BOOLEAN|
omitOptionalTags|BOOLEAN|
outputBOM|BOOLEAN|
pPrintTabs|BOOLEAN|
preserveEntities|BOOLEAN|
preTags|BOOLEAN|
priorityAttributes|BOOLEAN|
punctWrap|BOOLEAN|
quiet|BOOLEAN|
quoteAmpersand|BOOLEAN|
quoteMarks|BOOLEAN|
quoteNbsp|BOOLEAN|
replaceColor|BOOLEAN|
showErrors|BOOLEAN|
showInfo|BOOLEAN|
showMarkup|BOOLEAN|
showMetaChange|BOOLEAN|
showWarnings|BOOLEAN|
skipNested|BOOLEAN|
sortAttributes|BOOLEAN|
strictTagsAttr|BOOLEAN|
styleTags|BOOLEAN|
tabSize|BOOLEAN|
upperCaseAttrs|BOOLEAN|
upperCaseTags|BOOLEAN|
useCustomTags|BOOLEAN|
vertSpace|BOOLEAN|
warnPropAttrs|BOOLEAN|
word2000|BOOLEAN|
wrapAsp|BOOLEAN|
wrapAttVals|BOOLEAN|
wrapJste|BOOLEAN|
wrapLen|BOOLEAN|
wrapPhp|BOOLEAN|
wrapScriptlets|BOOLEAN|
wrapSection|BOOLEAN|
writeBack|BOOLEAN|
xhtmlOut|BOOLEAN|
xmlDecl|BOOLEAN|
xmlOut|BOOLEAN|
xmlPIs|BOOLEAN|
xmlSpace|BOOLEAN|
xmlTags|BOOLEAN|
encoding|TEXT|
language|TEXT|

#### Status

Property|Type|Description
------------|------|----
status|LONGINT|return value of ``tidyParseBuffer``
detectedGenericXml|BOOLEAN|
detectedHtmlVersion|BOOLEAN|
detectedXhtml|BOOLEAN|
html|TEXT|
info|TEXT|





