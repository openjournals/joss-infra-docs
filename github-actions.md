# GitHub Actions

There is a collection of small GitHub actions available to be used as steps in the different workflows run by JOSS at GitHub.

The actions are:

* **[publishing-artifacts-action](https://github.com/xuanxu/publishing-artifacts-action)**

    This action compiles a given paper.md markdown file and can generate PDF, JATS, Crossref XML, preprint and cff files.
    Under the hood it uses the [openjournals/inara action](https://github.com/openjournals/inara) to generate the output files.

* **[paper-action](https://github.com/xuanxu/paper-action)**

    This action looks for a `paper.md` file in the specified repository and uses it to compile a Open Journals paper, generating PDF, Crossref XML, JATS and CFF outputs using the publishing artifacts action.

* **[preprint-action](https://github.com/xuanxu/preprint-action)**

    This action looks for a paper.md file in the specified repository and uses it to generate (using the publishing artifacts action) a simple LaTeX file suitable to send to preprint archives.

* **[upload-files-action](https://github.com/xuanxu/upload-files-action)**

    This action creates a topic branch for a paper in the corresponding Open Journal's papers repository and adds the paper files (pdf/jats/crossref xml) to it.

* **[deposit-pull-request-action](https://github.com/xuanxu/deposit-pull-request-action)**

    This action opens a pull request for an accepted paper and optionally merges it

* **[update-files-action](https://github.com/xuanxu/update-files-action)**

    This action creates a topic branch in the corresponding Open Journal's papers repository and updates the published paper files (pdf/jats/crossref xml).

* **[validate-xml-files-action](https://github.com/xuanxu/validate-xml-files-action)**

    This action validates Open Journals' JATS and Crossref XML files. If an error happens it sends back a message to the review issue.

* **[deposit-with-openjournals-action](https://github.com/xuanxu/deposit-with-openjournals-action)**

    This action deposit an accepted paper with Open Journals

* **[deposit-with-crossref-action](https://github.com/xuanxu/deposit-with-crossref-action)**

    This action deposit an accepted paper with [Crossref](https://www.crossref.org/)

* **[citation-file-action](https://github.com/xuanxu/citation-file-action)**

    This action comments in the review issue with the contents of a CITATION.cff file.

* **[acceptance-tweet-action](https://github.com/xuanxu/acceptance-tweet-action)**

    This action creates a tweet and/or a toot announcing the acceptance of a paper.



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

    
