# Rancher Prime on the Google Cloud Marketplace

## Command line instructions

#### Clone this repo

Clone this repo:

```shell
git clone https://github.com/rancher/rancher-prime-gcm
cd rancher/rancher-prime-gcm
```

#### Install the Application resource definition

An Application resource is a collection of individual Kubernetes components,
such as Services, Deployments, and so on, that you can manage as a group.

To set up your cluster to understand Application resources, run the following
command:

```shell
kubectl apply -f "https://raw.githubusercontent.com/GoogleCloudPlatform/marketplace-k8s-app-tools/master/crd/app-crd.yaml"
```

You need to run this command once.

The Application resource is defined by the
[Kubernetes SIG-apps](https://github.com/kubernetes/community/tree/master/sig-apps)
community. The source code can be found on
[github.com/kubernetes-sigs/application](https://github.com/kubernetes-sigs/application).

#### Define install vars.

```shell
export NAME="rancher"
export NAMESPACE="cattle-system"
export VERSION="2.15.3"
```

#### Download and install a licence key

In the GCP console, click "Generate license key" and install into the desired application namespace, create this if it does not currently exist.

### Perform helm install

A helm installation and subsequent management can now be performed as per the default Rancher Prime documentation, sourcing the chart from this repository.

```shell
helm upgrade --install "$NAME" "./charts/$VERSION" --namespace $NAMESPACE
```
