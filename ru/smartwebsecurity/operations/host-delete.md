---
title: "Отключить профиль безопасности от виртуального хоста"
description: "Следуя данной инструкции, вы сможете отключить профиль безопасности от виртуального хоста."
---

# Отключить профиль безопасности от виртуального хоста

{% list tabs %}

- Консоль управления

  1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором вы хотите отключить [профиль безопасности](../concepts/profiles.md) от [виртуального хоста](../../application-load-balancer/concepts/http-router.md#virtual-host) сервиса [{{ alb-full-name }}](../../application-load-balancer/).
  1. В списке сервисов выберите **{{ ui-key.yacloud.iam.folder.dashboard.label_smartwebsecurity }}**.
  1. Выберите профиль, который вы хотите отключить от хоста.
  1. Перейдите на вкладку **{{ ui-key.yacloud.smart-web-security.overview.title_connected-to-the-hosts }}**.
  1. Напротив хоста, от которого вы хотите отключить профиль, нажмите ![options](../../_assets/options.svg) и выберите ![disconnect](../../_assets/smartwebsecurity/disconnect.svg) **{{ ui-key.yacloud.smart-web-security.overview.action_disconnect-host }}**.
  1. Подтвердите отключение.

{% endlist %}
