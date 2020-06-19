

Title: Issue History Ansible Opensim
====================================

__Git__

**git command line login credentials**
After setting up Two Factor Authentication (2FA) on gitgub the usual password won't work anymore. You have to generate an access token and use the token instead of the password.
To avoid having to type or paste inn this access token over and over you can:
-  cache your credentials for a number of seconds with the command:

   `$ git config --global credential.helper 'cache --timeout=7200'`
-  store your cridentials by:

   `git config credential.helper store`

   The credentials will be stored in `~/git-credentials` on the next time you enter your password token.

:link: [Creating a personal access token for the command line](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line)
:link: [Using command-line git with GitHub 2FA](http://gmacario.github.io/2017/08/08/cmdline-git-with-github-2fa.html)
