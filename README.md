 <h2 align="center">   
  <img src="https://github.com/Upbrainery-Technology/template-repo-AWS/assets/85288256/09ad0457-b8ee-4ab9-9a02-534cdefff5c0" alt="[Arthur Lawrence](https://github.com/Upbrainery-Technology)" width="500" height="92.11">
 <h2/>
  
# Template-repository
This will be the template repository and will be used for creating all the repositories in this organization. 

  - .github file will have all the rules defined
  - pull_request_template will be added.
  - mergeable.yml will have all the checks defined and will be running via [Mergeable app]
  - Compass will be connected to each repository, and compass.yml file will be added.
  - By default, master branch will be created and then other branches can be created; develop, stage etc.
 
  ---
  
### Branch Naming Convention on GitHub
- The branch naming conventions must be followed as:
```jsx
<keyword>/<JIRA_ID>-<developer signature>
```
- Keywords will be feature, bugfix, hotfix, build. (explained below)
- The signature can be the initials of your name, e.g. Ammar Ahmed Butt - AAB.
- JIRA_ID will be the ticket ID, i.e. JIRA-00, TPM-12 etc.

#### Feature Branches

- For new modules, features should be created from develop branch. This branch should be merged back into development once the feature is finished and the branch should be removed if delivered. 'feature/JIRA-1001-IL'

#### Bug fixes

- When a developer needs to fix a bug, this should be created from develop or release branch. This branch should not be called hotfix to avoid confusion with hotfixes done on production. Once it is merged with the branch it was created from this should be removed.  'bugfix/JIRA-1001-IL'

#### Hotfix

- When an important issue is found on production and this needs to be addressed immediately, a hotfix branch has to be created from the master branch. Once these are merged to master, develop, and stage branches, it has to be removed. Hotfixes should be immediately merged to existing branches develop, stage, and master to avoid conflicts.
- If merge to develop/staging is forgotten we may merge/release the bug in the future to the master branch. 'hotfix/JIRA-1001-IL'

#### Build Branch

- For build artifacts and configurations changes. 'build/JIRA-1001-IL'
 
#### Environment Branches

- These will be the main branches that will trigger the AWS Codebuild and CodePipeline via [webhook]
  - Upon merging the PR the pipeline trigger can be set, just choose PULL_REQUEST_MERGED and start the build under Head_Ref - refs/heads/branch-name
- Here branch names will be *develop* , *stage* & *master* .
  
  ![254796324-8aa8d968-4668-40b9-a291-6eb6b5cd0f8a](https://github.com/arthurlawrence-org/template-repo-AWS-master/assets/85288256/3e46dcf4-7ec3-457e-87c1-0c89abae5bab)
  

##### CodePipeline Naming Convention (AWS)

- ENV_Repo
  - ENV = Branch name
  - Repo = Repository name
- For example
  - develop_AL_BE  (this means that its branch and environment is develop and AL = Arthur Lawrence Product and BE = Backend)
  - stage_AL_BE  (this means that its branch and environment is stage and AL = Arthur Lawrence and BE = Backend)
  - master_AL_BE  (this means that its branch and environment is master and AL = Arthur Lawrence and BE = Backend)
- Use the name of the Environment branch, as per the naming convention explained here.
- Use the name of the Repository, as per the naming convention explained here. e.g. Techverx_BE, Techverx_FE etc.

### Commits - Standards

- Validates if commits are following Conventions or not. - [Conventional-commits]
- Checks the Commit message 
- Following checks are in place using [Mergable-Bot] to ensure commit standards are being met,

 ✅ Start with <type> such as build:, chore:, ci:, docs:, feat:, fix:, perf:, refactor:, revert:, update:, create:, style:, test: .
 
 ✅ Limit the subject line to 72 characters
 
 ✅ Use lowercase in the subject line
 
 ✅ Do not end the subject line with a period.
 
 ✅ Add Ticket id i.e. JIRA-00 in the description, so that all tickets can be tracked. 

#### Sample Commit 
```jsx
fix: summarize the fix in less than 72 characters JIRA-1337
BREAKING CHANGES: ticket endpoints no longer support the list of all entities.
```

## Pull Requests Standards

### Creating a Pull Request
Following checks should be followed to ensure PR standards are being met.

- Subject: Include <JIRA-ID><colon><space><message> e.g. JUB-85: new product added
- Summarize PR in less than 50 characters
  
Description:
- Describe what was done and why, but not how
- Include any testing details done
- Include any additional notes, relevant links, or co-authors
- Wrap the body at 72 characters

#### Sample PR

```jsx
Title
[JIRA-ID]: Summarize PR in less than 50 characters
JUB-85: new product added

Description
- Describe what was done and why, but not how
- Include any testing details done
- Include any additional notes, relevant links, or co-authors
- Make a new bullet for each reason
- Wrap the body at 72 characters
```

#### GitHub & Jira Automation 
- It will work if jira ID is mentioned in the Commits and PR.
- Tickets will move automatically.
- [Smart-Commits] - Check this link, one can log time as well, while pushing the code at the day-end.
- Jira workflow, according to the number of environments

![254830681-75334628-d025-44d2-a8db-7ccbccd01362](https://github.com/arthurlawrence-org/template-repo-AWS-master/assets/85288256/b5135522-a521-406d-920e-044a99a57c1b)


[Mergable-Bot]: https://github.com/apps/mergeable
[webhook]: https://docs.aws.amazon.com/codebuild/latest/userguide/github-webhook.html
[Conventional-commits]: https://www.conventionalcommits.org/en/v1.0.0/
[Smart-Commits]: https://support.atlassian.com/jira-software-cloud/docs/process-issues-with-smart-commits/
