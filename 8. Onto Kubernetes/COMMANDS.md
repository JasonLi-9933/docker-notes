# Feed a config file to kubectl

`kubectl apply -f <filename/path_to_file>`

- _apply_: change the current config of our cluster

# Print the status of all running pods `kubectl get pods`

# Print the status of all running services `kubectl get services`

# Print the status of all running deployments `kubectl get deployments`

# Print the status of all running persistent volumes `kubectl get pv`

# Print the status of all running persistent volume claims `kubectl get pvc`

# Get detailed info about an object `kubectl describe <object-type> <object-name>`

`object-name` is optional

# Remove an object: `kubectl delete -f <config-file>` (an imperative update)

# Imperatively updating a Deployment image

`kubectl set image <object_type>/<object_name> <container_name>=<new_image>`

ex: `kubectl set image deployment/client-deployment client/stephengrider/multi-client:v5`

# (Imperatively) create a Secret

`kubectl create secret <type-of-secret> <secret-name> --from-literal key=value`

- `create`: imperative command to create a new object
- `<type-of-secret>`: _docker-registry_, _tls_, _generic_
- `--from-literal`: we are going to add the secret info into this command, as opposed to from file

ex: `kubectl create secret generic pgpassword --from-literal PGPASSWORD=12345`
