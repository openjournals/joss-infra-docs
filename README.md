# JOSS Infrastructure Documentation

Find here information and help on how the Journal of Open Source Software infrastructure works



```mermaid
flowchart TD

  NEWPAPER([new paper])
  JOSS{{JOSS website}}
  REVIEW{Paper Review}
  BOT(EditorialBot)
  AUTHOR(Author)
  EDITOR(Editor)
  REVS(Reviewers)
  REJECT([paper rejected])
  WITHDRAW([paper withdrawn])
  ACCEPT([paper accepted])

  classDef oj fill:#738af4,stroke:#031568,stroke-width:4px,color:#fff;
  classDef rev fill:#f4e64e,stroke:#afa103,stroke-width:3px,color:#302c01;
  classDef red stroke:#e20606,stroke-width:2px;
  classDef green stroke:#20bc37,stroke-width:4px;
  classDef people stroke-dasharray: 5 5;


  NEWPAPER -.-> |new submission|JOSS
  JOSS:::oj --> |new GitHub issue|REVIEW
  BOT <--> REVIEW:::rev
  EDITOR <--> REVIEW
  REVS <--> REVIEW
  AUTHOR <--> REVIEW
  REVIEW -.-> ACCEPT:::green
  REVIEW -.-> REJECT:::red
  REVIEW -.-> WITHDRAW:::red
```

## Get started

- Flow of a paper submission
- Troubleshooting common errors


## Components


- [JOSS](./docs/joss.md)
- [Editorialbot](./docs/buffy.md)
- [Inara](./docs/inara.md)
- [Reviewers application](./docs/reviewers.md)
- [GitHub Actions](./docs/github-actions.md)
- [GitHub Workflows](./docs/workflows.md)
- [Ancillary Ruby gems](./docs/gems.md)

