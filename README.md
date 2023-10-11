# microservice

Menyeiapkan seluruh file yang dibutuhkan, saya menyimpannya di /d/tugas3/

## Langkah 1: Start Minikube

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes$ minikube start
😄  minikube v1.31.2 on Microsoft Windows 11 Home Single Language 10.0.22621.2283 Build 22621.2283
✨  Automatically selected the docker driver
📌  Using Docker Desktop driver with root privileges
👍  Starting control plane node minikube in cluster minikube
🚜  Pulling base image ...
💾  Downloading Kubernetes v1.27.4 preload ...
    > preloaded-images-k8s-v18-v1...:  393.21 MiB / 393.21 MiB  100.00% 4.98 Mi
🔥  Creating docker container (CPUs=2, Memory=2200MB) ...
🐳  Preparing Kubernetes v1.27.4 on Docker 24.0.4 ...
    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...
🔗  Configuring bridge CNI (Container Networking Interface) ...
🔎  Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: storage-provisioner, default-storageclass

❗  C:\Program Files\Docker\Docker\resources\bin\kubectl.exe is version 1.25.9, which may have incompatibilities with Kubernetes 1.27.4.
    ▪ Want kubectl v1.27.4? Try 'minikube kubectl -- get pods -A'
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```

## Langkah 2: Dapatkan IP Minikube

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes$ minikube ip
192.168.49.2
```

## Langkah 3: Unduh Istio

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes$ curl -L https://github.com/istio/istio/releases/download/1.17.1/istio-1.17.1-win.zip -o istio-1.17.1-win.zip
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100 26.7M  100 26.7M    0     0  3565k      0  0:00:07  0:00:07 --:--:-- 3652k

