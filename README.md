# Ansible Role Munkitools

Installs Munki, MunkiAdmin, AutoPKG, and AutoPkgr on a Mac. Optionally, clones an existing Munki repo to the local machine or can be used to only install the core Munkitools (for machines which are Munki clients but not Munki admins). Aspirationally, will add the ability to provision and sync a repo with a cloud storage provider (S3 or similar).

## Getting Started

Minimum Ansible Version: `2.5`

### Installation:

Clone from Ansible Galaxy:

    ansible-galaxy install apmarshall.ansible_role_munki_in_a_box
    
Include in a `requirements.yml`:

    - src: apmarshall.ansible_role_munki_in_a_box
    
## Testing

Syntax Check: `ansible-playbook tests/test.yml --syntax-check`
Run the Test Playbook: `ansible-playbook tests/test.yml`

## Usage

Example Playbook:
    - hosts: localhost
    vars: "{{ variables_file }}"
    roles:
      - apmarshall.ansible_role_munki_in_a_box 

### Role Variables:
Principle Variables:
    munkitools_existing_repo: boolean // true if you have an existing munki repo you wish to clone, false if starting fresh
    munkitools_repo_url: "url" // url of the repo you wish to clone (default is empty, doesn't come into play if munkitools_existing_repo is false)
    munki_repo_loc: "path/to/local/repo/location" // default is "Users/Shared/munki_repo"
    munki_default_catalog: "Catalog" // Catalog you want to default to installing packages to. Default is "Test"
    autopkg_repos: [] // List of autopkg repos you wish to install. Default is an empty list
    autopkg_packages: [] // List of autopkg packages you wish to install from the chosen repos. Default is an empty list
    is_munki_admin: boolean // If true, installs all packages for maintaining a munki repository. If false, only installs the core munkitools (essentially setting up a client machine)

Other Variables that Might Be Useful:
    user_home: Defaults to current user's home directory
    munki_admin_user: Defaults to the current user
    munki_editor: Defaults to emacs (so you should probably change this one)_

## Authors:

- [Alex Floyd Marshall](https://github.com/apmarshall): Initial creator and maintainer

## Acknowledgments

- [Tom Bridge](https://github.com/tbridge): Inspiration and provided the shell scripts which formed the basis for the underlying logic and structure
- [Jeff Geerling](https://github.com/geerlingguy): For providing such clear templates of how to use Ansible, including for the purposes of this role using GitHub actions for CI
