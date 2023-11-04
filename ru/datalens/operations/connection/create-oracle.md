---
title: "Инструкция по созданию подключения к Oracle Database в {{ datalens-full-name }}"
description: "Из статьи вы узнаете, как подключиться к Oracle Database в {{ datalens-full-name }}."
---

# Создание подключения к Oracle Database

{% include [connection-note](../../../_includes/datalens/datalens-connection-note.md) %}

Чтобы создать подключение к Oracle Database:


{% include [datalens-workbooks-collections-note](../../../_includes/datalens/operations/datalens-workbooks-collections-note.md) %}



1. Перейдите на [страницу подключений]({{ link-datalens-main }}/connections).


1. Нажмите кнопку **Создать подключение**.
1. Выберите подключение **Oracle Database**.
1. Укажите параметры подключения:

   * **Имя хоста**. Укажите путь до хоста-мастера или IP-адрес хоста-мастера Oracle Database. Вы можете указать несколько хостов через запятую. Если к первому хосту подключиться не получится, {{ datalens-short-name }} выберет следующий из списка. 
   * **Порт**. Укажите порт подключения к Oracle Database. Порт по умолчанию — 1521.
   * **Путь к базе данных**. Укажите имя сервиса или системный идентификатор подключаемой базы данных и выберите опцию **Имя сервиса** или **SID** соответственно.
   * **Имя пользователя**. Укажите имя пользователя для подключения к Oracle Database.
   * **Пароль**. Укажите пароль для указанного пользователя.
   * **Время жизни кеша в секундах**. Укажите время жизни кеша или оставьте значение по умолчанию. Рекомендованное значение — 300 секунд (5 минут).
   * **Уровень доступа SQL запросов**. Позволяет использовать произвольный SQL-запрос для [формирования датасета](../../concepts/dataset/settings.md#sql-request-in-datatset).

1. Нажмите кнопку **Создать подключение**.
1. Укажите название подключения и нажмите кнопку **Создать**.

{% include [datalens-check-host](../../../_includes/datalens/operations/datalens-check-host.md) %}

## Дополнительные настройки {#additional-settings}

{% include [datalens-db-connection-export-settings](../../../_includes/datalens/operations/datalens-db-connection-export-settings.md) %}
