# Rollout #

If you inspect the Pod you will see the running container is version 1.9

`kubectl describe pod hello | grep "Image:"`{{execute}}

A newer version of the container is 1.10.

An important aspect of Kubernetes is your users may benefit from the ideas of [continuous deployment](https://martinfowler.com/bliki/ContinuousDelivery.html). A fundamental way to approach this is with Kubernetes rollouts.

There are two approaches. A precise surgical way is with the _set image_ command. This will modify the image version for the Pod in the Deployment.

`kubectl set image deployment/hello hello=echoserver:1.10 --all`{{execute}}

Now, the Pod inspection will report the updated container.

`kubectl describe pod hello | grep "Image:"`{{execute}}

Another way is to modify the YAML then apply the change with the _update_ command.  

Restore the Pod's container 3
image the version back to the original version

`kubectl replace -f echoserver.yaml`{{execute}}

Verify the version has been restored.

`kubectl describe pod hello | grep "Image:"`{{execute}}

Then, look up the resource, change the image version with SED, then pipe modified stream to the _replace_ command.

`kubectl get deployment hello -o yaml | sed 's/\(image: echoserver\):.*$/\1:1.10/' | kubectl replace -f -`{{execute}}

Verify the version has been upgraded using the _replace_ command.

`kubectl describe pod hello | grep "Image:"`{{execute}}