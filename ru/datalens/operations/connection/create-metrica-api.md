# Создание подключения к Metrica

Чтобы создать подключение к Metrica:


{% include [datalens-workbooks-collections-note](../../../_includes/datalens/operations/datalens-workbooks-collections-note.md) %}



1. Перейдите на [страницу подключений]({{ link-datalens-main }}/connections).


1. Нажмите кнопку **Создать подключение**.
1. Выберите подключение **Metrica**.
1. Укажите параметры подключения:

   * **OAuth-токен**. Нажмите кнопку **Получить токен** или укажите вручную [OAuth-токен](#get-oauth-token) для доступа к данным Яндекс Метрики.
   * **Счетчик**. Укажите один или несколько счетчиков для подключения.
    
     {% include [datalens-get-token](../../../_includes/datalens/datalens-change-account-note.md) %}

   * **Точность**. Задайте точность данных (сэмплирование). Вы можете изменить точность после создания подключения.
   * Оставьте опцию **Автоматически создать дашборд, чарты и датасет над подключением** включенной, если хотите получить каталог со стандартным набором датасетов, чартов и готовый дашборд.
        
1. Нажмите кнопку **Создать подключение**.
1. Укажите название подключения и нажмите кнопку **Создать**.

{% include [datalens-metrica-note](../../../_includes/datalens/datalens-metrica-note.md) %}


Подключение к Metrica API не поддерживает [публичный доступ](../../concepts/datalens-public.md) к объектам, созданным на его основе. Чтобы поделиться дашбордом или чартом, созданным на основе данного подключения, воспользуйтесь одним из способов:

{% include [datalens-metrica-appmetrica-share](../../../_includes/datalens/datalens-metrica-appmetrica-share.md) %}


{% include [datalens-get-token](../../../_includes/datalens/operations/datalens-get-token.md) %}
