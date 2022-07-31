<!-- start title -->

# gitgitgadget Action: check-status

<!-- end title -->
<!-- start description -->

This is a GitHub action to perform various scheduled actions with projects using gitgitgadget to submit changes. It is used as a scheduled action running in a separate repo or the repo it is acting upon. The use case is for repos that will not allow complex GitHub actions in the codebase when the GitHub repo is a clone that is used to submit updates to a non-GitHub maintained repo.

<!-- end description -->
<!-- start contents -->
<!-- end contents -->

## Usage

<!-- start usage -->

```yaml
- uses: gitgitgadget/check-status@v0.5.0
  with:
    # The action to be performed. It must be one of the following: "update-open-prs",
    # "update-commit-mappings", "handle-open-prs", "handle-new-mails".
    action: ""

    # Repository owner.
    repo-owner: ""

    # Repository name.
    repo-name: ""

    # A repo scoped GitHub Personal Access Token.
    token: ""

    # The location of the repository.
    repository-dir: ""

    # The location of the repository with gitgitgadget configuration information. This
    # would be used in place of the `config` parameter for the `git` repository. This
    # is normally the gitgitgadget repo with any needed configuration settings. Most
    # users will specify a `config`.
    config-repository-dir: ""

    # JSON configuration for commands.
    config: ""
```

<!-- end usage -->

## Inputs

<!-- start inputs -->

| **Input**                   | **Description**                                                                                                                                                                                                                                                                | **Default** | **Required** |
| :-------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------: | :----------: |
| **`action`**                | The action to be performed. It must be one of the following: "update-open-prs", "update-commit-mappings", "handle-open-prs", "handle-new-mails".                                                                                                                               |             |   **true**   |
| **`repo-owner`**            | Repository owner.                                                                                                                                                                                                                                                              |             |   **true**   |
| **`repo-name`**             | Repository name.                                                                                                                                                                                                                                                               |             |   **true**   |
| **`token`**                 | A repo scoped GitHub Personal Access Token.                                                                                                                                                                                                                                    |             |   **true**   |
| **`repository-dir`**        | The location of the repository.                                                                                                                                                                                                                                                |             |   **true**   |
| **`config-repository-dir`** | The location of the repository with gitgitgadget configuration information. This would be used in place of the `config` parameter for the `git` repository. This is normally the gitgitgadget repo with any needed configuration settings. Most users will specify a `config`. |             |  **false**   |
| **`config`**                | JSON configuration for commands.                                                                                                                                                                                                                                               |             |   **true**   |

<!-- end inputs -->
<!-- start outputs -->
<!-- end outputs -->
<!-- start [.github/ghdocs/examples/] -->
<!-- end [.github/ghdocs/examples/] -->

## Contributing

### Environment

The rebuild of this document (README.md) expects a `docker`
command is available from the command line.

### Building

#### action.yml changes

Changes to `action.yml` require rebuilding the `README.md`. This is done
using `npm run build:readme`. **Note**: markup is very limited in the
`action.yml`.

#### Source changes

Code changes are built using `npm run build`. This builds a new action in the
`dist` directory.

### Testing

The action supports four different checks. The checks and associated npm
commands are:

- update-open-prs (test:upr)
- update-commit-mappings (test:ucm)
- handle-open-prs (test:hop)
- handle-new-mails (test:hnm)

A windows command is provided for testing. It requires:

1. A test repo set up to be monitored. A GitHub PAT must already be set as
   the INPUT_TOKEN environment variable or indentifed in a `.secret` file in
   the repo. The format of the `.secret` file is `INPUT_TOKEN=<pat>`.
2. A config describing the test repo.
3. For testing mail checks, a mail repo must be available with valid email.

The test is run using the command:

```
npm run <test-name> <test-repo-owner> <test-repo-name> <config-location> <email-repo-location>
```
