# Testing a lifecycle policy

A dry run helps verify which [Docker images](../../concepts/docker-image.md) meet [lifecycle policy](../../concepts/lifecycle-policy.md) rules. Docker images are not actually deleted during dry runs.

{% note warning %}

The maximum number of Docker images in a single [repository](../../concepts/repository.md) that a single dry run can verify is 50,000. In this case, an active policy with the same rules deletes all Docker images that are suitable for deletion.

{% endnote %}

{% list tabs %}

- Management console

  1. In the [management console]({{ link-console-main }}), select the [folder](../../../resource-manager/concepts/resources-hierarchy.md#folder) where the [registry](../../concepts/registry.md) was created.
  1. In the list of services, select **{{ ui-key.yacloud.iam.folder.dashboard.label_container-registry }}**.
  1. Select the registry and click the row with its name.
  1. Select the repository and click the row with its name.
  1. In the left-hand panel, click ![lifecycle](../../../_assets/container-registry/lifecycle.svg) **{{ ui-key.yacloud.cr.registry.label_lifecycle }}**.
  1. Click the name of the lifecycle policy you need.
  1. In the top-right corner, click ![image](../../../_assets/compute/run-vm.svg) **{{ ui-key.yacloud.cr.registry.button_lifecycle-dry-run }}**. Once the test is completed, the **{{ ui-key.yacloud.cr.registry.label_lifecycle-dry-runs }}** section will contain a line with the policy dry run results.
  1. To get a list of Docker images to be deleted according to the policy rules, click the line with the policy dry run results.

- CLI

  {% include [cli-install](../../../_includes/cli-install.md) %}

  To test a lifecycle policy:
  1. Perform a dry run of the policy:

     ```bash
     yc container repository lifecycle-policy dry-run <policy ID>
     ```

     Result:

     ```bash
     dry_run_lifecycle_policy_result_id: crpn27glo1k8r81dveq2
     lifecycle_policy_id: crp6lg1868p3i0emkv1b
     run_at: "2020-05-29T07:30:02.704Z"
     affected_images_count: "1"
     ```

     To find out the policy ID, get a [list of lifecycle policies in a repository or registry](lifecycle-policy-list.md#lifecycle-policy-list).
  1. Get a list of policy dry runs:

     ```bash
     yc container repository lifecycle-policy list-dry-run-results crp6lg1868p3i0emkv1b
     ```

     Result:

     ```bash
     +----------------------+----------------------+-----------------------+---------------------+
     |      RESULT ID       | LIFECYCLE POLICY ID  | AFFECTED IMAGES COUNT |       RUN AT        |
     +----------------------+----------------------+-----------------------+---------------------+
     | crpn27glo1k8r81dveq2 | crp6lg1868p3i0emkv1b |                     1 | 2020-05-29 07:30:02 |
     +----------------------+----------------------+-----------------------+---------------------+
     ```

  1. Get information about the results of the policy dry run. Use the `RESULT ID` parameter from the previous item:

     ```bash
     yc container repository lifecycle-policy get-dry-run-result crpn27glo1k8r81dveq2
     ```

      Result:

     ```bash
     dry_run_lifecycle_policy_result_id: crpn27glo1k8r81dveq2
     lifecycle_policy_id: crp6lg1868p3i0emkv1b
     run_at: "2020-05-29T07:30:02.704Z"
     affected_images_count: "1"
     ```

  1. Get a list of Docker images to be deleted according to the policy rules. Use the `dry_run_lifecycle_policy_result_id` parameter from the previous item:

     ```bash
     yc container repository lifecycle-policy list-dry-run-affected-images crpn27glo1k8r81dveq2
     ```

     Result:

     ```bash
     +----------------------+---------------------+-----------------------------+------+-----------------+
     |          ID          |       CREATED       |            NAME             | TAGS | COMPRESSED SIZE |
     +----------------------+---------------------+-----------------------------+------+-----------------+
     | crphc7nnrvhlg73oeiv5 | 2019-01-17 17:00:48 | crp2hlbs67tj4ggrfodb/ubuntu | 111  | 64.1 MB         |
     +----------------------+---------------------+-----------------------------+------+-----------------+
     ```

- API

  To test a lifecycle policy:
  1. Perform a policy dry run using the [DryRun](../../api-ref/grpc/lifecycle_policy_service.md#DryRun) method of the [LifecyclePolicyService](../../api-ref/grpc/lifecycle_policy_service.md) resource. In the `lifecycle_policy_id` parameter, specify a policy ID. You can retrieve a list of policies using the [List](../../api-ref/grpc/lifecycle_policy_service.md#List) method for the [LifecyclePolicyService](../../api-ref/grpc/lifecycle_policy_service.md) resource.
  1. Retrieve a list of policy dry runs using the [ListDryRunResults](../../api-ref/grpc/lifecycle_policy_service.md#ListDryRunResults) method for the [LifecyclePolicyService](../../api-ref/grpc/lifecycle_policy_service.md) resource. In the `lifecycle_policy_id` parameter, specify a policy ID.
  1. Retrieve information regarding a policy dry run using the [GetDryRunResult](../../api-ref/grpc/lifecycle_policy_service.md#GetDryRunResult) method for the [LifecyclePolicyService](../../api-ref/grpc/lifecycle_policy_service.md) resource. In the `dry_run_lifecycle_policy_result_id` parameter, specify the ID of the policy dry run results from the previous item.
  1. Get a list of Docker images to be deleted according to the policy rules. Use the [ListDryRunResultAffectedImages](../../api-ref/grpc/lifecycle_policy_service.md#ListDryRunResultAffectedImages) method for the [LifecyclePolicyService](../../api-ref/grpc/lifecycle_policy_service.md) resource. In the `dry_run_lifecycle_policy_result_id` parameter, specify the ID of the policy dry run results.

{% endlist %}