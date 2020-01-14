# OpenShift Useful Commands Cheat Sheet

## Ver ruta de la consola de OpenShift

```bash
echo -en "\n\nhttps://`oc get route console -o template --template {{.spec.host}} -n openshift-console`\n"
```

## Quotas

Examinar quotas usadas por los pods

```bash
oc get pods --field-selector=status.phase=Running -o json | jq '.items[] | {name: .metadata.name, res: .spec.containers[].resources}'
```

## Pods

### Ver en tiempo real a los pods

```bash
watch oc get pods
```

### Correr un pod de manera individual

```bash
oc run rhel-tools -it --image=rhel7/rhel-tools --generator=run-pod/v1
```

## Deployment Configs

Cambiar o añadir resources a un DC

```bash
oc set resources dc cakephp-mysql-example --limits=memory=1Gi
oc set resources dc jenkins --limits=cpu=2 --requests=cpu=1,memory=2Gideploymentconfig.apps.openshift.io/jenkins resource requirements updated
```

## Routes

Recoger solo la ruta expuesta
```bash
oc get route jenkins -o jsonpath='{.spec.host}{"\n"}'
```

## Triggers

Apagar todos los triggers
```bash
oc set triggers dc openshift-tasks --manual
```
