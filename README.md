![Strimzi](https://developers.redhat.com/blog/wp-content/uploads/2018/05/strimzilogo_stacked_default_450px.png)

# Kafka Workshop

### The purpose of this workshop is to utilize the components within the Red Hat Integration portfolio to integrate a traditional application with more applications within OpenShift through kafka. 

---

## The instructions below should be completed by the instructor to demonstrate the deployment of Kafka as a centralized service
 
**Note:** The following instructions deploy AMQ Streams leveraging the Strimzi operator. Additionally, it deploys a Java application that leverages Kafka with a built-in consumer and producer. It is capable of sending messages to AMQ Streams using REST endpoints

## To install AMQ Streams:

1) git clone https://github.com/roller1187/amq-examples.git

2) cd ./amq-examples

3) Login to OpenShift:

```sh
oc login <cluster URL>
```
4) Create a new project:

```sh 
oc new-project kafka
```

5) Load the new project:
```sh
oc project kafka
```

6) Configure access for the Strimzi operator namespace:

```sh
oc adm policy add-cluster-role-to-user strimzi-cluster-operator-namespaced --serviceaccount strimzi-cluster-operator -n kafka
```
```sh
oc adm policy add-cluster-role-to-user strimzi-entity-operator --serviceaccount strimzi-cluster-operator -n kafka
```
```sh
oc adm policy add-cluster-role-to-user strimzi-topic-operator --serviceaccount strimzi-cluster-operator -n kafka
```

7) oc apply -f https://github.com/roller1187/kafka-workshop/master/install/cluster-operator/

## To configure Kafka:

1) oc apply -f https://raw.githubusercontent.com/roller1187/kafka-workshop/master/setup/my-cluster.yaml

**Wait until all 5 replicas of Kafka and Zookeeper are online**

## Enjoy!
