# azure-tools

### Overview

Collection of random tools for Azure.

Note, some of these scripts assume they're executing in busybox. (`cleanup.sh`, for example, uses timeout which has different syntax under busybox)

#### `./cleanup.sh`

This will delete resource groups whose name contains the first argument.

```shell
export AZURE_SUBSCRIPTION_ID=6f368760-9ad2-4aef-8ff1-fb038d2e75bf
./cleanup.sh k8s

# Output:
# DELETE: campbelldgunn-k8s-c0 campbelldgunn-k8s-pr220 k8s-any-1117-1959a49
# SUBSCRIPTION: 6f368760-9ad2-4aef-8ff1-fb038d2e75bf
# CONFIRM ('yes' proceeds, everything else exits):
````

#### `./make-vhd.sh`

This will create and upload a formatted VHD to your storage account/container.

```shell
export AZURE_SUBSCRIPTION_ID=6f368760-9ad2-4aef-8ff1-fb038d2e75bf
export AZURE_RESOURCE_GROUP=campbelldgunn-vhds2
export AZURE_STORAGE_ACCOUNT=campbelldgunnvhds2
export AZURE_STORAGE_CONTAINER=campbelldgunnvhds2
export IMAGE_SIZE=10G
export MKFS_TYPE=ext4 # (default: 'ext4'. possible: ['ext4', 'ntfs', 'xfs'])

./make-vhd.sh

# Output:
# ...
# VHD_URL=https://campbelldgunnvhds2.blob.core.windows.net/campbelldgunnvhds2/data-disk-082916103645.vhd
```

### Docker Hub

`docker.io/campbelldgunn/azure-tools:latest`
