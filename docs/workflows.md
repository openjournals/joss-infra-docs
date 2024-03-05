# Workflows

This is a list of workflows [configured](https://github.com/openjournals/joss-papers/tree/master/.github/workflows) in the [JOSS papers repo](https://github.com/openjournals/joss-papers) that are triggered by the editorial bot.

### **[Accept](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/accept.yml)**

  This workflow is triggered by the `@editorialbot accept` command.

  * It uses the [paper action](./github-actions.md#paper) to compile the pdf and generate XML metadata files

  * The files are uploaded to a branch in the papers repo using the [upload-files action](./github-actions.md#upload-files)

  * Then the metadata files are validated with the [validate-metadata-files action](./github-actions.md#validate-metadata-files)

  * If files are valid a pull request is created and merged (using the [pull-request action](./github-actions.md#pull-request)) in the papers repo

  * The paper is deposited with Crossref (using the [deposit-with-crossref action](./github-actions.md#deposit-with-crossref)) and with JOSS (using the [deposit-with-openjournals action](./github-actions.md#deposit-with-open-journals))

  * The [citation-file action](./github-actions.md#citation-file) creates a CITATION.cff file that is posted to the review issue

  * The paper publication is announced in Twitter and Mastodon using the [social-media-posts action](./github-actions.md#acceptance-social-media-posts)

  * A comment is posted in the review issue linking the papers and announcing the acceptance of the paper and the issue is labeled as `accepted` and `published`

### **[Repository and paper info](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/checks.yml)**

This workflow is triggered by the `@editorialbot check repository` command, and is also triggered automatically when a new `review` or `pre preview` issue is created.

  * It uses the [repository-and-paper-checks action](./github-actions.md#repository-and-paper-checks) to run checks on the submitted software repository and paper file

  * It labels the issue with the more used languages of the software repository

  * Then post back comments with info on the software authors and file types, on the license of the submitted software and on the length of the paper file and the presence of a _Statement of need_ section in it

### **[Compile pdf](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/draft-paper.yml)**

  This workflow is triggered by the `@editorialbot generate pdf` command.

  * First it uses the [paper action](./github-actions.md#paper) to compile the pdf

  * Using the [upload-files action](./github-actions.md#upload-files) it pushes the paper.pdf file to a branch in the papers repo

  * And finally posts a comment to the original review issue with links to _view_ and _download_ the pdf file

### **[Preprint](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/preprint.yml)**

  This workflow is triggered by the `@editorialbot generate preprint` command.

  * First it uses the [preprint action](./github-actions.md#preprint) to generate a LaTeX file suitable to send to preprint archives and saves it as an artefact with a 24h expiration date.

  * Then it posts a comment to the original review issue with a link to the the page where the preprint file is located

### **[Re-accept](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/reaccept.yml)**

  This workflow is triggered by the `@editorialbot reaccept` command.

  * It uses the [paper action](./github-actions.md#paper) to compile the pdf and generate XML metadata files

  * The updated files are uploaded to a branch in the papers repo using the [update-files action](./github-actions.md#update-files)

  * Then the metadata files are validated with the [validate-metadata-files action](./github-actions.md#validate-metadata-files)

  * If files are valid a pull request is created and merged (using the [pull-request action](./github-actions.md#pull-request)) in the papers repo

  * The paper is deposited with Crossref (using the [deposit-with-crossref action](./github-actions.md#deposit-with-crossref)) and with JOSS (using the [deposit-with-openjournals action](./github-actions.md#deposit-with-open-journals))

  * A comment is posted in the review issue linking to the updated paper files


### **[Recommend acceptance](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/recommend-acceptance.yml)**

  This workflow is triggered by the `@editorialbot recommend-accept` command.

  * It uses the [paper action](./github-actions.md#paper) to compile the pdf and generate XML metadata files

  * The files are uploaded to a branch in the papers repo using the [upload-files action](./github-actions.md#upload-files)

  * And a pull request is open (using the [pull-request action](./github-actions.md#pull-request)) so the files can be easily inspected

  * Then the metadata files are validated with the [validate-metadata-files action](./github-actions.md#validate-metadata-files)

  * If no problems are found with the files, a comment is posted to the original review issue with links to view the files and the issue is labeled as `recommend-accept`, otherwise a link to any error found is posted in a comment in the review issue

### **[Check bibtex references ](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/references.yml)**

This workflow is triggered by the `@editorialbot check references` command, and is also triggered automatically when a new `review` or `pre preview` issue is created.

  * It uses the [check-references action](./github-actions.md#check-references) to check the validity of the DOIs listed in the `.bib`file containing the bibliographic references the a paper submitted for review.

  * It posts an error comment if no `.bib` file is found

  * It posts a comment to the original issue with a list of valid/invalid/missing DOIs

### **[Retract paper](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/retract.yml)**

  This workflow is meant to be triggered manually. It requires as input the review issue number of the paper to be retracted and the URL of the markdown file containing the retraction notice text. It can be run in draft or in final mode.

  * It uses the [retraction action](./github-actions.md#retraction) to compile the pdf, generate XML metadata files and optionally accept the retracion notice.

  * Draft mode will generate a zip with pdf, jats and crossref files for the retraction notice and save it as an artefact with a 24h expiration date.

  * Final mode will also merge the files into the `joss-papers` repository and deposit the retraction with JOSS and [with Crossref](./github-actions.md#deposit-with-crossref).


## Secrets

For the workflows to work some values are added to the repo settings in the actions secrets section:

```
To allow the bot to interact with the JOSS reviews and JOSS site:

BOT_TOKEN
JOSS_SECRET

For Crossref depositing:

CROSSREF_USERNAME
CROSSREF_PASSWORD

To post to Mastodon:

MASTODON_ACCESS_TOKEN
MASTODON_INSTANCE_URL
MASTODON_USER

To post to Twitter:

TWITTER_ACCESS_TOKEN
TWITTER_ACCESS_TOKEN_SECRET
TWITTER_CONSUMER_KEY
TWITTER_CONSUMER_SECRET

```
