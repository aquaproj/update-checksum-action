# update-checksum-action

GitHub Actions to update aqua-checksums.json. If aqua-checksums.json isn't latest, update aqua-checksums.json and push a commit

## Requirements

- [int128/ghcp](https://github.com/int128/ghcp)
- [aqua](https://aquaproj.github.io/)

## Example

https://github.com/aquaproj/example-update-checksum

```yaml
name: Update aqua-checksums.json
on:
  pull_request:
    branches: [main]
    paths:
      - aqua.yaml
      - aqua-checksums.json
env:
  AQUA_EXPERIMENTAL_CHECKSUM_VERIFICATION: "true" # https://aquaproj.github.io/docs/reference/checksum
permissions:
  contents: write # required to push a commit to update aqua-checksums.json
jobs:
  update-checksum:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      # Install aqua and int128/ghcp
      - uses: aquaproj/aqua-installer@v1.1.2
        with:
          aqua_version: v1.20.0-2

      # https://aquaproj.github.io/docs/reference/checksum
      - uses: aquaproj/update-checksum-action@main
        env:
          # To trigger GitHub Actions Workflow, you should use Personal Access Token or GitHub App token.
          GITHUB_TOKEN: ${{github.token}}
```

## Inputs

- `working_directory`

## Required Environment Variables

- `GITHUB_TOKEN`: GitHub Access Token. This is used to push a commit.

## Outputs

Nothing.

## LICENSE

[MIT](LICENSE)
