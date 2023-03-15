# vwt-ip-action-modules
These are actions which are used in our workflows. 
# Actions
### Brew and git action
##### Input parameters 
- git_token (this is a token required to allow data modules to be imported) 

##### Example of use brew and git
```yaml
  - name: Setup git token and brew
    id: brew_and_git
    uses: recognizegroup/vwt-ip-action-modules/.github/actions/brew_and_gittoken@{desired version}
    with:
      git_token: ${{ secrets.TEAM_ORANGE_GIT_TOKEN }}
```

### Terragrunt apply
##### Input parameters
- webhook (Webhook is used for notifying when terragrunt apply fails)
##### Example of use terragrunt apply

By the environement parameters you should set directory the     

 - TERRAGRUNT_DOWNLOAD:
 - TF_PLUGIN_CACHE_DIR

example with environment 

```yaml
env:
  TERRAGRUNT_DOWNLOAD: ${{ github.workspace }}/.terragrunt
  TF_PLUGIN_CACHE_DIR: ${{ github.workspace }}/.terragrunt/plugin-cache
```

Under steps add

```yaml
  - name: Terragrunt apply
    id: terragrunt_apply
    uses: recognizegroup/vwt-ip-action-modules/.github/actions/terragrunt_apply@{desired version}
    with:
      webhook: ${{ secrets.TEAMS_WEBHOOK_URL }}
      terragrunt_download_directory: $TERRAGRUNT_DOWNLOAD
      tf_plugin_directory: $TF_PLUGIN_CACHE_DIR
  ```

# Workflows

#### Pr title check

```yaml
name: PR Title Checker
on:
  pull_request:
    branches:
      - develop
    types:
      - opened
      - edited
      - synchronize

jobs:
  check-pr-title:
    uses: recognizegroup/vwt-ip-action-modules/.github/workflows/pull_request_title.yaml@{desired version}
```

