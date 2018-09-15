# html-to-sql
Extract word by word all text and meta data from an html page.  Save billions of html pages in a structured way in a sql database so you can perform analysis on words and tags,  minimizing storage space required and maximizing performance and still be able to reconstruct the html page with the same text, including punctuation marks and tags. 

## Goal
Extract word by word all words and meta data from an html page.  We want to save billions of html pages in a structured way in a sql database so we can perform analysis on words and tags,  to minimize the storage space required and maximize performance and still be able to reconstruct the html page with the same text, including punctuation marks and tags. 
Expected Result

## Data to extract

### Tags
#### <a>
*href*: string
*rel=nofollow*: NoFollowLink=true
*TagA*: true
#### <area>
*href*: string
*rel=nofollow*: NoFollowLink=true
*TagArea*: true
#### <b>
TagBold=true
#### <base> 
Href: string url: should be extracted as first and added to every other href string when relative. Use only when in <head> tag and the first one (if there are multiple). 
#### <big>
TagBig=true
#### <button>
TagButton=true
#### <del>
TagDel=true
#### <dfn>
TagDfn=true
#### <h1> - <h6>
TagHx=true
#### <i>
TagI=true
#### <img>
Text in Alt: TagImgAlt=true
