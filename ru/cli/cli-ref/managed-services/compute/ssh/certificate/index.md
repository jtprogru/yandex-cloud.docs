---
editable: false
sourcePath: en/_cli-ref/cli-ref/managed-services/compute/ssh/certificate/index.md
---

# yc compute ssh certificate

Manage certificates

#### Command Usage

Syntax: 

`yc compute ssh certificate <command>`

#### Command Tree

- [yc compute ssh certificate export](export.md) — Export certificate

#### Global Flags

| Flag | Description |
|----|----|
|`--id`|<b>`string`</b><br/>Instance ID.|
|`--name`|<b>`string`</b><br/>Instance name.|
|`--login`|<b>`string`</b><br/>Certificate owner login.|
|`--internal-address`|Connect to instance via internal address.|
|`--profile`|<b>`string`</b><br/>Set the custom configuration file.|
|`--debug`|Debug logging.|
|`--debug-grpc`|Debug gRPC logging. Very verbose, used for debugging connection problems.|
|`--no-user-output`|Disable printing user intended output to stderr.|
|`--retry`|<b>`int`</b><br/>Enable gRPC retries. By default, retries are enabled with maximum 5 attempts.<br/>Pass 0 to disable retries. Pass any negative value for infinite retries.<br/>Even infinite retries are capped with 2 minutes timeout.|
|`--cloud-id`|<b>`string`</b><br/>Set the ID of the cloud to use.|
|`--folder-id`|<b>`string`</b><br/>Set the ID of the folder to use.|
|`--folder-name`|<b>`string`</b><br/>Set the name of the folder to use (will be resolved to id).|
|`--endpoint`|<b>`string`</b><br/>Set the Cloud API endpoint (host:port).|
|`--token`|<b>`string`</b><br/>Set the OAuth token to use.|
|`--impersonate-service-account-id`|<b>`string`</b><br/>Set the ID of the service account to impersonate.|
|`--format`|<b>`string`</b><br/>Set the output format: text (default), yaml, json, json-rest.|
|`-h`,`--help`|Display help for the command.|
