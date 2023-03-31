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

* **[Re-accept](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/reaccept.yml)**

    This workflow is triggered by the `@editorialbot reaccept` command.

* **[Recommend acceptance](https://github.com/openjournals/joss-papers/blob/master/.github/workflows/recommend-acceptance.yml)**

    This workflow is triggered by the `@editorialbot recommend-accept` command.

