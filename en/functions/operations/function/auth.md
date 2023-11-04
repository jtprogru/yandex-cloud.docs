# Authenticating when invoking a private function via HTTPS

To invoke a private function via HTTPS, you must authenticate. To do this, get:

* [IAM token](../../../iam/concepts/authorization/iam-token.md):
   * [Guide](../../../iam/operations/iam-token/create.md) for a Yandex account.
   * [Guide](../../../iam/operations/iam-token/create-for-sa.md) for a service account.
   * [Guide](../../../iam/operations/iam-token/create-for-federation.md) for a federated account.

   Pass the obtained IAM token in the `Authorization` header using the following format:
   ```
   Authorization: Bearer <IAM TOKEN>
   ```
   IAM tokens are valid for up to 12 hours.

* The [API key](../../../iam/operations/api-key/create) for the service account.

   Specify the obtained API key in the `Authorization` header using the following format:
   ```
   Authorization: Api-Key <API key>
   ```
   API keys do not expire. This means that this authentication method is simpler, but less secure. Use it if you cannot request an IAM token automatically.
