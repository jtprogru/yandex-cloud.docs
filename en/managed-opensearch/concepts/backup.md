# Backups in {{ mos-name }}

{{ mos-short-name }} supports automatic and manual [index](./indexing.md) backups.

A backup is automatically created once in 24 hours and stored for 7 days. You cannot disable automatic backups or change the retention period.

To restore a cluster from a backup, [follow this guide](../operations/cluster-backups.md#restore).

## Creating backups {#size}

You can create backups both automatically and [manually](../operations/cluster-backups.md#create-backup). After a backup is created, it is compressed for storage. The exact backup size is not displayed.

Backups are only created on running clusters.

For more information about creating a backup manually, see [Managing backups](../operations/cluster-backups.md).

## Storing backups {#storage}

Storing backups in {{ mos-name }}:

* Backups are stored in object storage as binaries.

* All backups (automatic or manual) are stored for seven days.

* {% include [no-quotes-no-limits](../../_includes/mdb/backups/no-quotes-no-limits.md) %}

* {% include [using-storage](../../_includes/mdb/backups/storage.md) %}

   
   For more information, see the [{{ mos-name }} pricing policy](../pricing.md#rules-storage).


## Checking backup recovery {#capabilities}

To test how backup works, [restore a cluster from a backup](../operations/cluster-backups.md#restore) and check the integrity of your data.
