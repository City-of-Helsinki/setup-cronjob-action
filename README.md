# setup-cronjob-action

Action to set up cronjob to Kubernetes namespace.

## Configuration

Following input variables are used in the action. Values without default value are mandatory.

| Name               | Description                                                                                                                                               |                    Default value                    |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------: |
| `kubeconfig_raw`   | Kubeconfig as text to allow access to cluster and namespaces (RBAC) having Tunnistamo and review environment.                                             |                                                     |
| `target_namespace` | Namespace of where cronjob is deployed to                                                                                                                 |                                                     |
| `secret_name`      | Secret including environment variables for the job. Has to exist when job is started (not necessarily at the time CronJob created).                       |                         ""                          |
| `configmap_name`   | ConfigMap including environment variables for the job. Has to exist when job is started (not necessarily at the time CronJob created).                    |                         ""                          |
| `schedule`         | Schedule of job to run. Remember to give time according Kubernetes node timezone (preferably UTC). Comma needs to be escaped if used.                     |                     `0 0 * * *`                     |
| `command`          | Command (Entrypoint in container image) to use. Note notation with curly braces                                                                           |                     `{bin/sh}`                      |
| `args`             | Arguments (Command in container image) to use. Note notation with curly braces. Comma needs to be escaped if used.                                        | `{-c,date; echo Hello from the Kubernetes cluster}` |
| `envs`             | Direct environment variables to job. Note format (https://helm.sh/docs/intro/using_helm/#the-format-and-limitations-of---set). Key is `env.<desired_key>` |                         ""                          |
| `name`             | Name to use in job. Mandatory if multiple cronjobs in one namespace                                                                                       |                   action-cronjob                    |
| `single_run`       | If true, creates single job instaed of cronjob. This allows testing of job easier                                                                         |                       `false`                       |
| `request_cpu`      | CPU request to created pod                                                                                                                                |                        100m                         |
| `request_memory`   | Memory request to created pod                                                                                                                             |                        256Mi                        |
| `limit_cpu`        | CPU limit to created pod                                                                                                                                  |                        500m                         |
| `limit_memory`     | Memory limit to created pod                                                                                                                               |                       1024Mi                        |
| `max_duration`     | Jobs max duration (in seconds)                                                                                                                            |                         300                         |
