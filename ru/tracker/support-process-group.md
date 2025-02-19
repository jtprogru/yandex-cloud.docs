# Группировать обращения по темам

Часто требуется группировать обращения по каким-либо признакам: по типу проблемы, продукту и так далее. Это нужно, чтобы назначать исполнителями задач сотрудников с нужной специализацией, собирать и анализировать статистику по типам обращений.

Чтобы группировать задачи по темам, используйте компоненты:

1. В очереди службы поддержки [создайте компоненты](manager/components.md), соответствующие типам обращений.

    Для каждого компонента можно назначить ответственного сотрудника и включить опцию **{{ ui-key.startrek.blocks-desktop_b-form-new-component.task-assignee }}**, чтобы для новых задач с компонентом автоматически назначать этого сотрудника исполнителем.

1. Если требуется ограничить изменение или просмотр задач с определенными компонентами, [настройте для компонентов права доступа](manager/queue-access.md#access-components). 

1. Чтобы автоматически назначать исполнителя при добавлении компонента в существующую задачу, [настройте триггер](manager/trigger-examples.md#assign_ticket).

1. Используйте компоненты в фильтрах, чтобы искать задачи с определенной темой и настраивать [дашборды со статистикой](#dashboards).