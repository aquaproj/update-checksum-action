# update-checksum-action

GitHub Actions to update aqua-checksums.json. If aqua-checksums.json isn't latest, update aqua-checksums.json and push a commit

About aqua's Checksum Verification, please see the document too.

https://aquaproj.github.io/docs/security/checksum

## Reusable Workflow

Please see [update-checksum-workflow](https://github.com/aquaproj/update-checksum-workflow).

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

## LICENSE

[MIT](LICENSE)