```

### Langkah 4: Extrak

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes$ unzip istio-1.17.1-win.zip
Archive:  istio-1.17.1-win.zip
   creating: istio-1.17.1/
  inflating: istio-1.17.1/LICENSE
  inflating: istio-1.17.1/README.md  
   creating: istio-1.17.1/bin/
  inflating: istio-1.17.1/bin/istioctl.exe
  inflating: istio-1.17.1/manifest.yaml
   creating: istio-1.17.1/manifests/
   creating: istio-1.17.1/manifests/charts/
  inflating: istio-1.17.1/manifests/charts/README.md
  inflating: istio-1.17.1/manifests/charts/UPDATING-CHARTS.md  
   creating: istio-1.17.1/manifests/charts/base/
  inflating: istio-1.17.1/manifests/charts/base/Chart.yaml
  inflating: istio-1.17.1/manifests/charts/base/README.md
   creating: istio-1.17.1/manifests/charts/base/crds/
  inflating: istio-1.17.1/manifests/charts/base/crds/crd-all.gen.yaml  
  inflating: istio-1.17.1/manifests/charts/base/crds/crd-operator.yaml  
   creating: istio-1.17.1/manifests/charts/base/files/
  inflating: istio-1.17.1/manifests/charts/base/files/gen-istio-cluster.yaml  
  inflating: istio-1.17.1/manifests/charts/base/kustomization.yaml
   creating: istio-1.17.1/manifests/charts/base/templates/
  inflating: istio-1.17.1/manifests/charts/base/templates/NOTES.txt
  inflating: istio-1.17.1/manifests/charts/base/templates/clusterrole.yaml  
  inflating: istio-1.17.1/manifests/charts/base/templates/clusterrolebinding.yaml
  inflating: istio-1.17.1/manifests/charts/base/templates/crds.yaml  
  inflating: istio-1.17.1/manifests/charts/base/templates/default.yaml
  inflating: istio-1.17.1/manifests/charts/base/templates/endpoints.yaml  
  inflating: istio-1.17.1/manifests/charts/base/templates/reader-serviceaccount.yaml
  inflating: istio-1.17.1/manifests/charts/base/templates/role.yaml
  inflating: istio-1.17.1/manifests/charts/base/templates/rolebinding.yaml  
  inflating: istio-1.17.1/manifests/charts/base/templates/serviceaccount.yaml
  inflating: istio-1.17.1/manifests/charts/base/templates/services.yaml  
  inflating: istio-1.17.1/manifests/charts/base/values.yaml
   creating: istio-1.17.1/manifests/charts/default/
  inflating: istio-1.17.1/manifests/charts/default/Chart.yaml
   creating: istio-1.17.1/manifests/charts/default/templates/
  inflating: istio-1.17.1/manifests/charts/default/templates/mutatingwebhook.yaml  
  inflating: istio-1.17.1/manifests/charts/default/templates/validatingwebhook.yaml  
  inflating: istio-1.17.1/manifests/charts/default/values.yaml
   creating: istio-1.17.1/manifests/charts/gateway/
  inflating: istio-1.17.1/manifests/charts/gateway/Chart.yaml  
  inflating: istio-1.17.1/manifests/charts/gateway/README.md
   creating: istio-1.17.1/manifests/charts/gateway/templates/
  inflating: istio-1.17.1/manifests/charts/gateway/templates/NOTES.txt
  inflating: istio-1.17.1/manifests/charts/gateway/templates/_helpers.tpl  
  inflating: istio-1.17.1/manifests/charts/gateway/templates/deployment.yaml
  inflating: istio-1.17.1/manifests/charts/gateway/templates/hpa.yaml  
  inflating: istio-1.17.1/manifests/charts/gateway/templates/role.yaml  
  inflating: istio-1.17.1/manifests/charts/gateway/templates/service.yaml
  inflating: istio-1.17.1/manifests/charts/gateway/templates/serviceaccount.yaml
  inflating: istio-1.17.1/manifests/charts/gateway/values.schema.json  
  inflating: istio-1.17.1/manifests/charts/gateway/values.yaml
   creating: istio-1.17.1/manifests/charts/gateways/
   creating: istio-1.17.1/manifests/charts/gateways/istio-egress/
  inflating: istio-1.17.1/manifests/charts/gateways/istio-egress/Chart.yaml
  inflating: istio-1.17.1/manifests/charts/gateways/istio-egress/NOTES.txt
   creating: istio-1.17.1/manifests/charts/gateways/istio-egress/templates/
  inflating: istio-1.17.1/manifests/charts/gateways/istio-egress/templates/_affinity.tpl  
  inflating: istio-1.17.1/manifests/charts/gateways/istio-egress/templates/autoscale.yaml  
  inflating: istio-1.17.1/manifests/charts/gateways/istio-egress/templates/deployment.yaml
  inflating: istio-1.17.1/manifests/charts/gateways/istio-egress/templates/injected-deployment.yaml  
  inflating: istio-1.17.1/manifests/charts/gateways/istio-egress/templates/poddisruptionbudget.yaml
  inflating: istio-1.17.1/manifests/charts/gateways/istio-egress/templates/role.yaml
  inflating: istio-1.17.1/manifests/charts/gateways/istio-egress/templates/rolebindings.yaml
  inflating: istio-1.17.1/manifests/charts/gateways/istio-egress/templates/service.yaml
  inflating: istio-1.17.1/manifests/charts/gateways/istio-egress/templates/serviceaccount.yaml
  inflating: istio-1.17.1/manifests/charts/gateways/istio-egress/values.yaml  
   creating: istio-1.17.1/manifests/charts/gateways/istio-ingress/
  inflating: istio-1.17.1/manifests/charts/gateways/istio-ingress/Chart.yaml  
  inflating: istio-1.17.1/manifests/charts/gateways/istio-ingress/NOTES.txt
   creating: istio-1.17.1/manifests/charts/gateways/istio-ingress/templates/
  inflating: istio-1.17.1/manifests/charts/gateways/istio-ingress/templates/_affinity.tpl
  inflating: istio-1.17.1/manifests/charts/gateways/istio-ingress/templates/autoscale.yaml
  inflating: istio-1.17.1/manifests/charts/gateways/istio-ingress/templates/deployment.yaml
  inflating: istio-1.17.1/manifests/charts/gateways/istio-ingress/templates/injected-deployment.yaml  
  inflating: istio-1.17.1/manifests/charts/gateways/istio-ingress/templates/poddisruptionbudget.yaml
  inflating: istio-1.17.1/manifests/charts/gateways/istio-ingress/templates/role.yaml  
  inflating: istio-1.17.1/manifests/charts/gateways/istio-ingress/templates/rolebindings.yaml
  inflating: istio-1.17.1/manifests/charts/gateways/istio-ingress/templates/service.yaml  
  inflating: istio-1.17.1/manifests/charts/gateways/istio-ingress/templates/serviceaccount.yaml
  inflating: istio-1.17.1/manifests/charts/gateways/istio-ingress/values.yaml  
  inflating: istio-1.17.1/manifests/charts/install-OpenShift.md
   creating: istio-1.17.1/manifests/charts/istio-cni/
  inflating: istio-1.17.1/manifests/charts/istio-cni/Chart.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-cni/README.md
   creating: istio-1.17.1/manifests/charts/istio-cni/templates/
  inflating: istio-1.17.1/manifests/charts/istio-cni/templates/NOTES.txt
  inflating: istio-1.17.1/manifests/charts/istio-cni/templates/clusterrole.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-cni/templates/clusterrolebinding.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-cni/templates/configmap-cni.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-cni/templates/daemonset.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-cni/templates/resourcequota.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-cni/templates/serviceaccount.yaml
  inflating: istio-1.17.1/manifests/charts/istio-cni/values.yaml
   creating: istio-1.17.1/manifests/charts/istio-control/
   creating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/Chart.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/README.md
   creating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/files/
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/files/gateway-injection-template.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/files/gen-istio.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/files/grpc-agent.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/files/grpc-simple.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/files/injection-template.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/kustomization.yaml  
   creating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/NOTES.txt
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/autoscale.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/clusterrole.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/clusterrolebinding.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/configmap-jwks.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/configmap.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/deployment.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/istiod-injector-configmap.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/mutatingwebhook.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/poddisruptionbudget.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/reader-clusterrole.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/reader-clusterrolebinding.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/revision-tags.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/role.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/rolebinding.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/service.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/serviceaccount.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/telemetryv2_1.13.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/telemetryv2_1.14.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/telemetryv2_1.15.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/telemetryv2_1.16.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/telemetryv2_1.17.yaml  
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/templates/validatingwebhookconfiguration.yaml
  inflating: istio-1.17.1/manifests/charts/istio-control/istio-discovery/values.yaml  
   creating: istio-1.17.1/manifests/charts/istio-operator/
  inflating: istio-1.17.1/manifests/charts/istio-operator/Chart.yaml  
   creating: istio-1.17.1/manifests/charts/istio-operator/crds/
  inflating: istio-1.17.1/manifests/charts/istio-operator/crds/crd-operator.yaml
   creating: istio-1.17.1/manifests/charts/istio-operator/files/
  inflating: istio-1.17.1/manifests/charts/istio-operator/files/gen-operator.yaml  
   creating: istio-1.17.1/manifests/charts/istio-operator/templates/
  inflating: istio-1.17.1/manifests/charts/istio-operator/templates/clusterrole.yaml
  inflating: istio-1.17.1/manifests/charts/istio-operator/templates/clusterrole_binding.yaml
  inflating: istio-1.17.1/manifests/charts/istio-operator/templates/crds.yaml
  inflating: istio-1.17.1/manifests/charts/istio-operator/templates/deployment.yaml
  inflating: istio-1.17.1/manifests/charts/istio-operator/templates/service.yaml
  inflating: istio-1.17.1/manifests/charts/istio-operator/templates/service_account.yaml
  inflating: istio-1.17.1/manifests/charts/istio-operator/values.yaml
   creating: istio-1.17.1/manifests/charts/istiod-remote/
  inflating: istio-1.17.1/manifests/charts/istiod-remote/Chart.yaml  
  inflating: istio-1.17.1/manifests/charts/istiod-remote/NOTES.txt
   creating: istio-1.17.1/manifests/charts/istiod-remote/files/
  inflating: istio-1.17.1/manifests/charts/istiod-remote/files/gateway-injection-template.yaml  
  inflating: istio-1.17.1/manifests/charts/istiod-remote/files/injection-template.yaml  
   creating: istio-1.17.1/manifests/charts/istiod-remote/templates/
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/clusterrole.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/clusterrolebinding.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/configmap.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/crd-all.gen.yaml  
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/crd-operator.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/default.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/endpoints.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/istiod-injector-configmap.yaml  
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/mutatingwebhook.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/reader-clusterrole.yaml  
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/reader-clusterrolebinding.yaml  
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/reader-serviceaccount.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/role.yaml  
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/rolebinding.yaml  
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/serviceaccount.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/services.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/telemetryv2_1.13.yaml  
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/telemetryv2_1.14.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/telemetryv2_1.15.yaml  
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/telemetryv2_1.16.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/telemetryv2_1.17.yaml
  inflating: istio-1.17.1/manifests/charts/istiod-remote/templates/validatingwebhookconfiguration.yaml  
  inflating: istio-1.17.1/manifests/charts/istiod-remote/values.yaml
   creating: istio-1.17.1/manifests/examples/
   creating: istio-1.17.1/manifests/examples/customresource/
  inflating: istio-1.17.1/manifests/examples/customresource/istio_v1alpha1_istiooperator_cr.yaml
   creating: istio-1.17.1/manifests/examples/user-gateway/
  inflating: istio-1.17.1/manifests/examples/user-gateway/ingress-gateway-only.yaml
   creating: istio-1.17.1/manifests/profiles/
  inflating: istio-1.17.1/manifests/profiles/ambient.yaml  
  inflating: istio-1.17.1/manifests/profiles/default.yaml
  inflating: istio-1.17.1/manifests/profiles/demo.yaml  
  inflating: istio-1.17.1/manifests/profiles/empty.yaml
  inflating: istio-1.17.1/manifests/profiles/external.yaml  
  inflating: istio-1.17.1/manifests/profiles/minimal.yaml
  inflating: istio-1.17.1/manifests/profiles/openshift.yaml  
  inflating: istio-1.17.1/manifests/profiles/preview.yaml
  inflating: istio-1.17.1/manifests/profiles/remote.yaml  
   creating: istio-1.17.1/samples/
  inflating: istio-1.17.1/samples/README.md
   creating: istio-1.17.1/samples/addons/
  inflating: istio-1.17.1/samples/addons/README.md
   creating: istio-1.17.1/samples/addons/extras/
  inflating: istio-1.17.1/samples/addons/extras/prometheus-operator.yaml
  inflating: istio-1.17.1/samples/addons/extras/prometheus_vm.yaml
  inflating: istio-1.17.1/samples/addons/extras/prometheus_vm_tls.yaml
  inflating: istio-1.17.1/samples/addons/extras/skywalking.yaml  
  inflating: istio-1.17.1/samples/addons/extras/zipkin.yaml
  inflating: istio-1.17.1/samples/addons/grafana.yaml  
  inflating: istio-1.17.1/samples/addons/jaeger.yaml
  inflating: istio-1.17.1/samples/addons/kiali.yaml  
  inflating: istio-1.17.1/samples/addons/prometheus.yaml
   creating: istio-1.17.1/samples/bookinfo/
  inflating: istio-1.17.1/samples/bookinfo/README.md
  inflating: istio-1.17.1/samples/bookinfo/build_push_update_images.sh
  inflating: istio-1.17.1/samples/bookinfo/demo-profile-no-gateways.yaml  
   creating: istio-1.17.1/samples/bookinfo/gateway-api/
  inflating: istio-1.17.1/samples/bookinfo/gateway-api/bookinfo-gateway.yaml  
  inflating: istio-1.17.1/samples/bookinfo/gateway-api/route-all-v1.yaml
  inflating: istio-1.17.1/samples/bookinfo/gateway-api/route-reviews-50-v3.yaml  
  inflating: istio-1.17.1/samples/bookinfo/gateway-api/route-reviews-v1.yaml  
  inflating: istio-1.17.1/samples/bookinfo/gateway-api/route-reviews-v3.yaml
   creating: istio-1.17.1/samples/bookinfo/networking/
  inflating: istio-1.17.1/samples/bookinfo/networking/bookinfo-gateway.yaml  
  inflating: istio-1.17.1/samples/bookinfo/networking/certmanager-gateway.yaml
  inflating: istio-1.17.1/samples/bookinfo/networking/destination-rule-all-mtls.yaml
  inflating: istio-1.17.1/samples/bookinfo/networking/destination-rule-all.yaml
  inflating: istio-1.17.1/samples/bookinfo/networking/destination-rule-reviews.yaml  
  inflating: istio-1.17.1/samples/bookinfo/networking/egress-rule-google-apis.yaml
  inflating: istio-1.17.1/samples/bookinfo/networking/fault-injection-details-v1.yaml  
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-all-v1.yaml
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-details-v2.yaml
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-ratings-db.yaml
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-ratings-mysql-vm.yaml  
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-ratings-mysql.yaml
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-ratings-test-abort.yaml  
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-ratings-test-delay.yaml  
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-reviews-50-v3.yaml
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-reviews-80-20.yaml  
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-reviews-90-10.yaml
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-reviews-jason-v2-v3.yaml  
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-reviews-test-v2.yaml
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-reviews-v2-v3.yaml  
  inflating: istio-1.17.1/samples/bookinfo/networking/virtual-service-reviews-v3.yaml
   creating: istio-1.17.1/samples/bookinfo/platform/
   creating: istio-1.17.1/samples/bookinfo/platform/kube/
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/README.md
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-certificate.yaml  
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-db.yaml
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-details-v2.yaml  
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-details.yaml
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-ingress.yaml
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-mysql.yaml
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-ratings-discovery.yaml
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-ratings-v2-mysql-vm.yaml
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-ratings-v2-mysql.yaml
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-ratings-v2.yaml
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-ratings.yaml  
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-reviews-v2.yaml
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo-versions.yaml  
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/bookinfo.yaml
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/cleanup.sh  
  inflating: istio-1.17.1/samples/bookinfo/platform/kube/productpage-nodeport.yaml
   creating: istio-1.17.1/samples/bookinfo/policy/
  inflating: istio-1.17.1/samples/bookinfo/policy/productpage_envoy_ratelimit.yaml
   creating: istio-1.17.1/samples/bookinfo/src/
  inflating: istio-1.17.1/samples/bookinfo/src/build-services.sh
   creating: istio-1.17.1/samples/bookinfo/src/details/
   creating: istio-1.17.1/samples/bookinfo/src/mongodb/
  inflating: istio-1.17.1/samples/bookinfo/src/mongodb/ratings_data.json
  inflating: istio-1.17.1/samples/bookinfo/src/mongodb/script.sh  
   creating: istio-1.17.1/samples/bookinfo/src/mysql/
   creating: istio-1.17.1/samples/bookinfo/src/productpage/
  inflating: istio-1.17.1/samples/bookinfo/src/productpage/requirements.txt
   creating: istio-1.17.1/samples/bookinfo/src/productpage/static/
   creating: istio-1.17.1/samples/bookinfo/src/productpage/static/bootstrap/
   creating: istio-1.17.1/samples/bookinfo/src/productpage/static/bootstrap/css/
   creating: istio-1.17.1/samples/bookinfo/src/productpage/static/bootstrap/fonts/
   creating: istio-1.17.1/samples/bookinfo/src/productpage/static/bootstrap/js/
   creating: istio-1.17.1/samples/bookinfo/src/productpage/templates/
  inflating: istio-1.17.1/samples/bookinfo/src/productpage/test-requirements.txt  
   creating: istio-1.17.1/samples/bookinfo/src/productpage/tests/
   creating: istio-1.17.1/samples/bookinfo/src/productpage/tests/unit/
   creating: istio-1.17.1/samples/bookinfo/src/ratings/
  inflating: istio-1.17.1/samples/bookinfo/src/ratings/package.json
   creating: istio-1.17.1/samples/bookinfo/src/reviews/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-application/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-application/src/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-application/src/main/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-application/src/main/java/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-application/src/main/java/application/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-application/src/main/java/application/rest/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-application/src/main/webapp/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-application/src/main/webapp/WEB-INF/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-application/src/test/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-application/src/test/java/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-application/src/test/java/test/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-wlpcfg/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-wlpcfg/servers/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-wlpcfg/servers/LibertyProjectServer/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-wlpcfg/shared/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-wlpcfg/src/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-wlpcfg/src/test/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-wlpcfg/src/test/java/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-wlpcfg/src/test/java/it/
   creating: istio-1.17.1/samples/bookinfo/src/reviews/reviews-wlpcfg/src/test/java/it/rest/
  inflating: istio-1.17.1/samples/bookinfo/swagger.yaml  
   creating: istio-1.17.1/samples/certs/
  inflating: istio-1.17.1/samples/certs/README.md  
  inflating: istio-1.17.1/samples/certs/ca-cert-alt.pem
  inflating: istio-1.17.1/samples/certs/ca-cert.pem  
  inflating: istio-1.17.1/samples/certs/ca-key-alt.pem
  inflating: istio-1.17.1/samples/certs/ca-key.pem
  inflating: istio-1.17.1/samples/certs/cert-chain-alt.pem  
  inflating: istio-1.17.1/samples/certs/cert-chain.pem  
  inflating: istio-1.17.1/samples/certs/generate-workload.sh  
  inflating: istio-1.17.1/samples/certs/leaf-workload-bar-cert.pem  
  inflating: istio-1.17.1/samples/certs/leaf-workload-foo-cert.pem
  inflating: istio-1.17.1/samples/certs/root-cert-alt.pem  
  inflating: istio-1.17.1/samples/certs/root-cert.pem
  inflating: istio-1.17.1/samples/certs/workload-bar-cert.pem
  inflating: istio-1.17.1/samples/certs/workload-bar-key.pem
  inflating: istio-1.17.1/samples/certs/workload-bar-root-certs.pem  
  inflating: istio-1.17.1/samples/certs/workload-foo-cert.pem  
  inflating: istio-1.17.1/samples/certs/workload-foo-key.pem
  inflating: istio-1.17.1/samples/certs/workload-foo-root-certs.pem
   creating: istio-1.17.1/samples/cicd/
   creating: istio-1.17.1/samples/cicd/skaffold/
  inflating: istio-1.17.1/samples/cicd/skaffold/README.md
  inflating: istio-1.17.1/samples/cicd/skaffold/skaffold.yaml  
   creating: istio-1.17.1/samples/custom-bootstrap/
  inflating: istio-1.17.1/samples/custom-bootstrap/README.md  
  inflating: istio-1.17.1/samples/custom-bootstrap/custom-bootstrap.yaml
  inflating: istio-1.17.1/samples/custom-bootstrap/example-app.yaml
   creating: istio-1.17.1/samples/extauthz/
  inflating: istio-1.17.1/samples/extauthz/README.md  
   creating: istio-1.17.1/samples/extauthz/cmd/
   creating: istio-1.17.1/samples/extauthz/cmd/extauthz/
   creating: istio-1.17.1/samples/extauthz/docker/
  inflating: istio-1.17.1/samples/extauthz/ext-authz.yaml  
  inflating: istio-1.17.1/samples/extauthz/local-ext-authz.yaml
   creating: istio-1.17.1/samples/external/
  inflating: istio-1.17.1/samples/external/README.md
  inflating: istio-1.17.1/samples/external/aptget.yaml  
  inflating: istio-1.17.1/samples/external/github.yaml  
  inflating: istio-1.17.1/samples/external/pypi.yaml
   creating: istio-1.17.1/samples/grpc-echo/
  inflating: istio-1.17.1/samples/grpc-echo/README.md
  inflating: istio-1.17.1/samples/grpc-echo/grpc-echo.yaml
   creating: istio-1.17.1/samples/health-check/
  inflating: istio-1.17.1/samples/health-check/liveness-command.yaml  
  inflating: istio-1.17.1/samples/health-check/liveness-http-same-port.yaml
   creating: istio-1.17.1/samples/helloworld/
  inflating: istio-1.17.1/samples/helloworld/README.md
   creating: istio-1.17.1/samples/helloworld/gateway-api/
  inflating: istio-1.17.1/samples/helloworld/gateway-api/README.md
  inflating: istio-1.17.1/samples/helloworld/gateway-api/helloworld-gateway.yaml  
  inflating: istio-1.17.1/samples/helloworld/gateway-api/helloworld-route.yaml  
  inflating: istio-1.17.1/samples/helloworld/gateway-api/helloworld-versions.yaml  
  inflating: istio-1.17.1/samples/helloworld/gen-helloworld.sh
  inflating: istio-1.17.1/samples/helloworld/helloworld-gateway.yaml  
  inflating: istio-1.17.1/samples/helloworld/helloworld.yaml  
  inflating: istio-1.17.1/samples/helloworld/loadgen.sh  
   creating: istio-1.17.1/samples/helloworld/src/
  inflating: istio-1.17.1/samples/helloworld/src/build_service.sh  
  inflating: istio-1.17.1/samples/helloworld/src/requirements.txt
   creating: istio-1.17.1/samples/httpbin/
  inflating: istio-1.17.1/samples/httpbin/README.md  
  inflating: istio-1.17.1/samples/httpbin/httpbin-gateway.yaml
  inflating: istio-1.17.1/samples/httpbin/httpbin-nodeport.yaml
  inflating: istio-1.17.1/samples/httpbin/httpbin-vault.yaml  
  inflating: istio-1.17.1/samples/httpbin/httpbin.yaml
   creating: istio-1.17.1/samples/httpbin/sample-client/
  inflating: istio-1.17.1/samples/httpbin/sample-client/fortio-deploy.yaml  
   creating: istio-1.17.1/samples/jwt-server/
  inflating: istio-1.17.1/samples/jwt-server/jwt-server.yaml  
   creating: istio-1.17.1/samples/jwt-server/src/
  inflating: istio-1.17.1/samples/jwt-server/src/Makefile
   creating: istio-1.17.1/samples/jwt-server/testdata/
   creating: istio-1.17.1/samples/kind-lb/
  inflating: istio-1.17.1/samples/kind-lb/README.md  
  inflating: istio-1.17.1/samples/kind-lb/setupkind.sh
   creating: istio-1.17.1/samples/multicluster/
  inflating: istio-1.17.1/samples/multicluster/README.md
  inflating: istio-1.17.1/samples/multicluster/expose-istiod-https.yaml
  inflating: istio-1.17.1/samples/multicluster/expose-istiod.yaml  
  inflating: istio-1.17.1/samples/multicluster/expose-services.yaml  
  inflating: istio-1.17.1/samples/multicluster/gen-eastwest-gateway.sh
   creating: istio-1.17.1/samples/open-telemetry/
  inflating: istio-1.17.1/samples/open-telemetry/README.md  
  inflating: istio-1.17.1/samples/open-telemetry/otel.yaml
   creating: istio-1.17.1/samples/operator/
  inflating: istio-1.17.1/samples/operator/cni-on.yaml
  inflating: istio-1.17.1/samples/operator/default-install.yaml  
  inflating: istio-1.17.1/samples/operator/pilot-advanced-override.yaml
  inflating: istio-1.17.1/samples/operator/pilot-k8s.yaml  
  inflating: istio-1.17.1/samples/operator/values-global.yaml
  inflating: istio-1.17.1/samples/operator/values-pilot.yaml
   creating: istio-1.17.1/samples/ratelimit/
  inflating: istio-1.17.1/samples/ratelimit/rate-limit-service.yaml  
   creating: istio-1.17.1/samples/security/
   creating: istio-1.17.1/samples/security/psp/
  inflating: istio-1.17.1/samples/security/psp/sidecar-psp.yaml  
   creating: istio-1.17.1/samples/security/spire/
  inflating: istio-1.17.1/samples/security/spire/README.md
  inflating: istio-1.17.1/samples/security/spire/istio-spire-config.yaml  
  inflating: istio-1.17.1/samples/security/spire/sleep-spire.yaml
  inflating: istio-1.17.1/samples/security/spire/spire-quickstart.yaml
   creating: istio-1.17.1/samples/sleep/
  inflating: istio-1.17.1/samples/sleep/README.md  
  inflating: istio-1.17.1/samples/sleep/sleep-vault.yaml
  inflating: istio-1.17.1/samples/sleep/sleep.yaml  
   creating: istio-1.17.1/samples/tcp-echo/
  inflating: istio-1.17.1/samples/tcp-echo/README.md
   creating: istio-1.17.1/samples/tcp-echo/gateway-api/
  inflating: istio-1.17.1/samples/tcp-echo/gateway-api/tcp-echo-20-v2.yaml
  inflating: istio-1.17.1/samples/tcp-echo/gateway-api/tcp-echo-all-v1.yaml  
   creating: istio-1.17.1/samples/tcp-echo/src/
  inflating: istio-1.17.1/samples/tcp-echo/tcp-echo-20-v2.yaml  
  inflating: istio-1.17.1/samples/tcp-echo/tcp-echo-all-v1.yaml
  inflating: istio-1.17.1/samples/tcp-echo/tcp-echo-services.yaml
  inflating: istio-1.17.1/samples/tcp-echo/tcp-echo.yaml  
   creating: istio-1.17.1/samples/wasm_modules/
  inflating: istio-1.17.1/samples/wasm_modules/README.md
   creating: istio-1.17.1/samples/wasm_modules/header_injector/
  inflating: istio-1.17.1/samples/wasm_modules/header_injector/Makefile
   creating: istio-1.17.1/samples/websockets/
  inflating: istio-1.17.1/samples/websockets/README.md  
  inflating: istio-1.17.1/samples/websockets/app.yaml
  inflating: istio-1.17.1/samples/websockets/route.yaml  
   creating: istio-1.17.1/tools/
  inflating: istio-1.17.1/tools/_istioctl  
   creating: istio-1.17.1/tools/certs/
  inflating: istio-1.17.1/tools/certs/Makefile.k8s.mk
  inflating: istio-1.17.1/tools/certs/Makefile.selfsigned.mk
  inflating: istio-1.17.1/tools/certs/README.md
  inflating: istio-1.17.1/tools/certs/common.mk
  inflating: istio-1.17.1/tools/istioctl.bash
```

