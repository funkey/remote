remote
======

Simple script to execute a command on a remote server. Great to deploy
experiments on a cluster.

Usage
-----

```bash
remote <cmd>
```

Searches for a `remote.toml` file in parent directories. The directory where
this file is found is treated as the project directory. Everything under this
directory will be `rsync`ed to the remote.

Example `remote.toml`:
```toml
# name of the remote server
remote = "submit"

# the corresponding project directory on the remote server
remote_project_dir = "~/projects/fluffy"

# an optional command prefix to prepend to the <cmd> given above
command_prefix = "bsub -I -q gpu_a100 -gpu 'num=1' uv run --with 'jax[cuda]'"

[rsync]
# exclude certain files/directories from syncing
exclude = [".git", "__pycache__", "*.tmp"]

# other options to pass to rsync
# extra_options = ["--dry-run"]
```
