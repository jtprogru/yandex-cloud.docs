---
title: "Как удалить пользователя из сообщества"
description: "Из статьи вы узнаете, как удалить пользователя из сообщества в {{ ml-platform-name }}."
---

# Удалить пользователя из сообщества

{% note info %}

Вы можете удалить пользователя, только если в сообществе у вас есть роль `{{ roles-datasphere-communities-admin }}`.

{% endnote %}

1. Откройте [главную страницу]({{ link-datasphere-main }}) {{ ml-platform-name }}.
1. На панели слева выберите ![community-panel](../../../_assets/datasphere/communities.svg) **{{ ui-key.yc-ui-datasphere.common.spaces }}**.
1. Выберите сообщество, из которого вы хотите удалить пользователей.
1. Перейдите на вкладку **{{ ui-key.yc-ui-datasphere.common.members }}**. 
1. Напротив нужного пользователя нажмите ![image](../../../_assets/horizontal-ellipsis.svg) и выберите **{{ ui-key.yc-ui-datasphere.common.member.remove }}**.
1. Нажмите кнопку **{{ ui-key.yc-ui-datasphere.common.submit }}**.
1. Если вы добавляли пользователя с помощью ссылки, то ее необходимо пересоздать:
    * Нажмите кнопку **{{ ui-key.yc-ui-datasphere.common.add-member }}**. 
    * Внизу открывшегося окна нажмите **{{ ui-key.yc-ui-datasphere.invite-link.reset-invitation-link }}** ⟶ **{{ ui-key.yc-ui-datasphere.invite-link.reset-link }}**.