## Langkah 5: Masuk ke folder

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes$ cd istio-1.17.1/
```

## Langkah 6: Set PATH dan Install Istio

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/istio-1.17.1$ export PATH=$PWD/bin:$PATH
```

## Langkah 7: Menginstal inti Istio.
```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/istio-1.17.1$ istioctl install --set profile=demo -y
✔ Istio core installed
✔ Istiod installed
✔ Ingress gateways installed
✔ Egress gateways installed
✔ Installation complete                                                                                                                                                                                       Making this installation the default for injection and validation.

Thank you for installing Istio 1.17.  Please take a few minutes to tell us about your install/upgrade experience!  https://forms.gle/hMHGiwZHPU7UQRWe9

MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/istio-1.17.1
```

## Langkah 8: Label Default Namespace untuk Injection

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/istio-1.17.1$ kubectl label namespace default istio-injection=enabled
namespace/default labeled
```

## Langkah 9: Install RabbitMQ dengan Helm

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/istio-1.17.1$ helm repo add bitnami https://charts.bitnami.com/bitnami
"bitnami" has been added to your repositories
```

## Langkah 10: Update repo

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/istio-1.17.1$ helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "bitnami" chart repository
Update Complete. ⎈Happy Helming!⎈
```

## Langkah 11: Install
```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/istio-1.17.1$ helm install my-rabbitmq bitnami/rabbitmq
NAME: my-rabbitmq
LAST DEPLOYED: Wed Oct 11 13:19:46 2023
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
CHART NAME: rabbitmq
CHART VERSION: 12.2.0
APP VERSION: 3.12.6** Please be patient while the chart is being deployed **

