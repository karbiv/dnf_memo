
Memo for the DNF software package manager(Fedora Linux, "Dandified Yum").  

+ `dnf` allows only `*`, `?`, `[]` globbing in query strings(exps).
+ `apt-get` may use POSIX regular exps.

| Red&nbsp;Hat/Fedora | Debian/Ubuntu | Description |
| :------------------ | :------------ | :---------- |
| dnf install | apt install | Install packages
| dnf remove | apt remove | Remove packages
| dnf search | apt search | Search for packages by a word in name, description, etc
| dnf upgrade | apt&nbsp;update;&nbsp;apt&nbsp;upgrade | Upgrade installed packages to newer versions
| dnf distro-sync | apt full-upgrade | Upgrade packages with distro version upgrade
| dnf&nbsp;clean&nbsp;all&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br>{*metadata,packages,dbcache,<br>expire-cache,all*} | apt-get&nbsp;clean /&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br>apt-get&nbsp;autoclean&nbsp;/<br>aptitude clean | Clean up all local caches. Autoclean deletes only obsolete info
| dnf autoremove | apt-get autoremove | Remove dependencies that are no longer needed
| dnf mark install | apt-mark manual | Mark or unmark installed packages as installed by user.
| dnf install<br>dnf mark remove | aptitude install '$package&M' | Install package(s) as dependency / without marking as explicitly required.
| dnf download | apt-get&nbsp;install&nbsp;--download-only<br>(into the package cache)<br>apt-get download<br>(bypass the package cache) | Download package to current directory
| dnf history<br>[*list\|info\|redo\|undo<br>\|rollback\|userinstalled*] | cat /var/log/dpkg.log | Show a log of actions taken by the software management.
| dnf&nbsp;list,&nbsp;dnf&nbsp;info | apt&nbsp;show&nbsp;/<br>apt-cache&nbsp;policy | Show all or most information about a package
|  | aptitude purge '~o' | Remove packages no longer included in any repositories.
| dnf repoquery --extras |  | List packages no longer included in any repositories.
| dnf repoquery --whatrequires | apt-cache rdepends /<br>aptitude&nbsp;search&nbsp;~D$pattern | Display packages which require X to be installed, i.e. show reverse dependencies
| dnf repoquery --conflicts | aptitude&nbsp;search&nbsp;'~C$pattern' | Display packages which conflict with given expression (often package)
| dnf repoquery --requires | apt-cache depends /<br>apt-cache show | Show dependencies
| dnf repoquery -l | apt-file list $pattern | Display files provided by a remote/local package
| dnf repoquery --installed | dpkg -l | List installed packages along with version
| dnf provides | dpkg -S / dlocate | Search the package which provides FILE
| dnf repoquery -f  | apt-file search | Displays packages which provide the given *exp*
|  | apt-get changelog | Show the changelog of a package
| dnf check-update | apt-get upgrade -> n | Lists packages which have an update available
| dnf list available | apt-cache dumpavail<br>apt-cache&nbsp;dump&nbsp;(Cache&nbsp;only)<br>apt-cache pkgnames | Display a list of all packages in all installation sources
| dnf list installed | dpkg --list \| grep ^i | List of installed packages
| ... | ... | ...