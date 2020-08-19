# DNF


## Commandes de base

**list all installed and available packages**

`dnf list`

**list all the installed packages**

`dnf list installed`

**list available packages**

`dnf list available`

**search any package**

`dnf search httpd`

**install**

`dnf install httpd`

**reinstall**

`dnf reinstall httpd`

**download the packages without installing it**

`dnf download httpd`

**see details of package**

`dnf info httpd`

**check updates for all the system packages**

`dnf check-update`

**update all the packages installed**

`dnf update`

**update only one package**

`dnf update httpd`

**remove packages**

`dnf remove httpd`
`dnf erase httpd`

**remove unwanted dependencies**

`dnf autoremove`

**clean all the cached packages**

`dnf clean all`


### Groupes

**list all group packages**

`dnf grouplist`

**install specific Group**

`dnf groupinstall 'System Tools'`

**update a Group package**

`dnf groupupdate 'System Tools'`

**remove a group package**

`dnf groupremove 'System Tools'`


## Repos

**list all repos**

`dnf repolist all`

**list only active ones**

`dnf repolist`

**disable a repo**

`dnf config-manager --disable repo-name`


## Misc

**Check which package provides the required function**

`dnf provides crontab`

**Check which package is associated to a file**

`dnf provides /var/www/html`
`dnf provides "*/bin/tree"`
`dnf provides "*/libssl.so*"`

**check dnf history**

`dnf history`

with this command, we can see dnf commands have an id. To get info about one of them :

`dnf history info 5`

**synchronize to latest stable releases**

`dnf distro-sync`

**search for packages by their package name**

`dnf repoquery *kvm*`

**same, in one repo**

`dnf repoquery "*ssh*" --repo fedora`
`dnf repoquery "*ssh*" --repo updates`

**install only required security patches**

`dnf upgrade-minimal`

**system upgrade**

Example from Fedora 31 to 32:

`dnf upgrade --refresh`
`dnf install dnf-plugin-system-upgrade` (if not already done)
`dnf system-upgrade download --refresh --releasever=32`
`dnf system-upgrade reboot`