Credentials:
    echo "Username      : user"
    echo "Password      : $(kubectl get secret --namespace default my-rabbitmq -o jsonpath="{.data.rabbitmq-password}" | base64 -d)"
    echo "ErLang Cookie : $(kubectl get secret --namespace default my-rabbitmq -o jsonpath="{.data.rabbitmq-erlang-cookie}" | base64 -d)"

Note that the credentials are saved in persistent volume claims and will not be changed upon upgrade or reinstallation unless the persistent volume claim has been deleted. If this is not the first installation of this chart, the credentials may not be valid.
This is applicable when no passwords are set and therefore the random password is autogenerated. In case of using a fixed password, you should specify it when upgrading.
More information about the credentials may be found at https://docs.bitnami.com/general/how-to/troubleshoot-helm-chart-issues/#credential-errors-while-upgrading-chart-releases.

RabbitMQ can be accessed within the cluster on port 5672 at my-rabbitmq.default.svc.cluster.local

To access for outside the cluster, perform the following steps:

To Access the RabbitMQ AMQP port:

    echo "URL : amqp://127.0.0.1:5672/"
    kubectl port-forward --namespace default svc/my-rabbitmq 5672:5672

To Access the RabbitMQ Management interface:

    echo "URL : http://127.0.0.1:15672/"
    kubectl port-forward --namespace default svc/my-rabbitmq 15672:15672
