
- Imperative commands: run, expose, scale, edit, create deployment
	- Best for dev/learning/personal projects
	- Easy to learn, hardest to manage over time
- Imperative objects: create -f file.yml, replace -f file.yml, delete ...
	- Good for prod of small environments, single file per command
	- Store your changes in git-based yaml files
	- Hard to automate
- Declarative objects: apply -f file.yml or dir\, diff
	- Best for prod, easier to automate
	- Harder to understand and predict changes

## Most Important Rule:
- Don't mix the three approaches
## Bret's recommendations:
- Learn the Imperative CLI for easy control of local and test setups
- Move to apply -f file.yml and apply -f directory\ for prod
- Store yaml in git, git commit each change before you apply
- This trains you for later doing GitOps (where git commits are automatically applied to clusters)