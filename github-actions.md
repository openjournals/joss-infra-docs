# GitHub Actions

There is a collection of small GitHub actions available to be used as steps in the different workflows run by JOSS at GitHub.

The actions are:

* **publishing-artifacts-action** 
* **paper-action**
* **preprint-action**  
* **upload-files-action** 
* **deposit-pull-request-action** 
* **update-files-action** 
* **validate-xml-files-action** 
* **deposit-with-crossref-action** 
* **deposit-with-openjournals-action** 
* **citation-file-action** 
* **acceptance-tweet-action** 





```mermaid
flowchart TD
  PAPER(fa:fa-file-contract paper-action)
  PREPRINT(fa:fa-file preprint-action)
  ARTIFACTS(fa:fa-stream publishing-artifacts-action)
    
  Inara[(Inara)]    

  ARTIFACTS --> |compiles files using| Inara
  PAPER --> |Makes pdf, jats, crossref-xml, preprint, cff files available using| ARTIFACTS
  PREPRINT --> |Makes preprint file available using| ARTIFACTS
```

```mermaid
flowchart TD
  UPLOAD(fa:fa-code-branch upload-files-action)
  PR(fa:fa-code-merge deposit-pull-request-action)
  UPDATE(fa:fa-file-edit update-files-action)
   
  PapersRepo[JOSS Papers repository at GitHub]

  UPLOAD --> |New branch with metadata/image files| PapersRepo
  PR --> |Opens a pull request| PapersRepo
  UPDATE --> |Updates existing paper metadata/image files| PapersRepo
```

```mermaid
flowchart TD
  VALIDATE(fa:fa-file-check validate-xml-files-action)
   
  xml-validator[(The OJXV gem)]

  VALIDATE --> |Validates JATS/XML metadata files using| xml-validator
```

```mermaid
flowchart TD
  DEPOSIT-CROSSREF(fa:fa-cloud-upload deposit-with-crossref-action)
  DEPOSIT-OJ(fa:fa-file-upload deposit-with-openjournals-action)
  
  Openjournals[(TheOJ gem)]
  Crossref[(crossref.org API)]
    
  DEPOSIT-OJ --> |Deposit the paper to openjournals using| Openjournals
  DEPOSIT-CROSSREF --> |Deposit the crossref.xml file with| Crossref
```

```mermaid
flowchart TD
  CITATION-INFO(fa:fa-file-code citation-file-action)
   
  Review[fa:fa-github Review Issue at GitHub]
   
  CITATION-INFO --> |post the CITATION.cff file to| Review
```

```mermaid
flowchart TD
  ACCEPTANCE-TWEET(fa:fa-bullhorn acceptance-tweet-action)
  
  SocialMedia[(Twitter/Mastodor APIs)]
  
  ACCEPTANCE-TWEET --> |post to social media using| SocialMedia
```

    
