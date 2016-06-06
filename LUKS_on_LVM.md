# Creating Encrypted Partitions

The general instructions are on Aaron's website: http://dads2busy.github.io/2015/10/luks_on_lvm

The tl;dr:

```bash
sudo mkdir -p /home/sdal/projects/teen_sex
sudo lvcreate -L 100G system -n teen_sex
sudo mkfs.ext4 /dev/mapper/system-teen_sex
# sudo dd if=/dev/urandom of=/dev/system/teen_sex
sudo cryptsetup luksFormat -c aes-xts-plain64 -s 512 /dev/system/teen_sex
sudo cryptsetup open --type luks /dev/system/teen_sex teen_sex_Encrypted
sudo mkfs.ext4 /dev/mapper/teen_sex_Encrypted
sudo mount /dev/mapper/teen_sex_Encrypted /home/sdal/projects/teen_sex
```

- Open `/etc/crypttab` to create a mapper that can then be referenced in the fstab
- Mount the device in fstab `/etc/fstab`
- Auto mount in the containers `/home/sdal/vms/lxc/sdal_config`
