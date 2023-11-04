# Размещение HTML-кода для работы {{ captcha-full-name }}

Чтобы иметь возможность встраивать сервис {{ captcha-name }} в Android или IOS-приложение через **WebView**, разместите данную HTML-страницу на хосте одного из ваших доменов:

{% cut "HTML-страница с кодом капчи" %}

```html
<!DOCTYPE html>
<html>
  <head>
    <title>SmartCaptcha Mobile</title>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1, shrink-to-fit=no"
    />
    <script>
      function onSmartCaptchaReady() {
        if (!window.smartCaptcha) {
          throw new Error("SmartCaptcha is not present");
        }

        const params = getParameters();

        const widgetId = window.smartCaptcha.render(
          "captcha-container",
          params
        );

        window.smartCaptcha.subscribe(
          widgetId,
          "challenge-visible",
          handleChallengeVisible
        );

        window.smartCaptcha.subscribe(
          widgetId,
          "challenge-hidden",
          handleChallengeHidden
        );

        window.smartCaptcha.subscribe(widgetId, "success", handleSuccess);

        if (params.invisible) {
          window.smartCaptcha.execute(widgetId);
        }
      }

      function handleSuccess(token) {
        if (window.NativeClient) {
          window.NativeClient.onGetToken(token);
        } else {
          sendIos("captchaDidFinish", token);
        }
      }

      function handleChallengeVisible() {
        if (window.NativeClient) {
          window.NativeClient.onChallengeVisible();
        } else {
          sendIos("challengeDidAppear");
        }
      }

      function handleChallengeHidden() {
        if (window.NativeClient) {
          window.NativeClient.onChallengeHidden();
        } else {
          sendIos("challengeDidDisappear");
        }
      }

      function sendIos(...args) {
        if (args.length == 0) {
          return;
        }

        const message = {
          method: args[0],
          data: args[1] !== undefined ? args[1] : ""
        };

        if (window.webkit) {
          window.webkit.messageHandlers.NativeClient.postMessage(message);
        }
      }

      function getParameters() {
        const result = {};

        if (!window.location.search) {
          return result;
        }

        const queryParams = new URLSearchParams(window.location.search);

        queryParams.forEach((value, key) => {
          result[key] = value;
        });

        result.test = result.test === "true";
        result.invisible = result.invisible === "true";
        result.hideShield = result.hideShield === "true";
        result.webview = true;

        return result;
      }
    </script>

    <script
      src="https://smartcaptcha.yandexcloud.net/captcha.js?render=onload&onload=onSmartCaptchaReady"
      defer
    ></script>
  </head>

  <body>
    <noscript>
      You need to enable JavaScript to run this app.
    </noscript>
    <div id="captcha-container" class="smart-captcha" />
  </body>
</html>
```

{% endcut %}

Если вы не хотите самостоятельно размещать на хосте данную страницу, то можете воспользоваться готовой HTML-страницей `{{ captcha-mobile-site }}` с нашего сервера.

После размещения кода капчи можно использовать {{ captcha-full-name }} в следующих случаях:

* [{#T}](../smartcaptcha/tutorials/mobile-app/android/quickstart-android.md).
* [{#T}](../smartcaptcha/tutorials/mobile-app/android/invisible-captcha-android.md).
* [{#T}](../smartcaptcha/tutorials/mobile-app/ios/quickstart-ios.md).
