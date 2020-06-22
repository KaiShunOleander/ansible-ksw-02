

Lesson's Learned creating Ansible Opensim
=========================================

**Ansible**

*code editor * - After using just vi for coding the need arrised to get an editor that supports the yaml syntax. I first tried `atam`, which used lots of resources, switched to `sublime` which is more light weight and than when I was looking in to Travis saw people use a slick using interface that even supported git. Seems that most people either use `Xode` for a Mac or `Visual Studio Code` which you can use on Linux. There is eve a Visual Code editor for the iPad called `VSApp Code Server`

Under Ubuntu the `Visual Code Viewer` can be installed with:
```
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -o root -g root -m 644 packages.microsoft.gpg /usr/share/keyrings/
sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install code # or code-insiders
```

*role skeletons* - To create skeletons for roles, yaml files were used. When creating a role based on a skeleton the yaml files are replaced by target files, e.a. main.yml.j2 will be replaced by main.yml. Only the {{ role_name }} var;iable will be expanded. 
If we like to generate the following code:
```YAML
   - name: Ensure nginx is started and enabled at boot.
  service:
    name: ngginx
    state: "{{ nginx_service_state }}"
```

then we can **can not** use the following jinja code

```YAML
- name: Ensure {[ role_name }} is started and enabled at boot.
  service:
    name: {{  role_name }}
    state: "{{ {{ role_name }}_service_state }}"
    enabled: "{{ {{ role_name }}_service_enabled }}"
```

The parser won't like this nesting and generates an error on the four curly brackets. we can escape the brackets however by using:

```YAML
- name: Ensure {{ role_name }} is started and enabled at boot.
  service:
    name: {{ role_name }}
    state: {% raw %}"{{{% endraw %} {{ role_name }}_service_state {% raw %}}}"{% endraw %}
    enabled: {% raw %}"{{{% endraw %} {{ role_name }}_service_enabled {% raw %}}}"{% endraw %}
```

:link: [Using a custom role skeleton](https://docs.ansible.com/ansible/latest/galaxy/dev_guide.html#using-a-custom-role-skeleton)

:link: [Unsafe or Raw String](https://docs.ansible.com/ansible/latest/user_guide/playbooks_advanced_syntax.html#unsafe-or-raw-strings)

**GitHub**

*GitHub Workflows* - Molecule seems to need a playbook on a single system (localhost), so testing playbooks or roles which include different roles or target different systems seems an issue. Makes sense the workflow tests should be unit tests and not test all playbooks used to configure the opensim grid.

A Workflow can be triggered on a commit on the repository. To target a single role for a unit test upon a git-commit means for now that each role will use a seperate github repository.

:link: [GitHub action to run Molecule](https://robertdebock.nl/2019/12/20/github-action-to-run-molecule.html)

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



**MD*

*Usefull MD code block extentions*
- Batchfile
- C, C#, C++
- console
- Dockerfile
- HTML
- INI
- JSON
- Nginx
- PHP
- PLSQL
- Python
- YAML
