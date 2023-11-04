## Create a transfer {#create-transfer}

{% list tabs %}

- Management console

   1. In the [management console]({{ link-console-main }}), select the folder where you want to create a transfer.
   1. Select {{ ui-key.yacloud.iam.folder.dashboard.label_data-transfer }}.
   1. Create a source endpoint:
      1. In the ![endpoint](../../_assets/data-transfer/endpoint.svg) **{{ ui-key.yacloud.data-transfer.label_endpoints }}** tab, click **{{ ui-key.yacloud.data-transfer.button_create-endpoint }}**.
      1. In the **{{ ui-key.yacloud.data-transfer.forms.label-is_source }}** field, select `{{ ui-key.yacloud.data-transfer.forms.label_source-type }}`.
      1. Enter the endpoint name, for example, `logs-source`.
      1. In the **{{ ui-key.yacloud.data-transfer.forms.label-database_type }}** list, select `{{ ui-key.yacloud.data-transfer.label_endpoint-type-YDS_ru }}`.
      1. Select the database you specified in the settings of the stream you previously created.
      1. Enter the stream name: `logs-stream`.
      1. Select the previously created `logs-sa` service account.
      1. Under **{{ ui-key.yacloud.alb.label_detailed-settings }}**, specify the conversion rules for the `{{ ui-key.yc-data-transfer.data-transfer.console.form.logbroker.console.form.logbroker.ParserConfigCommon.parser_config_common_cloud_logging.title }}` data.
      1. Click **{{ ui-key.yacloud.common.create }}**.
   1. Create a target endpoint:
      1. In the ![endpoint](../../_assets/data-transfer/endpoint.svg) **{{ ui-key.yacloud.data-transfer.label_endpoints }}** tab, click **{{ ui-key.yacloud.data-transfer.button_create-endpoint }}**.
      1. In the **{{ ui-key.yacloud.data-transfer.forms.label-is_source }}** field, select `{{ ui-key.yacloud.data-transfer.forms.label_target-type }}`.
      1. Enter the endpoint name, for example, `logs-receiver`.
      1. In the **{{ ui-key.yacloud.data-transfer.forms.label-database_type }}** list, select `{{ ui-key.yacloud.data-transfer.label_endpoint-type-OBJECT_STORAGE }}`.
      1. Enter the name of the previously created bucket.
      1. Select the previously created `logs-sa` service account.
      1. In the **{{ ui-key.yc-data-transfer.data-transfer.console.form.object_storage.console.form.object_storage.ObjectStorageTarget.output_format.title }}** field, select `JSON`.
      1. Click **{{ ui-key.yacloud.common.create }}**.
   1. Create a transfer:
      1. In the ![image](../../_assets/data-transfer/transfer.svg) **{{ ui-key.yacloud.data-transfer.label_connectors }}** tab, click **{{ ui-key.yacloud.data-transfer.button_create-transfer }}**.
      1. Enter the transfer name, e.g., `logs-transfer`.
      1. Select the previously created source endpoint, `logs-source`.
      1. Select the previously created target endpoint, `logs-receiver`.
      1. Click **{{ ui-key.yacloud.common.create }}**.
   1. Click ![ellipsis](../../_assets/horizontal-ellipsis.svg) next to the created transfer and select **{{ ui-key.yacloud.data-transfer.label_connector-operation-ACTIVATE }}**.

   Wait until the transfer is activated. Once the transfer is ready for use, its status will change from `{{ ui-key.yacloud.data-transfer.label_connector-status-CREATING }}` to `{{ ui-key.yacloud.data-transfer.label_connector-status-RUNNING }}`.

{% endlist %}