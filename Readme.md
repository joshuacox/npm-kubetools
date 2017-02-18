
# kubetools

Streamplace does a lot of Javascript things and a lot of Kubernetes things. It helps us to have
the Kubernetes CLI tools on npm, because that's how we handle dependencies in all of our
Javascript projects.

So, this project does that for the following Kubernetes-related projects:

* kubectl `npm install -g kubectl-cli`
* minikube `npm install -g minikube-cli`
* helm `npm install -g helm-cli`

If you find this useful, we'd love more tools!

## How it works?

This project publishes manifests for each of those tools (e.g. packages/kubectl/manifest.json)
that contain URLs and SHA256 hashes for each supported architecture/platform combination. It also
publishes `download.js` alongside them, which parses the version in `package.json` and downloads
the appropriate version from `manifest.json`.

## CI

There's a Travis build set to run hourly that runs `build-manifests.sh` and errors if there's a
new version of any of our binaries available. For now, that just sends an email to me and I update
the script manually. Maybe eventually we'll do some kind of sweet auto-update.


# LICENSE

The license behind this project is MIT. The license behind all three tools is Apache-2.0.
git@github.com:kubernetes/kubernetes.git
