**Note: This step is under construction.**

You can trigger a Kubeless function using the [PubSub mechanism](https://kubeless.io/docs/pubsub-functions/). The PubSub function is expected to consume input messages from a predefined topic from a messaging system. Kubeless currently supports consuming events from Kafka and NATS messaging systems.

## Install Kafka ##

Add the repo where the Kafka chart can be referenced from

`helm repo add incubator http://storage.googleapis.com/kubernetes-charts-incubator`{{execute}}

and install the Kafka chart.

`helm install incubator/kafka --namespace kubeless --name kafka`{{execute}}

(Next todo, instructions on consuming events)