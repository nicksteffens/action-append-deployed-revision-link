# action-append-deployed-revision-link
<p align="center">
  <a href="https://github.com/nicksteffens/action-append-deployed-revision-link/actions"><img alt="javscript-action status" src="https://github.com/nicksteffens/action-append-deployed-revision-link/workflows/units-test/badge.svg"></a>
</p>

`nicksteffens/action-append-deployed-revision-link` action is Javascript action that appends a provided package with revision number `[${packageName_revision=${revision}](${url}?${packageName}_revision=${revision})` to the PR description. The following scenarios are possible with this action:
1. Appends revision link if non exist
2. Updates the specific package's revision link if one exists
3. Allows for multiple packages.

*note: only 1 revision link per package is possible*

This action is inspired from [chabroA/action-append-pr-description](https://github.com/chabroA/action-append-pr-description). It was created for the purpose of using [ember-cli-deploy](http://ember-cli-deploy.com)
## Usage

```yaml
steps:
  - name: Add Revision Link to PR description
    uses: nicksteffens/action-append-deployed-revision-link@main
    with:
      auth: ${{ secrets.GITHUB_TOKEN }}
      repo: ${{ github.event.repository.name }}
      owner: ${{ github.repository_owner }}
      pr: ${{ github.event.number }}
      url: "https://my-url.test"
      packageName: "monorepo_package"
      revision: "commitSHA"
```

## Inputs

- `auth` - (required) A [GitHub Secret Token](https://docs.github.com/en/actions/reference/authentication-in-a-workflow) with access to the repository you want to update.

- `repo` - (required) The GitHub repository name containing the PR to update.

- `owner` - (required) The GitHub repository owner.

- `pr` - (required) The pull request number.

- `url` - (required) The url to append to the specified pull request description.

## License

[MIT](./dist/LICENSE.md)