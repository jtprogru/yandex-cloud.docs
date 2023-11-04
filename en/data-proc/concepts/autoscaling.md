# Autoscaling of subclusters


{% note info %}

Autoscaling of subclusters is supported for {{ dataproc-full-name }} clusters version 1.4 and higher.

{% endnote %}



{{ dataproc-full-name }} supports autoscaling of [data processing subclusters](../concepts/index.md) based on metrics received by [{{ monitoring-full-name }}](../../monitoring/concepts/index.md):


* If the metric value exceeds the specified threshold, new hosts are added to a subcluster. You can use them in a YARN cluster running Apache Spark or Apache Hive as soon as the host status changes to **Alive**.
* If the value of the key metric falls below the specified threshold, the processes of [decommissioning](decommission.md) and removing redundant hosts are started sequentially in the subcluster.

Read more about autoscaling mechanisms in the [{{ ig-name }} documentation](../../compute/concepts/instance-groups/scale.md#auto-scale).

You can choose the scaling method that best suits your needs:

* **{{ ui-key.yacloud.compute.groups.create.field_default-utilization-target }}**: Scaling based on the `yarn.cluster.containersPending` metric.

   This is an internal YARN metric that shows the number of resource allocation units that pending jobs in the queue expect to be assigned. It is suitable for clusters that have lots of relatively small jobs managed by Apache Hadoop® YARN. This scaling method does not require additional configuration.

* **{{ ui-key.yacloud.compute.groups.create.field_utilization-target }}**: Scaling based on the vCPU usage metric. Learn more about this type of scaling in the [{{ ig-name }} documentation](../../compute/concepts/instance-groups/scale.md#cpu-utilization).

To set up autoscaling of your cluster based on other metrics and formulas, [contact](../../support/qa.md) support.

You can set the following autoscaling parameters:

* Initial (minimum) size of the group.
* [Decommissioning](decommission.md) timeout in seconds. The maximum value is `86400` seconds (24 hours). The default value is `120` seconds.
* Type of VM instances: standard or preemptible.
* Maximum group size.
* Time period for calculating the average load on each VM instance in the group.
* Instance warmup period: Interval during which instance metrics are not used after it starts. Average metric values for the group are used instead.
* Stabilization period (minutes or seconds): Interval during which the number of instances in the group cannot be decreased.
