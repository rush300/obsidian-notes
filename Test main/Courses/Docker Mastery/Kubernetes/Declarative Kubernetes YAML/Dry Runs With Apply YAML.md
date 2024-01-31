In the next lecture video, you will learn about the `--dry-run` option.  The dry run feature was tweaked since Kubernetes 1.18 and the option name has changed slightly, but its purpose and functionality has not, so I didn't think it was necessary to re-record the whole video. You'll learn about how you can use dry run to test your changes before they are applied to a cluster.  The --dry-run option is no longer just a true/false option has as expanded to accept multiple values.

In the next video you'll see the option `--dry-run` used. That has changed to now be `--dry-run=client`

You'll also see `--server-dry-run` used. That is now changed to `--dry-run=server`

The two options were changed to be more consistent.  If you try to use the old options in a command, you'll get a warning to use the new format.

- New stuff, not out of beta yet
- dry-run a create (client side only)
	- `kubectl apply -f app.yml --dry-run`
- dry-run a create/update on server
	- `kubectl apply -f app.yml --server-dry-run`
- see a diff visually
	- `kubectl diff -f app.yml`