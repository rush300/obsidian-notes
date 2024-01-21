
- Imperative: Focus on how a program operates
- Declarative: Focus on what a program should accomplish
- Example: "I'd like a cup of coffee"
- Imperative: I boil water, scoop out 42 grams of medium-fine grounds, poor over 700 grams of water, etc.
- Declarative: "Barista, I'd like a cup of coffee". (Barista is the engine that works through the steps, including retying to make a cup, and is only finished when I have a cup)

## Kubernetes Imperative

- Examples: `kubectl run, kubectl create deployment, kubectl update`
	- We start with a state we know (no deployment exists)
	- We ask `kubectl` run to create a deployment
- Different commands are required to change that deployment
- Different commands are required per object
- Imperative is easier when you know the state
- Imperative is easier to get started
- Imperative is easier for humans at the CLI
- Imperative is NOT easy to automate

## Kubernetes Declarative

- Example: `kubectl apply -f my-resources.yaml`
	- We don't know the current state
	- We only know what want the end result to be (yaml contents)
- Same command each time (tiny exception for delete)
- Resources can be all in a file, or many files (apply a whole dir)
- Requires understanding the YAML keys and values
- More work than `kubectl run` for just starting a pod
- The easiest way to automate
- The eventual path to GitOps happiness