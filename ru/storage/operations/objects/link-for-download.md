# Получение ссылки на скачивание

Если у вас публичный бакет, объекты доступны всегда, даже если для бакета не настроен [хостинг веб-сайта](../../concepts/hosting.md). Ссылку можно получить по этой инструкции либо сформировать самостоятельно. [Подробнее про формат ссылки](../../concepts/object.md#object-url).

Если у вас бакет с ограниченным доступом, то {{ objstorage-name }} позволяет сгенерировать подписанную ссылку на объект. Любой человек, получивший эту ссылку, сможет скачать объект даже из бакета с ограниченным доступом. [Подробнее про подписанные ссылки, их генерацию и использование](../../concepts/pre-signed-urls.md).

{% list tabs %}

- Консоль управления

  {% include [storage-get-link-for-download](../../_includes_service/storage-get-link-for-download.md) %}

{% endlist %}
