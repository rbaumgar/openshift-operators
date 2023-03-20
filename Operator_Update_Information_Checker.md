The Operator Update Information Checker

*By Robert Baumgartner, Red Hat Austria, March 2023*

# Summery
Recenetly Red Hat ha released a tool at the Customer Portal Labs which can give a very detailed information abount Operators and available updates, supported versions, and much more.

The name is **Red Hat OpenShift Container Platform Operator Update Information Checker**

Where to find:
[Customer Portal Labs](https://access.redhat.com/labs/)

![Customer Portal Labs](images/labs01.png)

## Overview
When you start the **Operator Update Information Checker** you will get a long list of currently available operators. 
At the time of writing I found 108 (!) pages.

Supported Openshift versions 4.6+

![Operator Overview](images/labs02.png)

Now can start to twaek the output.

## Tweak / Filter the output
You can start by selecting a specific Openshift version. Or may be two, when you are interested which operator is available in your current version and the version you are upgrading to.

You can also start typing an operator name to get only a specific operator you are currently interested in.

![Logging Operator details](images/labs03.png)

In this example screen you see the two channel stable and stable-5.5 of the logging operator in OpenShift version 4.12.

- For the stable channel the current operator version is 4.6.3. And this version will be supported until OpenShift version 4.14. (MaxOCP)
- For the stable-5.5 channel the current operator version is 5.5.8. And this operator will not be supported in Openshift after 4.12 as of now.

## Many chennels
When you select amq-streams (Kafka) you will find many channels available.

![AMQ Streams/Kafka Operator details](images/labs04.png)

- The stable channel points to version v2.3.0-1, the latest version.
- The amq-streams-2.2.x channel points to version v2.2.1-0
- The amq-streams-2.x channel points to v2.3.0.1

Non of this operator channel has defined a latest version. This does not mean it will be supported forever. You have to look at the release information!

## Version change with OpenShift version

![MetalsLB Operator details](images/labs05.png)

When you select MetalLB operator you will see an example of an operator with just one channel. And when you upgrade from from OpenShift version 4.10 to 4.12 the operator will be automatically upgraded to a new version. (4.12.0-202303021943)

## API Interface
- Is their an API available/planed? json/jaml output
- How to call?
- Would be nice, to get only the operators I am running on my cluster
- How to select a list of operators?

```shell
$ oc get subscriptions.operators.coreos.com -A -o custom-columns='NAME:.metadata.name,CHANNEL:.spec.channel' --no-headers |sort
amq-streams                                                         stable
costmanagement-metrics-operator                                     stable
devworkspace-operator-fast-redhat-operators-openshift-marketplace   fast
jaeger-product                                                      stable
netobserv-operator                                                  v0.2.x
openshift-cert-manager-operator                                     tech-preview
openshift-gitops-operator                                           latest
openshift-pipelines-operator-rh                                     latest
opentelemetry-product                                               stable
red-hat-camel-k                                                     latest
rhsso-operator-stable-redhat-operators-openshift-marketplace        stable
serverless-operator                                                 stable
web-terminal                                                        fast
```




