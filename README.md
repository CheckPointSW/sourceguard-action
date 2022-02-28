
 
# Check Point SourceGuard
 <img src="logo.svg" align="left"/>
SourceGuard is designed to leverage Check Point's different prevention technologies and services, providing source-code security and visibility into the risk analysis of projects. With a simple, cross-platform CLI tool users can customize exclusions and control ignore list with easy integration to any pipeline.
 
## GitHub Integration
 
The following istruction would enable fast and simple integration to your GitHub repo using [GitHub Actions](https://docs.github.com/en/actions).
 
### Add To Repo
 
Add the following job to your workflow yml file under .github/workflows/
 
```
name: My Workflow
on: [push, pull_request]
jobs:
  …
  code-analysis:
    runs-on: ubuntu-latest
    container:
      image: sourceguard/sourceguard-cli
    steps:
      - name: SourceGuard Scan
        uses: chkp-roniz/sourceguard@main
        with:
          SG_CLIENT_ID: ${{ secrets.SG_CLIENT_ID }}
          SG_SECRET_KEY: ${{ secrets.SG_SECRET_KEY }}
…
 
```
 
### Create Secrets
 
SourceGuard action must recive:
 
- SG_CLIENT_ID - Infinity Portal account identification
- SG_SECRET_KEY - Secret key for access
 
To generate those parameters, refer to https://portal.checkpoint.com/dashboard/sourceguard#/config/install (select your requiered Tenant) > GENERATE TOKEN
 
Now, create those keys:
 
- Organiztaion Scope
  https://github.com/organizations/OrganizationName/settings/secrets/actions
- Repo Scope
  https://github.com/AccountName/RepoName/settings/secrets/actions
