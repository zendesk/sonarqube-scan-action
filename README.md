# Disclaimer
This is a Zendesk maintained repository cloned from [SonarSource/sonarqube-scan-action](https://github.com/SonarSource/sonarqube-scan-action). This repository is not updated from upstream master branch, instead it is updated from the latest tag from the SonarSource/sonarqube-scan-action.

# Current Rebase
The code is currently rebased with tag `v5.3.1`

## Recommended Use within Zendesk
It is exepected that the Zendesk teams to use `sonarqube-scan-action` like below:
```
 - name: SonarQube Scan
        uses: zendesk/sonarqube-scan-action@master
        env:
          SONAR_TOKEN: ${{ secrets.SONARQUBE_TOKEN }}
          SONAR_HOST_URL: ${{ secrets.SONARQUBE_HOST }}
```
## How to update the repository to latest tag from upstream
We should never update from the upstream `master` branch, instead we should force rebase from the upstream latest tag. Follow the steps below to rebase this repository:

- Add upstream (Note: This is needed once during local setup)
```
git remote add upstream git@github.com:SonarSource/sonarqube-scan-action.git
```
- Fetch all tags from upstream
```
git fetch upstream --tags
```
- Pick the latest tag
- Create an update branch
```
git checkout -b "<username>/<jira_issue_id>-update-to-tag-<target_tag_name>”
```
- Reset to target tag
```
git reset --hard <target_tag_name>
```
- Delete the workflow folder(as tests are already performed in upstream and we are rebasing with a tagged release)
```
rm -rf .github/workflows
```
- Update this README.md file with the current target tag under Current Rebase section.

- Push the changes
```
git push origin <username>/<jira_issue_id>-update-to-tag-<target_tag_name> --force-with-lease
```
- Create a PR to merge with the `master` branch of `zendesk/sonarqube-scan-action`

- Request `test-infra` team to review and merge the PR

## Upstream Details
For details check upstream [README.md](https://github.com/SonarSource/sonarqube-scan-action/blob/master/README.md)