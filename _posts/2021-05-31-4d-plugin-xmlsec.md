---
layout: simple
title: XMLDsig and XAdES
tags: plugin xml v18
---

XML signature based on [xmlsec](https://www.aleksey.com/xmlsec/).

<!--more-->

[miyako/4d-plugin-xmlsec](https://github.com/miyako/4d-plugin-xmlsec/)

```
status:=xmlsec sign(params{;key{;certs}})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">Object</div>
  <div class="syntax-td cell cell--8">see below</div>      
  <div class="syntax-td cell cell--2">key</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8">key used to sign the XML. typically PEM, DER or P12</div>         
  <div class="syntax-td cell cell--2">certs</div>
  <div class="syntax-td cell cell--2">ARRAY BLOB</div>
  <div class="syntax-td cell cell--8">an array of chained certificates that qualify the signer. not used if key is P12. the order doesn't matter, but element 0 must be the signing certficate (so the same value will appear  twice in the array) for XAdES</div>   
 </div>
 
 ```
hash:=xmlsec hash(data{;algorithm})
 ```
 
 <div class="grid">
   <div class="syntax-th cell cell--2">Parameter</div>
   <div class="syntax-th cell cell--2">Type</div>
   <div class="syntax-th cell cell--8">Description</div>
   <div class="syntax-td cell cell--2">data</div>
   <div class="syntax-td cell cell--2">BLOB</div>
   <div class="syntax-td cell cell--8">data to hash</div>      
   <div class="syntax-td cell cell--2">algorithm</div>
   <div class="syntax-td cell cell--2">Text</div>
   <div class="syntax-td cell cell--8">sha1 (default), sha224, sha256, sha384 or sha512</div>         
   <div class="syntax-td cell cell--2">hash</div>
   <div class="syntax-td cell cell--2">Text</div>
   <div class="syntax-td cell cell--8">base64 encoded hash</div>   
  </div>
  
  This is a convenience method to hash a BLOB. 

#### Params ([**XMLDsig**](http://www.w3.org/TR/xmldsig-core/))

`*` indicates default value

Property|Type|Description
------------|------|----
xml | Text|source text
key | Text|format of private key `pem*` `der` `pkcs12` 
password | Text|password to read private key 
cert | Text|format of certificates  `pem*` `der`
xmldsig | Object|root object for XMLDsig
xmldsig.digest | Text|[`dsig:DigestMethod@Algorithm`](https://www.w3.org/TR/xmldsig-core/#sec-DigestMethod) `sha1*` `sha224` `sha256` `sha384` `sha512`
xmldsig.ref | Object|[`dsig:Reference`](https://www.w3.org/TR/xmldsig-core/#sec-Reference)
xmldsig.ref.id | Text|`dsig:Reference@Id`
xmldsig.ref.uri | Text|`dsig:Reference@URI`
xmldsig.ref.type | Text|`dsig:Reference@Type`
xmldsig.sign | Text|[`dsig:SignatureMethod`](https://www.w3.org/TR/xmldsig-core/#sec-SignatureMethod) `rsa-sha1*` `rsa-sha224` `rsa-sha256` `rsa-sha384` `rsa-sha512` `hmac-sha1` `hmac-sha224` `hmac-sha256` `hmac-sha384` `hmac-sha512` `dsa-sha1` `dsa-sha256` `ecdsa-sha1` `ecdsa-sha224` `ecdsa-sha256` `ecdsa-sha384` `ecdsa-sha512`
xmldsig.c14n | Text|[`dsig:CanonicalizationMethod`](https://www.w3.org/TR/xmldsig-core/#sec-CanonicalizationMethod) `1.0*` `1.0.c` `1.1` `1.1.c` `1.0.e` `1.0.e.c`
xmldsig.ns | Text|[namespace `ds*`
xmldsig.id | Text|[`xmldsig:Signature@Id`](https://www.w3.org/TR/xmldsig-core/#sec-Signature) 
xmldsig.ski | Boolean|`false*`
xmldsig.crl | Boolean|`false*`
xmldsig.subjectName | Boolean|`false*`
xmldsig.keyValue | Boolean|`true*`
xmldsig.issuerSerial | Boolean|`false*`
xmldsig.certificate | Boolean|`true*`
xmldsig.keyInfo | Object|
xmldsig.keyInfo.id | Text|[`dsig:KeyInfo@Id`](https://www.w3.org/TR/xmldsig-core/#sec-KeyInfo)
xmldsig.keyInfo.keyName | Text|[`dsig:KeyInfo/dsig:KeyName`](https://www.w3.org/TR/xmldsig-core/#sec-KeyName)

#### Params ([**XAdES**](https://www.w3.org/TR/XAdES/))

`*` indicates default value

Property|Type|Description
------------|------|----
xades | Text|root object for XAdES
xades.ns | Text|namespace `xades*`
xades.digest | Text|[`xades:DigestValue@Algorithm`](https://www.w3.org/TR/XAdES/#Syntax_for_XAdES_The_SignaturePolicyIdentifier_element) `sha1*` `sha224` `sha256` `sha384` `sha512`
xades.qualifyingProperties | Object|[`xades:QualifyingProperties`](https://www.w3.org/TR/XAdES/#Syntax_overview_The_QualifyingProperties)
xades.qualifyingProperties.signedProperties | Object|[`xades:SignedProperties`](https://www.w3.org/TR/XAdES/#Syntax_overview_The_QualifyingProperties_SignedProperties)
xades.qualifyingProperties.signedProperties.id | Object|
xades.qualifyingProperties.signedProperties.signedSignatureProperties | Object|[`xades:SignedSignatureProperties`](https://www.w3.org/TR/XAdES/#Syntax_overview_The_QualifyingProperties_SignedSignatureProperties)
xades.qualifyingProperties.signedProperties.signedSignatureProperties.signingTime | Text|
xades.qualifyingProperties.signedProperties.signedSignatureProperties.signaturePolicyIdentifer | Object|
xades.qualifyingProperties.signedProperties.signedSignatureProperties.signaturePolicyIdentifer.signaturePolicyId[] | Collection
xades.qualifyingProperties.signedProperties.signedSignatureProperties.signaturePolicyIdentifer.signaturePolicyId[].sigPolicyId |Object
xades.qualifyingProperties.signedProperties.signedSignatureProperties.signaturePolicyIdentifer.signaturePolicyId[].sigPolicyId.identifier | Text|
xades.qualifyingProperties.signedProperties.signedSignatureProperties.signaturePolicyIdentifer.signaturePolicyId[].sigPolicyId.digest | Text|
xades.qualifyingProperties.signedProperties.signedSignatureProperties.signaturePolicyIdentifer.signaturePolicyId[].sigPolicyId.description | Text|
xades.qualifyingProperties.signedProperties.signedSignatureProperties.signaturePolicyIdentifer.signaturePolicyId[].sigPolicyId.documentationReferences[] | Collection
xades.qualifyingProperties.signedProperties.signedSignatureProperties.signaturePolicyIdentifer.signaturePolicyId[].sigPolicyId.documentationReferences[].documentationReference | Text
xades.qualifyingProperties.signedProperties.signedDataObjectProperties | Object|
xades.qualifyingProperties.signedProperties.signedDataObjectProperties.dataObjectFormat | Object|
xades.qualifyingProperties.signedProperties.signedDataObjectProperties.dataObjectFormat.id | Text|
xades.qualifyingProperties.signedProperties.signedDataObjectProperties.dataObjectFormat.description | Text|
xades.qualifyingProperties.signedProperties.signedDataObjectProperties.dataObjectFormat.objectIdentifier | Object|
xades.qualifyingProperties.signedProperties.signedDataObjectProperties.dataObjectFormat.objectIdentifier.identifier | Text|
xades.qualifyingProperties.signedProperties.signedDataObjectProperties.dataObjectFormat.objectIdentifier.identifier_qualifier | Text|
xades.qualifyingProperties.signedProperties.signedDataObjectProperties.dataObjectFormat.objectIdentifier.description | Text|
xades.qualifyingProperties.signedProperties.signedDataObjectProperties.dataObjectFormat.mimeType | Text|
xades.qualifyingProperties.signedProperties.signedDataObjectProperties.dataObjectFormat.encoding | Text|

`xades:SigningCertificate` is added automatically  

`xades:SignaturePolicyImplied` is added if `signaturePolicyId.length` is `0`  

`xades:SigPolicyHash` is added automatically  from `policy`

### not implemented

Property|Type|Description
------------|------|----
xades.qualifyingProperties.unsignedProperties | Object|
xades.qualifyingProperties.unsignedProperties.id | Text|
xades.qualifyingProperties.unsignedProperties.unsignedSignatureProperties[] | Collection|
xades.qualifyingProperties.unsignedProperties.unsignedSignatureProperties[].signatureTimeStamp | Object|
xades.qualifyingProperties.unsignedProperties.unsignedDataObjectProperties[] | Collection|
xades.qualifyingProperties.unsignedProperties.unsignedDataObjectProperties[].unsignedDataObjectProperty | Text|

Only the **XAdES-B-B** form is supported.

#### Results

Property|Type|Description
------------|------|----
crypto | Text|crypto engine name `openssl`
success | Boolean|
error | Text|error message
xml | Text|signed XML

```
status:=xmlsec x509(cert;params)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">cert</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8">der, pem or p12</div>      
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">Object</div>
  <div class="syntax-td cell cell--8"></div>         
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">Object</div>
  <div class="syntax-td cell cell--8"></div>   
 </div>
 
 This is a convenience method to get the certificate expire date. 

#### Params

`*` indicates default value

Property|Type|Description
------------|------|----
cert | Text|format of certificate `pem*` `der` `pkcs12` 
password | Text|password to read pkcs12 

#### Results

Property|Type|Description
------------|------|----
success | Boolean|
notBefore | Text|
notAfter | Text|
