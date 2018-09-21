# html-to-sql
Extract word by word all important text and meta data from an html page.  Save billions of html pages in a structured way in a sql database so you can perform analysis on words and tags,  minimizing storage space required and maximizing performance and still be able to reconstruct the html page with the same text, including punctuation marks and tags. 



## Extracted Data
An example can be found in [htmlexample.html] (htmlexample.html)

### HEAD
#### base
* *href*: add to Links with Type base. Use only the first one (if there are multiple). 
#### title
* *TagTitle*: true
#### meta description
* *TagMetaDescription*: true
#### meta keywords
* *TagMetaKeywords*:true
#### meta http-equiv
< meta http-equiv="refresh" content="30;URL=http://www.keyboost.com" >: add to Links with Type http-equiv
#### meta robots
< meta name="robots" content="noindex, nofollow" >: sets page properties depending on content:
* *noindex*: Page.NoIndex=true
* *nofollow*: Page.NoFollow=true
* *noarchive*: Page.NoArchive=true
* *none*: Page.NoIndex=true & Page.NoFollow=true
* *nosnippet*: Page.NoSnippet=true
* *nocache*: Page.NoArchive=true
#### meta language or language-content
< meta name="language" content="en" >
< meta name="language-content" content="en" >
*Page.Lang* = content

#### frame
* *src*: add to Links with type frame


### BODY
#### a
* *href*: add to Links with type a and to Word.href
* *rel=nofollow*: NoFollowLink=true
* *TagA*: true
  
#### area
* *href*: add to links with type area and to Word.href
* *rel=nofollow*: NoFollowLink=true
* *TagArea*: true

#### b
* *TagBold*: true
  

  
#### big
* *TagBig*: true
  
#### button
* *TagButton*: true
  
#### del
* *TagDel*: true
  
#### dfn
* *TagDfn*: true
  
#### em
* *TagEm*: true

#### h1 - h6
* *TagH[1-6]*:true
#### html
* *lang*: Page.Lang
#### i
* *TagI*:true
#### iframe
* *src*: Add to Links with type iframe
  
#### img
* *src*: add to Links with type img and to Word.Href
* *Alt*: TagImgAlt=true

#### ins
* *TagIns*: true

#### link
< link rel="canonical" href="http://www.seopageoptimizer.com/" />
* *canonical*: Add to Links with type canonical 

#### mark
* *TagMark*: true

#### optgroup
* *label*: TagOptGroup=true
#### option
* *value*: TagOption=true
#### small
* *TagSmall*:true
#### strike
* *TagStrike*:true
#### strong
* *TagStrong*:true
#### sub
* *TagSub*:true
#### sup
* *TagSup*:true
#### u
* *TagU*:true

## Result
The expected results of  [htmlexample.html] (htmlexample.html) can be found in [resultsexample.xlsx] (resultsexpample.xlsx)

### Page
Specific page wide properties independent of words used:
* NoFollow: bool default false
* NoIndex: bool default false
* NoArchive: bool default false
* NoImageIndex: bool default false
* NoSnippet: bool default false
* Lang: string
* Country: string

### Links
Dictionary<string, string>: List of urls found with their LinkType
* LinkTypes:
  * base
  * http-equiv
  * frame
  * iframe
  * a
  * area
  * canonical
  * img
* NoFollow: bool: true if attribute rel=nofollow is found. 

### Words
Object that stores all words, word by word, in order of appearance with their enclosed tags.
* *Word*: string cannot contain whitespace. It cannot contain punctuation marks except for hyphens and dots if they are immediatly followed by another character.  eg 
  * **M.A.S.H.**: M.A.S.H
  * **finished.**: finished 
  * **mother-in-law**: mother-in-law
  * **mother- and I**: mother
* *PunctuationMarkBefore*: nchar(1) string: if a punctuation mark proceeds the word, store it here (only the last)
* *PunctuationMarkAfter*: nchar(1) string: if a punctuation mark comes after the word, store it here (only the first)
* *FirstLetterUppercase*: bool: true if the first letter of the word is in uppercase.
* *AllInUpperCase*: bool: true if all letters of the word are in uppercase
* *TagTitle*: bool: is enclosed in the head title tag
* *TagMetaDescription*: bool: is enclosed in the meta tag
* *TagMetaKeywords*: bool: is enclosed in the meta tag
* *TagA*: bool: is enclosed in (parent) A tag
* *Href*: string: stores the href of A tags, AREA tags
* *TagArea*: bool: is enclosed in (parent) AREA tag
* *TagH1*: bool: is enclosed in (parent) H1 tag
* *TagH2*: bool: is enclosed in (parent) H2 tag
* *TagH3*: bool: is enclosed in (parent) H3 tag
* *TagH4*: bool: is enclosed in (parent) H4 tag
* *TagH5*: bool: is enclosed in (parent) H5 tag
* *TagH6*: bool: is enclosed in (parent) H6 tag
* *TagB*: bool: is enclosed in (parent) B tag
* ... (see Extracted Data for all tags)
* *isHidden*: bool: if text is hidden, this should be true
  * css display:none
  * css display:hidden
* *Lang*: if a tag contains an attribute lang, this should be the lang part.
* *Country*: if a tag contains an attribute lang, this should be the country part (if exists).








