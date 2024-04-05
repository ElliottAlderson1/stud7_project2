### Initialize a new project
- Select User, Group, Visibility, add a README, like GitHub

### Set up organization
- Namespaces
  1. Personal - based upon your username
  2. Group/Subgroup
- Members
  - Assign Roles: Owner & Maintainer
- Groups
  - Group visibility
- User Account

### User Account
 - Select your avatar
 - Select name or username
 - Edit settings under edit profile
 - You can add email to account
- Create Tokens, only can see it on the page you created, it's gone after.
### Project Details
- Project Name
  - Must start with lowercase or uppercase letter, digit, emoji, underscore
  - can contain dots, pluses, or dashes
- Project URL
- Project Slug
- Project deployment target (Optional)
- Visibility Level
- Project Configuration

## Create Issues
Used to summarize to align team on goals. Can label them. 
- Must be at least a Guest to the project
- You can auto close an issue using words like 'close'
- Can create from: a project, a group, another issue (will mark the two issues as related)
- To close you must be at least the Reporter role, author of issue, or assigned to issue.

## Create Milestones
- Define at lowest level needed
- Keep track of issues and merge requests

### Track Issues
Shows all issues to milestones in three categories:
1. `un-started` open and unassigned
2. `ongoing` open and assigned
3. `completed issues` closed


#### Columns Shows all merge requests assigned to milestone at four levels: 
1. `Work in Progress` open and unassigned 
2. `Waiting for Merge` open and assigned
3. `Rejected` closed
4. `Merged`

You **DON'T** want to delete source branch when merge is completed.
## Issue Boards
### Track Issues
Use issue board as scrum board or Kanban.
Sort by blocks, create date, due dates, label priority, updated date.
### Labels

# Lab 02 Project management with GitLab
Create a project under the `menu` button. Labels are created under the left tab under `project information`. Create a 'milestone' under the 'Issues' in the left column.

### Creating Issues
Create issues, assign `assignee`, `milestone, `weight` and more. You can then assign and more under the 'milestone' tab they are assigned to.


### Board Modification
You can make boards show issues for certain milestones only under the `edit` menu. You can also add `new list`. You cab set a permanent issue filter by searching it, then `edit board` to add.

### Deleting Project
Deleting project is hidden under advanced.

# Lab 03 Intro to Version Control
Use the `commits` tab to see history. It also lets you select branches here. You can select the branch right on the files page. `Graph` aslo shows you various branches in relations to commits.

### Merge Requests
Make sure to uncheck `delete source` when merging. View changes at bottom next to `create merge request` button to see changes.

Once made the merge request will have three tabs:
1. `overview` see comments to the merge request, and also execute the merge
2. `commits`  all commits associated with this merge request
3. `changes` all specific changes to a file as a result of the merge. Additions are displayed in green, and deletions in red

