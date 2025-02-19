---
title: "Viewing execution logs in {{ sf-full-name }}"
description: "You can view monitoring charts in {{ sf-full-name }} using the management console. To do this, select {{ sf-name }} and click the function whose execution log you want to view. In the window that opens, go to Logs and specify the time period. The default time period is 1 hour. Function execution logs are stored for 3 days. Time in the log is shown in UTC."
---

# Viewing function logs

Function execution logs are stored for 3 days. The log uses [UTC time](https://en.wikipedia.org/wiki/Coordinated_Universal_Time).

{% list tabs %}

- Management console

   1. In the [management console]({{ link-console-main }}), select the folder containing your function.
   1. Select **{{ ui-key.yacloud.iam.folder.dashboard.label_serverless-functions }}**.
   1. Click a function to view its runtime log.
   1. In the window that opens, go to **{{ ui-key.yacloud.serverless-functions.item.switch_logs }}** and specify the period for which you want to view logs. The default period is 1 hour.

- CLI

   {% include [timeslot](../../../_includes/functions/timeslot.md) %}

   {% include [cli-install](../../../_includes/cli-install.md) %}

   {% include [default-catalogue](../../../_includes/default-catalogue.md) %}

   {% include [function-list-note](../../../_includes/functions/function-list-note.md) %}

   View the function execution log:

   ```
   yc serverless function logs <function name>
   ```
   Result:
   ```
   2019-07-04 09:27:43     START RequestID: 34dc9533-ed6e-4468-b9f2-2aa082266fad Version: b09i2s85a0c1fisjboft
   2019-07-04 09:27:43     END RequestID: 34dc9533-ed6e-4468-b9f2-2aa082266fad
   2019-07-04 09:27:43     REPORT RequestID: 34dc9533-ed6e-4468-b9f2-2aa082266fad Duration: 538.610 ms Billed Duration: 538.700 ms Memory Size: 128 MB Max Memory Used: 13 MB
   2019-07-04 09:29:25     START RequestID: 5b6a3779-dcc8-44ec-8ee2-2e7f279394ef Version: b09i2s85a0c1fisjboft
   2019-07-04 09:29:26     END RequestID: 5b6a3779-dcc8-44ec-8ee2-2e7f279394ef
   2019-07-04 09:29:26     REPORT RequestID: 5b6a3779-dcc8-44ec-8ee2-2e7f279394ef Duration: 554.904 ms Billed Duration: 555.000 ms Memory Size: 128 MB Max Memory Used: 13 MB
   ...
   ```

   {% note info %}

   If you called a function with a specific tag, you must also specify this tag when viewing the execution log: `yc serverless function logs my-python-function --tag test`.

   {% endnote %}


- {{ yandex-cloud }} Toolkit

   You can view the function execution log using the [{{ yandex-cloud }} Toolkit plugin](https://github.com/yandex-cloud/ide-plugin-jetbrains/blob/master/README.en.md) for the IDE family on the [IntelliJ platform](https://www.jetbrains.com/opensource/idea/) from [JetBrains](https://www.jetbrains.com/).


{% endlist %}

Learn more about working with logs in the [{{ cloud-logging-full-name }} documentation](../../../logging/).
