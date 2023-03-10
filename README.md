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
    uses: recognizegroup/vwt-ip-action-modules/.github/actions/brew_and_gittoken@{laterst  release version}
    with:
      git_token: ${{ secrets.TEAM_ORANGE_GIT_TOKEN }}
```

### Terragrunt apply
##### Input parameters
- webhook (Webhook is used for notifying when terragrunt apply fails)
##### Example of use terragrunt apply
```yaml
  - name: Terragrunt apply
    id: terragrunt_apply
    uses: recognizegroup/vwt-ip-action-modules/.github/actions/terragrunt_apply@{laterst  release version}
    with:
      webhook: ${{ secrets.TEAMS_WEBHOOK_URL }}
  ```

# Workflows