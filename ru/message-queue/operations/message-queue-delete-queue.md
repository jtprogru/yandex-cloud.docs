# Удаление очереди сообщений

Чтобы удалить очередь сообщений:

{% list tabs %}

- Консоль управления

  1. В [консоли управления]({{ link-console-main }}) выберите каталог, которому принадлежит очередь.
  1. Выберите сервис **{{ ui-key.yacloud.iam.folder.dashboard.label_message-queue }}**.
  1. В строке нужной очереди нажмите значок ![image](../../_assets/horizontal-ellipsis.svg) и выберите **{{ ui-key.yacloud.common.delete }}**.
  1. В открывшемся окне нажмите кнопку **{{ ui-key.yacloud.common.delete }}**.
  
- AWS CLI
  
  1. Получите URL очереди сообщений, которую нужно удалить:
  
     ```bash
     aws sqs list-queues \
       --endpoint <эндпойнт>
     ```

     Где `--endpoint` — эндпоинт в значении `https://message-queue.{{ api-host }}/`.

  2. Удалите очередь сообщений:
  
     ```
     aws sqs delete-queue \
       --queue-url <URL_очереди> \
       --endpoint <эндпоинт>
     ```

     Где:
     * `--queue-url` — URL очереди, которую нужно удалить.
     * `--endpoint` — эндпоинт в значении `https://message-queue.{{ api-host }}/`.

- {{ TF }}

  Если вы создавали очередь сообщений с помощью {{ TF }}, вы можете удалить ее:
  1. В командной строке перейдите в папку, где расположен конфигурационный файл {{ TF }}.
  1. Удалите ресурсы с помощью команды:

     ```bash
     terraform destroy
     ```

     {% note alert %}

     {{ TF }} удалит все ресурсы, созданные в текущей конфигурации: кластеры, сети, подсети, виртуальные машины и т. д.

     {% endnote %}

  1. Введите слово `yes` и нажмите **Enter**.

{% endlist %}
