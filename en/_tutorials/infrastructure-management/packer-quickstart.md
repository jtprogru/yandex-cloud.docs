# Getting started with Packer

Packer enables you to create [virtual machine disk images](../../compute/concepts/image.md) with parameters specified in a configuration file. Below, we describe how to create a disk image using Packer.

In this scenario, Packer will create and launch a virtual machine with [Debian 11](/marketplace/products/yc/debian-11) from {{ marketplace-name }} and nginx web server. Then, it will delete the VM and create an image of its boot disk. After that, the disk will also be deleted.

To create an image:

1. [Prepare your cloud](#before-you-begin)
1. [Install Packer](#install-packer)
1. [Prepare the image configuration](#prepare-image-config)
1. [Create an image](#create-image)
1. [Check the image](#check-image)

If you no longer need the image you created, [delete it](#clear-out).

## Prepare your cloud {#before-you-begin}

{% include [before-you-begin](../_tutorials_includes/before-you-begin.md) %}

* Install the {{ yandex-cloud }} [command line interface](../../cli/quickstart.md#install).
* [Create](../../vpc/quickstart.md) a cloud network with a single subnet in your folder.
* Get an [OAuth token]({{ link-cloud-oauth }}) for a [Yandex account](../../iam/concepts/#passport) or an [IAM token](../../iam/operations/iam-token/create-for-federation.md) for a [federated account](../../iam/concepts/federations.md).


### Required paid resources {#paid-resources}

You pay for storing created images (see [pricing](../../compute/pricing#prices-storage) for {{ compute-full-name }}).


## Install Packer {#install-packer}

{% note info %}

{{ yandex-cloud }} requires Packer 1.5 or higher.

{% endnote %}

Download a Packer distribution and install it by following the [instructions on the official website](https://www.packer.io/intro/getting-started/install.html#precompiled-binaries).

You can also download a Packer distribution for your platform from a [mirror](https://hashicorp-releases.yandexcloud.net/packer/). When the download is complete, add the path to the folder with the executable to the `PATH` variable:

```bash
export PATH=$PATH:/path/to/packer
```

### Configure the Yandex Compute Builder plugin {#configure-plugin}

To configure the [plugin](https://developer.hashicorp.com/packer/plugins/builders/yandex):

1. Create a `config.pkr.hcl` file with the following contents:

   ```hcl
   packer {
     required_plugins {
       yandex = {
         version = ">= 1.1.2"
         source  = "{{ packer-source-link }}"
       }
     }
   }
   ```

1. Install the plugin:

   ```bash
   packer init <config.pkr.hcl_file_path>
   ```

   Result:

   ```text
   Installed plugin github.com/hashicorp/yandex v1.1.2 in ...
   ```

## Prepare the image configuration {#prepare-image-config}

1. Get the folder ID by running the `yc config list` command.
1. Get the subnet ID by running the command `yc vpc subnet list`.
1. Create a JSON file with any name, like `image.json`. This will be your template. Enter the following parameters:


```json
{
  "builders": [
    {
      "type":      "yandex",
      "token":     "<OAuth_or_IAM-token>",
      "folder_id": "<folder_ID>",
      "zone":      "{{ region-id }}-a",

      "image_name":        "debian-11-nginx-not_var{{isotime | clean_resource_name}}",
      "image_family":      "debian-web-server",
      "image_description": "my custom debian with nginx",

      "source_image_family": "debian-11",
      "subnet_id":           "<subnet_ID>",
      "use_ipv4_nat":        true,
      "disk_type":           "network-ssd",
      "ssh_username":        "debian"
    }
  ],
  "provisioners": [
    {
      "type": "shell",
      "inline": [
        "echo 'updating APT'",
        "sudo apt-get update -y",
        "sudo apt-get install -y nginx",
        "sudo su -",
        "sudo systemctl enable nginx.service",
        "curl localhost"
      ]
    }
  ]
}
```

Where:
  * `token`: OAuth token for a Yandex account or an IAM token for a federated account.
  * `folder_id`: [ID of the folder](../../resource-manager/operations/folder/get-id) to create a VM and its image in.
  * `subnet_ID`: ID of the subnet to create a VM and its image in.

Learn more about image configuration parameters in the [Yandex Compute Builder documentation](https://www.packer.io/docs/builders/yandex).




## Create an image {#create-image}

Build the image using the template:

```
packer build image.json
```

## Check the image {#check-image}

Make sure the image was created:

1. Go to the [management console]({{ link-console-main }}).
1. Select **{{ compute-short-name }}**.
1. Open **Images**. Check if the new disk image is there.

### Delete the resources you created {#clear-out}

If you no longer need the created image, [delete it](../../compute/operations/image-control/delete.md).

Delete the [subnet](../../vpc/operations/subnet-delete.md) and [cloud network](../../vpc/operations/network-delete.md) if you created them to run this scenario.
