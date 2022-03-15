# Check Point SourceGuard
 <img src="logo.svg" align="left"/>
SourceGuard is designed to leverage Check Point's varied prevention technologies and services, providing source-code security and visibility. With a simple, cross-platform CLI tool users can customize exclusions and control an ignore list with easy integration into any pipeline.
 
## GitHub Integration
 
The following instructions would help you to perform a fast and simple integration to your GitHub repo workflow actions using [GitHub Actions](https://docs.github.com/en/actions).
 
### Add To Repo
 
Add this job to your workflow yml file under .github/workflows/
 
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
        uses: CheckPointSW/sourceguard@main
        with:
          SG_CLIENT_ID: ${{ secrets.SG_CLIENT_ID }}
          SG_SECRET_KEY: ${{ secrets.SG_SECRET_KEY }}
…
 
```
 
### Create Secrets
 
SourceGuard action must recive:
 
- SG_CLIENT_ID - Infinity Portal account identification
- SG_SECRET_KEY - Secret key for access
 
To generate these parameters, refer to https://portal.checkpoint.com/dashboard/sourceguard#/config/install (select your required Tenant) > GENERATE TOKEN
 
Now, create these keys:
 
- Organiztaion Scope
  https://github.com/organizations/OrganizationName/settings/secrets/actions
- Repo Scope
  https://github.com/AccountName/RepoName/settings/secrets/actions
