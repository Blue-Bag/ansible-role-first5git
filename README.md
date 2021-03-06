# Ansible Role: Git
[![Build Status](https://travis-ci.org/Blue-Bag/ansible-role-first5git.svg?branch=main)](https://travis-ci.org/Blue-Bag/ansible-role-first5git)


Installs Git, a distributed version control system, on any RHEL/CentOS or Debian/Ubuntu Linux system.

Based on geerlingguy.ansible-role-git

only addition is to template the config - could separate that and use the role

should the check for git installed be carried out before downloading git?

ToDo use the PPA repo to install the latest version

Add Redhat dependencies:
see https://github.com/Marslo/MyBlog/blob/master/Programming/Git/GitQ%26A.md

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    workspace: /root

Where certain files will be downloaded and adjusted prior to git installation, if needed.

    git_enablerepo: ""

This variable, as well as `git_packages`, will be used to install git via a particular `yum` repo if `git_install_from_source` is false (CentOS only). Any additional repositories you have installed that you would like to use for a newer/different Git version.

    git_packages:
      - git
      - git-svn

The specific Git packages that will be installed. By default, `git-svn` is included, but you can easily add this variable to your playbook's variables and remove `git-svn` if desired.

    git_install_from_source: false
    git_install_path: "/usr"
    git_version: "2.1.0"

Whether to install Git from source; if set to `true`, `git_version` is required and will be used to install a particular version of git (see all available versions here: https://www.kernel.org/pub/software/scm/git/), and `git_install_path` defines where git should be installed.

## Dependencies

None.

## Example Playbook

    - hosts: servers
      roles:
        - { role: ansible-role-first5git }

## License

MIT / BSD

## Author Information
Forked by Blue-Bag from:

This role was created in 2014 by [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/).
