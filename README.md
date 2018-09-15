# html-to-sql
Extract word by word all important text and meta data from an html page.  Save billions of html pages in a structured way in a sql database so you can perform analysis on words and tags,  minimizing storage space required and maximizing performance and still be able to reconstruct the html page with the same text, including punctuation marks and tags. 

## Result
### Page
Specific page wide properties independent of words used:
* NoFollow: bool default false
* NoIndex: bool default false
* NoArchive: bool default false
* NoImageIndex: bool default false
* NoSnippet: bool default false
* Lang: string

### Links
Dictionary<string, string>: List of Uris with their LinkType

### Words
Object that stores all words, word by word, in order of appearance with their enclosed tags.
* *Word*: string cannot contain whitespace. It cannot contain punctuation marks except for hyphens and dots if they are immediatly followed by another character.  eg 
  * **M.A.S.H.**: M.A.S.H
  * **finished.**: finished 
  * **mother-in-law**: mother-in-law
  * **mother- and I**: mother
* PunctuationMarkBefore: nchar(1) string: if a punctuation mark proceeds the word, store it here (only the last)
* PunctuationMarkAfter: nchar(1) string: if a punctuation mark comes after the word, store it here (only the first)
* *TagH1*: bool: is enclosed in (parent) H1 tags
* *TagH2*: bool: is enclosed in (parent) H2 tags

## Data to extract
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
*Page.Lang* = content.

#### frame
* *src*: add to Links with type frame


### BODY
#### a
* *href*: add to Links with type a
* *rel=nofollow*: NoFollowLink=true
* *TagA*: true
  
#### area
* *href*: add to links with type area
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
* *src*: add to Links with type img
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