```

## Langkah 12: Masuk folder shipping-service

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/istio-1.17.1$ cd ../shipping-service
```

## Langkah 13: Konfigurasi Konfigurasi Shipping Service

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/shipping-service$ kubectl apply -f .
deployment.apps/order-service-deploy created
gateway.networking.istio.io/order-service-gw created
service/order-service-svc created
virtualservice.networking.istio.io/order-service-vs created
```

## Langkah 14: Masuk folder order-service

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/shipping-service$ cd ../order-service
```

## Langkah 15: Konfigurasi Konfigurasi Order Service

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/order-service$ kubectl apply -f .
deployment.apps/order-service-deploy created
gateway.networking.istio.io/order-service-gw created
service/order-service-svc created
virtualservice.networking.istio.io/order-service-vs created
```

## Langkah 16: Port Forward ke RabbitMQ Management Interface

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/order-service$ kubectl port-forward --namespace default svc/my-rabbitmq 15672:15672
Forwarding from 127.0.0.1:15672 -> 15672
Forwarding from [::1]:15672 -> 15672
Handling connection for 15672
Handling connection for 15672
Handling connection for 15672
```

## Langkah 17: Mendapatkan password

buka terminal baru
```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/order-service$ echo "$(kubectl get secret --namespace default my-rabbitmq -o jsonpath="{.data.rabbitmq-password}" | base64 -d)"
2lUdRqdqTLMOBVmV
```
Anda kemudian mendapatkan password dari secret RabbitMQ.

copy 2lUdRqdqTLMOBVmV

buka: http://127.0.0.1:15672

__username:__ user

__password:__ 2lUdRqdqTLMOBVmV

## Langkah 18: Port Forward ke Istio Ingress Gateway

```
MSI GAMING@MSI MINGW64 /d/tugas3/kubernetes/order-service$ kubectl port-forward svc/istio-ingressgateway -n istio-system 80:80
Forwarding from 127.0.0.1:80 -> 8080
Forwarding from [::1]:80 -> 8080
Handling connection for 80
Handling connection for 80
Handling connection for 80
Handling connection for 80
```

buka: http://127.0.0.1:80/order

