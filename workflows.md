# Workflows

This is a list of workflows [configured](https://github.com/openjournals/joss-papers/tree/master/.github/workflows) in the [JOSS papers repo](https://github.com/openjournals/joss-papers) that are triggered by the editorial bot.

* **[Accept](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/accept.yml)**

    This workflow is triggered by the `@editorialbot accept` command.

* **[Compile pdf](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/draft-paper.yml)**

    This workflow is triggered by the `@editorialbot generate pdf` command.

    * First it uses the [paper action](./github-actions.md#paper) to compile the pdf

    * Using the [upload-files action](./github-actions.md#upload-files) it pushes the paper.pdf file to a branch in the papers repo

    * And finally posts a comment to the original review issue with links to view or download the pdf file

* **[Preprint](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/preprint.yml)**

    This workflow is triggered by the `@editorialbot generate preprint` command.

    * First it uses the [preprint action](./github-actions.md#preprint) to generate a LaTeX file suitable to send to preprint archives and saves it as an artefact with a 24h expiration date.

    * Then it posts a comment to the original review issue with a link to the the page where the preprint file is located

* **[Re-accept](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/reaccept.yml)**

    This workflow is triggered by the `@editorialbot reaccept` command.

* **[Recommend acceptance](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/recommend-acceptance.yml)**

    This workflow is triggered by the `@editorialbot recommend-accept` command.

    * It uses the [paper action](./github-actions.md#paper) to compile the pdf and generate XML metadata files

    * The files are uploaded to a branch in the papers repo using the [upload-files action](./github-actions.md#upload-files)

    * And a pull request is open (using the [pull-request action](./github-actions.md#pull-request)) so the files can be easily inspected

    * Then the metadata files are validated with the [Validate-metadata-files action](./github-actions.md#validate-metadata-files)

    * If no problems are found with the files, a comment is posted to the original review issue with links to view the files and the issue is labeled as `recommend-accept`, otherwise a link to any error found is posted in a comment in the review issue