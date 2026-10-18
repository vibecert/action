# VibeCert action

Posts a pull request's VibeCert badge, or a nudge to get one, as a comment.

The comment shows the branch's [VibeCert](https://l.martinchapman.co.uk/vibecert) badge when a certificate exists, with anything that makes it out of date.
When there is none but a commit credits a generative tool (a `Co-authored-by` trailer or a `Generated with` line), it encourages scoring the branch instead.
Otherwise nothing is posted, and one comment is updated on each push rather than a new one added.

## Usage

```yaml
on: pull_request
permissions:
  contents: read
  pull-requests: write
jobs:
  vibecert:
    runs-on: ubuntu-latest
    steps:
      - uses: vibecert/action@v1
```

Pull requests from forks get a read-only token, so commenting on them needs `pull_request_target` in place of `pull_request`.
The action only reads the checked-out branch, and never runs its code.

## Inputs

| Input | Default | |
| --- | --- | --- |
| `site-url` | `https://vibecert.github.io` | Where certificates are served from |
| `github-token` | `${{ github.token }}` | The token used to comment |
