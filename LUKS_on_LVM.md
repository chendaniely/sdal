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

another example:

```
sudo mkdir -p /home/sdal/staff
sudo lvcreate -L 50G system -n staff
sudo mkfs.ext4 /dev/mapper/system-staff
sudo cryptsetup luksFormat -c aes-xts-plain64 -s 512 /dev/system/staff
sudo cryptsetup open --type luks /dev/system/staff staff_Encrypted
sudo mkfs.ext4 /dev/mapper/staff_Encrypted
sudo mount /dev/mapper/staff_Encrypted /home/sdal/staff

dd if=/dev/urandom of=/etc/luks-keys/staff bs=1 count=256
cryptsetup luksAddKey /dev/system/staff /etc/luks-keys/staff
```

in `/etc/crypttab`:

```
staff /dev/system/staff /etc/luks-keys/staff luks
```

in `/etc/fstab`:

```
/dev/mapper/staff  /home/sdal/staff    ext4  defaults        0 2 
```

- Open `/etc/crypttab` to create a mapper that can then be referenced in the fstab
- Mount the device in fstab `/etc/fstab`
- Auto mount in the containers `/home/vms/lxc/sdal_config`
