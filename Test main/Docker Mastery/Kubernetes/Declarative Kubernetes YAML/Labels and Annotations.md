
- Labels goes under ==metadata:== in your YAML
- Simple list of key: value for identifying your resource later by selecting, grouping, or filtering for it
- Common examples include tier: frontend, app: api, env: prod, customer: acme.co
- Not meant to hold complex, large, or non-identifying info, which is what annotations are for
- filter a get command
	- `kubectl get pods -l app=nginx`
- apply only matching labels
	- kubectl apply -f myfile.yaml -l app=nginx

## Label Selectors

- The "glue" telling Services and Deployments which pods are theirs
- Many resources use Label Selectors to "link" resource dependencies
- You'll see these match up in the Service and Deployment YAML
- Use Labels and Selectors to control which pods go to which nodes
- Taints and Tolerations also control node placement

## Cleanup

- Let's remove anything you created in this section
	- `kubectl get all`
	- `kubectl delete <resource type>/<resource name>`