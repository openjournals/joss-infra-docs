# Ruby gems

This is a collection of simple Ruby gems developed to help in some specific step of the Open Journal's paper submission process.

## TheOJ: The Open Journals gem

`theoj` is a library to manage editorial objects (journal/paper/review_issues/submission) during the review process. It is used by almost every workflow run by the editorial bot to interact with the JOSS website.

Source code: https://github.com/xuanxu/theoj

## OJXV: The Open Journals XML validator gem

`OJXV` is a small library used in the acceptance/re-acceptance/recommend-acceptance workflows to validate the format of some Open Journals' publishing pipeline XML outputs (JATS and Crossref).

Source code: https://github.com/xuanxu/ojxv

## Issue

`Issue` is a small library dedicated to parse requests coming from GitHub webhooks triggered by issues, issue_comment and pull_request events. It is used in the editorial bot and in the JOSS application code to listen to the configured GitHub webhooks.

Source code: https://github.com/xuanxu/issue

##  OJRA: Open Journals Reviewers API

`OJRA` is a Ruby wrapper for the Open Journal's Reviewers application's API. It is used by a couple of responders in the editorial bot code to keep in sync the number of active/total reviews of every reviewer when a new submission assigment starts or finishes.

Source code: https://github.com/xuanxu/ojra
