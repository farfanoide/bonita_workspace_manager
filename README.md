Bonita Workspace Manager
------------------------

This is a rather simple utility to help management of workspaces in the
community edition of BonitaBPM which doesn't have this feature.

It's done simply by creating new workspaces from a template and symlinking the
active one to the BonitaBPM  installation directory.


Usage:
======

```bash
# Only required configuration
export BONITA_INSTALL_DIR='/path/to/bonita/installation'

# First we have to let bonita_wm start handling workspaces. This will
bonita_wm -initialize

# Now we can create new workspaces.
bonita_wm -new somews

# and enable them
bonita_wm -enable somews

# to list available workspaces
bonita_wm -list
# => default somews
```

Installation
============

Clone repo and add [bonita_wm](./bin/bonita_wm) to your `$PATH`

```bash
git clone https://github.com/farfanoide/bonita_workspace_manager ~/bonita_wm

ln -s ~/bonita_wm/bin/bonita_wm /usr/local/bin
```


Configuration
=============

Available configurations are:

**BONITA_INSTALL_DIR**: [Required] Represents the installation directory of your
BonitaBPM.

**BONITAWM_WS_DIR**: [Optional] Represents the directory where workspaces will
be saved. If left unset the workspaces directory in the repo will be used.

Disclaimer
==========

```
For safety BonitaBPM should be closed while using this utility.
It has  only been tested with version 7.3.3
```

Commands:
=========

All commands have a long and a short flag, ie: the `initialize` command can
be invoked both as `-i` and as `-invoke`.

### Initialize

Enables `bonita_wm` to start managing workspaces. it basically checks if the
default workspace currently installed is a directory or a symlink. If it's a
directory `bonita_wm` will copy it to the workspaces directory and enable it.

```bash
bonita_wm -i
# or
bonita_wm -initialize
```

### List

Lists all available workspaces currently created.

```bash
bonita_wm -l
# or
bonita_wm -list
```

### New

Receives a `name` as only argument and creates a new workspaces with the given
name.

```bash
bonita_wm -n 'ws_name'
# or
bonita_wm -new 'ws_name'
```

### Enable

Receives a `name` as only argument and enables said workspace if available.

```bash
bonita_wm -e 'ws_name'
# or
bonita_wm -enable 'ws_name'
```

