# Managing NGINX with Helm

## Prerequisites

* Helm installed on your system.
* A running Kubernetes cluster.
* kubectl configured to interact with the cluster.

---

### 1. Installing NGINX using Helm

To deploy NGINX, we will use the Bitnami Helm chart.

1. **search for charts in the Artifact Hub or your own hub instance**

   ```bash
   helm search hub nginx
   ```
2. **To get all information about the chart**

   ```bash
   helm show all bitnami/nginx
   ```
3. **you can add a chart repository. Check [Artifact Hub](https://artifacthub.io/packages/search?kind=0) for available Helm chart repositories.**

   ```bash
   helm repo add bitnami https://charts.bitnami.com/bitnami
   ```

4. **Add the Bitnami repository:**

   ```bash
   helm repo add bitnami https://charts.bitnami.com/bitnami
   helm repo update
   ```

5. **Install the NGINX Helm chart:**

   ```bash
   helm install my-nginx bitnami/nginx
   ```

6. **Verify the installation:**

   ```bash
   helm list
   kubectl get pods
   ```

---

### Customize during Installation

* To see available values for customization, run:

  ```bash
  helm show values bitnami/nginx
  ```
* To preview the manifest without deploying:

  ```bash
  helm template my-nginx bitnami/nginx
  ```

---

### 2. Upgrading NGINX using Helm

To upgrade the NGINX release, we can change parameters or update the chart version.

1. **Upgrade the release:**

   ```bash
   helm upgrade my-nginx bitnami/nginx --set service.type=NodePort
   ```

2. **Check the upgrade status:**

   ```bash
   helm status my-nginx
   ```

---

### 3. Uninstalling NGINX using Helm

To remove the NGINX release from the cluster:

1. **Uninstall the release:**

   ```bash
   helm uninstall my-nginx
   ```

2. **Verify the uninstallation:**

   ```bash
   helm list
   kubectl get pods
   ```

Want to uninstall a chart but release history will be kept

```bash
helm uninstall mysql-1612624192 --keep-history
```

Helm tracks your releases even after you've uninstalled them, you can audit a cluster's history, and even undelete a release (with `helm rollback`)

---



