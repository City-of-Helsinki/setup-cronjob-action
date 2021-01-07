# setup-cronjob-action

Action to set up cronjob to Kubernetes namespace.

## Configuration

Following input variables are used in the action. Values without default value are mandatory.

| Name               | Description                                                                                                                           |                    Default value                    |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------: |
| `kubeconfig_raw`   | Kubeconfig as text to allow access to cluster and namespaces (RBAC) having Tunnistamo and review environment.                         |                                                     |
| `target_namespace` | Namespace of where cronjob is deployed to                                                                                             |                                                     |
| `secret_name`      | Secret including environment variables for the job                                                                                    |                         ""                          |
| `configmap_name`   | ConfigMap including environment variables for the job                                                                                 |                         ""                          |
| `schedule`         | Command (Entrypoint in container image) to use. Note notation with curly braces                                                       |                     `0 0 * * *`                     |
| `command`          | Schedule of job to run. Remember to give time according Kubernetes node timezone (preferably UTC). Comma needs to be escaped if used. |                     `{bin/sh}`                      |
| `args`             | Arguments (Command in container image) to use. Note notation with curly braces. Comma needs to be escaped if used.                    | `{-c,date; echo Hello from the Kubernetes cluster}` |
