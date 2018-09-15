# html-to-sql
Extract word by word all important text and meta data from an html page.  Save billions of html pages in a structured way in a sql database so you can perform analysis on words and tags,  minimizing storage space required and maximizing performance and still be able to reconstruct the html page with the same text, including punctuation marks and tags. 

## Result

## Data to extract
### HEAD
#### base
*href*: url: should be added to every other href string when relative. Use only the first one (if there are multiple). 
#### title
*TagTitle*: true
#### description
*TagMetaDescription*: true
#### keywords
*TagMetaKeywords*:true
#### http redirect
< meta http-equiv="refresh" content="30;URL=http://www.keyboost.com" >

### BODY
#### a
*href*: string

*rel=nofollow*: NoFollowLink=true

*TagA*: true
  
#### area
*href*: string

*rel=nofollow*: NoFollowLink=true

*TagArea*: true

#### b
*TagBold*: true
  

  
#### big
*TagBig*: true
  
#### button
*TagButton*: true
  
#### del
*TagDel*: true
  
#### dfn
*TagDfn*: true
  
  #### em
*TagEm*: true

#### h1 - h6
*TagH[1-6]*:true

#### i
*TagI*:true
  
#### img
*Alt*: TagImgAlt=true

#### ins
*TagIns*: true

#### mark
*TagMark*: true





