# Решение конфликта версий при установке Python SDK

Когда вы [устанавливаете пакет](install.md) `yandex-speechkit`, вместе с ним также устанавливается пакет `grpcio-tools` версии {{ grpcio-tools-version }}. Если вы ранее устанавливали `grpcio-tools` (например, при разборе [примеров работы с API {{ speechkit-name }}](../../tutorials/index.md)), может возникнуть конфликт версий этого пакета.

Проверьте, какая версия `grpcio-tools` установлена:

```bash
pip list | grep grpcio-tools
```

Если результат команды содержит пакет `grpcio-tools` и его версия больше {{ grpcio-tools-version }}, создайте виртуальное окружение, чтобы избежать конфликта версий. Иначе установите пакет `yandex-speechkit` без виртуального окружения.

Чтобы развернуть окружение и установить в нем пакет:

1. Создайте папку для проекта на Python SDK и перейдите в нее.
1. Создайте виртуальное окружение в этой папке:

   ```bash
   python3 -m venv <название окружения>
   ```

   Если нужно создать окружение с определенной версией Python, вместо `python3` укажите `python<версия>`. Например, `python3.9`.

1. Активируйте окружение:

   ```bash
   source <название окружения>/bin/activate
   ```

   Название окружения появится перед строкой ввода в терминале.

1. Установите пакет `yandex-speechkit` с помощью менеджера пакетов pip:

   ```bash
   pip install yandex-speechkit
   ```

Далее продолжайте работу с Python SDK в развернутом окружении. Когда завершите работу, выйдите из окружения с помощью команды `deactivate`.
