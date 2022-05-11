---
order: 9
---
# Project Setup

## Creating a new Project
!!!info Existing Projects
If a project for the year already exists, please clone the repo from github rather than creating a new project. 
!!!
1. Open WPILib VSCode
2. Click the 'W' icon in the top right corner.
3. Choose Create New Project from the dropdown menu.
4. Click select project type
5. Choose Template > Java > Command Robot
6. Choose a location on your hard drive to create the project
7. Give the project a name. The recommended name is `4733 FRC {YEAR}`, where `{YEAR}` is the current year.
8. Click generate project.

## Acquiring an Existing Project from Github
!!!warning Github Organization
You must be in the ScarlettRobotics Github organization to clone and contribute to the codebase. If you are not part of the organization, talk to the head of the code team to be added.
!!!
### Using VSCode's Git Client
1. Open WPILib VSCode
2. Click the git tab on the left
3. Click the clone button
4. Choose Clone from Github in the dropdown menu.
    a. If asked to sign in, sign in with your github account.
5. Choose this years project repository from the list.

### Using Github Desktop
1. Open Github Desktop
2. Choose File > Clone Repository
3. Choose this years project repository from the list.

### Using Git CLI
1. Open a terminal window.
2. Find the URL of the git repository for this year's project.
3. Clone the repository.
```bash
$ git clone {url} {local location}
```
4. Open the project in VSCode.