# distro-snapper

Small tool to create, manage and rollback to snapshots of distrobox-containers.

NOTE: Currently, only distrobox using **podman** is supported!

## Usage
### Create snapshot

```
$ distrobox create -n foo

$ distrobox enter foo
# Install some packages and leave it again

$ distro-snapper current foo
registry.opensuse.org/opensuse/distrobox:latest

$ distro-snapper create foo
```

This creates a podman container commit of the current state of the distrobox.

### List snapshots

```
$ distro-snapper ls foo
localhost/f1d2d2f924e986ac86fdf7b36c94bcdf32beec15-2024-06-18t11-24-07
```

Name of the snapshots look like `localhost/$(SHA1_HASH_OF_DISTROBOX_NAME)-$(DATE)t$(TIME)`.

### Rollback to old snapshot after you messed up your container

```
$ distro-snapper rollback foo localhost/f1d2d2f924e986ac86fdf7b36c94bcdf32beec15-2024-06-18t11-24-07
```

Note: This throws away the current state and rolls back to the given image. If you want to keep the current state, make a snapshot before rolling back.

### Update distrobox

Convenience-wrapper to make a snapshot and then update the container.
This will keep 3 snapshots in total and remove all older snapshots.

```
$ distro-snapper update foo 3
```

### Export / import snapshots

Create a tarball of a snapshot.

```
$ distro-snapper export foo localhost/f1d2d2f924e986ac86fdf7b36c94bcdf32beec15-2024-06-18t11-24-07 /tmp/
$ ls /tmp/*.tar.bz
foo-2024-06-18t11-24-07.tar.bz

$ distro-snapper import /tmp/foo-2024-06-18t11-24-07.tar.bz
```
