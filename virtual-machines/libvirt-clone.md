# Libvirt Clone
---------------

It may be needed to create virtual machines based on an existing image.
For that reason cloning an existing virtual machine is a very important
operation on VM cluster administrator toolkit.

Using the command *virt-clone* from the libvirt suite it is really easy to
create a clone of a VM:

```sh
virt-clone --original <base_image> \
    --name <name_of_the_clone> \
    --file <path_to_virtual_disk>
```

After this operation a new domain will be added into libvirt's pool using the
name of *name_of_the_clone* with the disk *path_to_virtual_disk*.

It should be noted that this operation **does not** alter the network
configuration of the created machine, which means things like the hostname
and the dhcp state will remain the same of the base\_image. To change that
the *virt-sysprep* utility may be used:

```sh
virt-sysprep --domain <name_of_the_clone> \
    --enable customize,dhcp-client-state,machine-id \
    --hostname <hostname_of_the_clone>
```
