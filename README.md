Bonita Workspace Manager
========================

This is a rather simple utility to help management of workspaces in the
community edition of BonitaBPM which doesn't have this feature.

It's done simply by creating new workspaces from a template and symlinking the
active one to the BonitaBPM  installation directory.


Disclaimer
----------

```
Alpha software, i do not take any responsibility for any damage it may cause to
your system, although it shouldn't.

For safety BonitaBPM should be closed while using this utility.

It has only been tested with version 7.3.3 under linux.
```

Usage:
------

```bash
# Only required configuration
export BONITA_INSTALL_DIR='/path/to/bonita/installation'

# First we have to let bonitawm start handling workspaces. This will
bonitawm -initialize

# Now we can create new workspaces.
bonitawm -new somews

# and enable them
bonitawm -enable somews

# to list available workspaces
bonitawm -list
# => default somews
```

Installation
------------

Clone repo and add [bonitawm](./bin/bonitawm) to your `$PATH`

```bash
git clone https://github.com/farfanoide/bonita_workspace_manager ~/bonitawm

ln -s ~/bonitawm/bin/bonitawm /usr/local/bin
```


Configuration
-------------

Available configurations are:

**BONITA_INSTALL_DIR -- [Required]:** Represents the installation directory of your
BonitaBPM.

**BONITAWM_WS_DIR    -- [Optional]:** Represents the directory where workspaces will
be saved. If left unset the workspaces directory in the repo will be used.

Commands:
---------

All commands have a long and a short flag, ie: the `initialize` command can
be invoked both as `-i` and as `-invoke`.

### Initialize

Enables `bonitawm` to start managing workspaces. it basically checks if the
default workspace currently installed is a directory or a symlink. If it's a
directory `bonitawm` will copy it to the workspaces directory and enable it.

```bash
bonitawm -i
# or
bonitawm -initialize
```

### List

Lists all available workspaces currently created.

```bash
bonitawm -l
# or
bonitawm -list
```

### New

Receives a `name` as only argument and creates a new workspaces with the given
name.

```bash
bonitawm -n 'ws_name'
# or
bonitawm -new 'ws_name'
```

### Enable

Receives a `name` as only argument and enables said workspace if available.

```bash
bonitawm -e 'ws_name'
# or
bonitawm -enable 'ws_name'
```

License:
--------

See the [LICENSE](LICENSE).

Contributing:
-------------

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
