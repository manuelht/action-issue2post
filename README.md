# turn-issues-to-posts-action

Github action which turn issues into post markdown files

## Usage

add `.github/workflows/main.yml` with following content:

```yaml
name: generate my blog posts
on:
  issues:
    types: [opened, edited]
jobs:
  run:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - uses: manuelht/action-issue2post
        with:
          branch: "master" # default to master
          dir: "_posts" # default to _posts
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          created_at: ${{ github.event.issue.created_at }}
          title: ${{ github.event.issue.title }}
          body: ${{ github.event.issue.body }}
          actor: ${{ github.actor }}
```
