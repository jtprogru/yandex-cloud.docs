# Создать профиль OS Login

{% include notitle [preview](../../_includes/note-preview-by-request.md) %}

По умолчанию профили OS Login будут созданы для всех пользователей организации при [включении настройки](./os-login-access.md). При необходимости вы можете создать дополнительные профили или отредактировать существующие. Профили OS Login можно использовать в качестве профилей пользователей при работе внутри ВМ.

{% list tabs %}

- {{ org-name }}

  1. [Войдите в аккаунт]({{ link-passport-login }}) администратора или владельца организации.
  1. Перейдите в сервис [{{ org-full-name }}]({{ link-org-main }}).
  1. На панели слева выберите раздел [{{ ui-key.yacloud_org.pages.users }}]({{ link-org-users }}) ![icon-users](../../_assets/organization/icon-users.svg).
  1. Выберите пользователя из списка.
  1. Перейдите на вкладку **Профили OS Login**.
  1. Нажмите кнопку **Создать профиль**.
  1. Введите имя пользователя и уникальный числовой идентификатор.
  1. (Опционально) Укажите путь к домашнему каталогу пользователя.
  1. (Опционально) Укажите путь до исполняемого файла командной оболочки.
  1. Нажмите кнопку **Сохранить**.

{% endlist %}
