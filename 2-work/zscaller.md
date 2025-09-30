To install zscaler on Pop!_OS 22.04, download the connector from the admin zscaler site by clicking the Client Connector link on the sidebar, then clicking Client Connector App Store, New Releases, Linux and download 1.4.0.105.

Before installing, you must temporarily replace your /etc/os-release file:

```bash
cd /etc
sudo mv os-release os-release.old
sudo cat <<EOF >> os-release
PRETTY_NAME="Ubuntu 22.04.2 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.2 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
EOF
```

Now install it: `sudo ~/Downloads/pacote.deb`

Then revert the changes to `/etc/os-release`:

```bash
sudo mv os-release.old os-release
```

If you are having issues with the zscaler updater, you can replace the apparmor profiles with the below ones in `/etc/apparmor.d/`. Don't forget to reload the profiles by doing:


```bash
cd /etc/apparmor.d
for prof in opt.zscaler.bin.*; do
  sudo apparmor_parser -r $prof
done
```
