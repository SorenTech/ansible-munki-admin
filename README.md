# ansible-role-munkitools

Repository to set up the munki admin tools on a Mac that will be used to administer a munki repository.

## What it Does:
- Installs the latest version of Munki and its Admin Tools
- Optionally: Clone an existing Munki Repository onto the admin machine
- Optionally: Set up a new Munki Repository on the admin machine

## Variables:
`
munkitools_existing_repo: default no -> creation of new (local) repo
munkitools_repo_location
`
