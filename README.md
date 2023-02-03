# update-checksum-action

GitHub Actions to update aqua-checksums.json. If aqua-checksums.json isn't latest, update aqua-checksums.json and push a commit

About aqua's Checksum Verification, please see the document too.

https://aquaproj.github.io/docs/reference/checksum

## Requirements

- [aqua](https://aquaproj.github.io/)
- [int128/ghcp](https://github.com/int128/ghcp): You can install ghcp with aqua (`aqua g -i int128/ghcp`)

```console
$ aqua init
$ aqua g -i int128/ghcp
```

## Example

[Workflow](https://github.com/aquaproj/example-update-checksum/blob/main/.github/workflows/test.yaml)

## Inputs

- `working_directory`
- `prune`
- `skip_push`

## Required Environment Variables

- `GITHUB_TOKEN`: GitHub Access Token. This is used to push a commit.

## Outputs

Nothing.

## Reusable Workflow

[Workflow](.github/workflows/update-checksum.yaml)

### Eample

```yaml
name: update-aqua-checksum
on:
  pull_request:
    paths:
      - aqua.yaml
      - aqua-checksums.json
jobs:
  update-aqua-checksums:
    needs: path-filter
    uses: aquaproj/update-checksum-action/.github/workflows/update-checksum.yaml@main
    permissions:
      contents: read
    with:
      aqua_policy_config: aqua-policy.yaml
      aqua_version: v1.32.3
    secrets:
      gh_app_id: ${{secrets.APP_ID}}
      gh_app_private_key: ${{secrets.APP_PRIVATE_KEY}}
```

## LICENSE

[MIT](LICENSE)
