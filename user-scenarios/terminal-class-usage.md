1. Delete the Kubernetes secret by running:

    ```
    kubectl delete secret INSTANCE-NAME-credentials
    ```
    Where `INSTANCE-NAME` is the name of the MySQL instance.

    For example:

    <pre class="terminal">$ kubectl delete secret mysql-sample-credentials
    <br>secret "mysql-sample-credentials" deleted
    </pre>

1. Wait until Kubernetes has automatically re-created the secret.
   You can watch the progress by running:

    ```
    kubectl get secret --watch
    ```
    For example:

    <pre class="terminal">$ kubectl get secret --watch
NAME                                  TYPE                                  DATA   AGE
default-token-wb7gl                   kubernetes.io/service-account-token   3      10d
<span style="color: #77bf00;">mysql-sample-credentials         Opaque                                4      48s</span>
tanzu-mysql-backup-cron-token-c7bnt   kubernetes.io/service-account-token   3      10d
tanzu-mysql-image-registry            kubernetes.io/dockerconfigjson        1      2m3s
tanzu-mysql-token-24cdv               kubernetes.io/service-account-token   3      10d
    </pre>

1. Update the database with the new passwords by restarting your MySQL instance:

    ```
    kubectl rollout restart statefulset INSTANCE-NAME
    ```

    For example:

    <pre class="terminal">$ kubectl rollout restart statefulset mysql-sample
    <br>statefulset.apps/mysql-sample restarted
    </pre>

1. Verify that your MySQL instance has finished updating by running:

    ```
    kubectl get mysql INSTANCE-NAME
    ```
    A MySQL instance has finished updating when the value of the `STATUS`
    column is `Running`.
    For example:

    <pre class="terminal">$ kubectl get mysql mysql-sample
    <br>NAME           READY   STATUS    AGE
    mysql-sample   true    Running   10d
    </pre>

1. To verify that the passwords were rotated successfully, try connecting to your
   MySQL instance.
   See [Accessing MySQL Instances](accessing.html).

## <a id='patch-secret'></a>Option 2: Patch the Kubernetes Secret with a Custom Password
