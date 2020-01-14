# Install RHEL 8 Virtual Machine

## Host

### Install KVM

```bash
sudo yum update
sudo yum install @virt
sudo dnf -y install virt-top libguestfs-tools
sudo systemctl enable --now libvirtd
sudo yum -y install virt-manager
```

### Install VM

```bash
virt-manager
sudo nmcli conn show ---> Check that the bridge has been created
```

Install the VM

### Change root password of the guest image

```bash
sudo virt-customize -a <name_iso> --root-password <password>: --uninstall cloud-init
```

## Guest

### Register the VM

```bash
subscription-manager register --username=<USER_NAME> --password=<PASSWORD> --auto-attach
```

### Activate GNOME

```bash
dnf groupinstall workstation
systemctl set-default graphical.target
systemctl isolate graphical
```
