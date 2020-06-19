

Title: Lesson's Learned creating Ansible Opensim
================================================

**GitHub**

*GitHub Workflows* - Molecule seems to need a playbook on a single system (localhost), so testing playbooks or roles which include different roles or target different systems seems an issue. Makes sense the workflow tests should be unit tests and not test all playbooks used to configure the opensim grid.

Workflow are triggered on a commit on the repository. To target a single role for a unit test upon a git-commit means for now that each role will use a seperate github repository.

*GitHub Projects* - Projects ( containing KanBan boards) can be linked to a repository, an github personal account or a organization. If you create an account, and filled a project connected to the account, and than decide to create an organization, there doesnt seem a way to transfer a project to the organization level, unless you create the organization promoting the personal account to a organization.

**Git**

*git command line login credentials:* - 
After setting up Two Factor Authentication (2FA) on gitgub the usual password won't work anymore. You have to generate an access token and use the token instead of the password.
To avoid having to type or paste inn this access token over and over you can:
-  cache your credentials for a number of seconds with the command:

   `$ git config --global credential.helper 'cache --timeout=7200'`
-  store your cridentials by:

   `$ git config credential.helper store`

   The credentials will be stored in `~/git-credentials` on the next time you enter your password token.

:link: [Creating a personal access token for the command line](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line)

:link: [Using command-line git with GitHub 2FA](http://gmacario.github.io/2017/08/08/cmdline-git-with-github-2fa.html)

**Molecule**

*Name of the test* is set in `molecule.yml` under platforms:. Molecule doesn'lt like spaces in the name, so use underscore.
