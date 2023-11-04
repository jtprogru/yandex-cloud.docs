# Замена датасета в чарте

Чтобы заменить датасет в чарте:


{% include [datalens-workbooks-collections-select-note](../../../_includes/datalens/operations/datalens-workbooks-collections-select-note.md) %}


1. На панели слева нажмите ![image](../../../_assets/datalens/chart.svg) **Чарты** и выберите нужный чарт.
1. В левой части экрана нажмите значок ![image](../../../_assets/datalens/horizontal-ellipsis.svg) у датасета и выберите **Заменить датасет**.
1. Выберите другой датасет.

   {% note info %}

   Новый датасет должен содержать поля с теми же названиями, что и старый. Если после замены датасета чарт отображается с ошибкой `ERR.DS_API.DB.COLUMN_DOES_NOT_EXIST`, воспользуйтесь инструкцией [{#T}](../dataset/update-field.md#replace-field).

   {% endnote %}

1. В правом верхнем углу нажмите кнопку **Сохранить**.
