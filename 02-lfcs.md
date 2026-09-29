# Chapter 2: Linux Foundation LFCS

This guide prepares you; you book, sit and pass the exam yourself.

## At a glance

As of September 2026 (verified on training.linuxfoundation.org and docs.linuxfoundation.org, see Sources).

| Item | Detail |
|---|---|
| Credential | Linux Foundation Certified System Administrator (LFCS) |
| Current version | Competencies revised for exams from 11 May 2023 |
| Format | Online, proctored, performance-based, all command line |
| Tasks | 17-20 hands-on tasks on several remote hosts |
| Duration | 2 hours |
| Passing score | 67% |
| Price (exam only) | USD 445 |
| Bundles | USD 645 with LFS207 course; USD 625 with THRIVE-ONE |
| Delivery | Remote, PSI Bridge secure browser, webcam proctor |
| Scheduling window | 12 months from purchase |
| Retake | 1 free retake per purchase, inside the same 12 months |
| Retake wait | No enforced wait; retake unlocks after No Pass is graded |
| Results | Emailed within 24 hours |
| Validity | 2 years; renew by passing the exam again |
| Simulator | killer.sh, 2 sessions, 36 hours of access each |
| Allowed help | man pages, /usr/share/doc, distro packages |
| Distribution | Official: "independent of distribution-specific tasks" |
| Exam OS in practice | Ubuntu (per your brief); exact version unverified |

Note on the distribution: the official LFCS page says the exam is distribution-independent and you no longer pick a platform. It does not name Ubuntu or a version, so "Ubuntu, version X" is unverified from official pages. This chapter practises on Ubuntu Server 24.04 LTS, which matches your production servers; the skills transfer to any recent Ubuntu.

Why it fits you: LFCS is the Ubuntu/Debian-flavoured counterpart to RHCSA and grades you on live systems, the way you already work. It rewards what you do daily (systemd, Nginx, SSH, Docker, cron) and forces you to close gaps in LVM, NFS, bonding, NAT, libvirt, AppArmor and LDAP. Two years of validity and a free retake keep the cost risk low.

## Objectives map

The five official domains and their weights, with each competency reworded. Strength is judged from your profile.

| Objective area | What you must be able to do | Your current strength |
|---|---|---|
| Ops Deployment (25%) | Set kernel parameters at runtime and persistently | Refresh |
| Ops Deployment | Find and fix misbehaving processes and services | Strong |
| Ops Deployment | Schedule jobs with cron, at and systemd timers | Strong |
| Ops Deployment | Search, install, pin, verify packages; add repos | Refresh |
| Ops Deployment | Recover from boot, OS and filesystem failures | Refresh |
| Ops Deployment | Create and manage VMs with libvirt (virsh) | New |
| Ops Deployment | Configure a container engine and run containers | Strong |
| Ops Deployment | Enforce mandatory access control (SELinux, AppArmor) | New |
| Networking (25%) | Configure IPv4/IPv6 addresses and name resolution | Refresh |
| Networking | Set the clock and sync time with NTP servers | Refresh |
| Networking | Monitor and troubleshoot network traffic | Refresh |
| Networking | Configure the OpenSSH server and client | Strong |
| Networking | Packet filtering, port redirection and NAT | Refresh |
| Networking | Add static routes | New |
| Networking | Build bridge and bond interfaces | New |
| Networking | Run reverse proxies and load balancers | Strong |
| Storage (20%) | Create and grow LVM volumes | New |
| Storage | Work with virtual filesystems (tmpfs, /proc, /sys) | Refresh |
| Storage | Create, mount, check and repair filesystems | Refresh |
| Storage | Use NFS and network block devices | New |
| Storage | Add and manage swap | Refresh |
| Storage | Configure automounting (autofs, systemd) | New |
| Storage | Monitor storage performance | Refresh |
| Essential Commands (20%) | Basic Git: init, commit, branch, merge, remotes | Strong |
| Essential Commands | Create, configure and troubleshoot services | Strong |
| Essential Commands | Monitor system performance and services | Strong |
| Essential Commands | Find a service's limits, ports and dependencies | Refresh |
| Essential Commands | Troubleshoot full disks and inode exhaustion | Strong |
| Essential Commands | Create, inspect and deploy SSL/TLS certificates | Refresh |
| Users and Groups (10%) | Create and manage local users and groups | Strong |
| Users and Groups | Manage user and system-wide shell environment | Refresh |
| Users and Groups | Set per-user resource limits | Refresh |
| Users and Groups | Configure POSIX ACLs | Refresh |
| Users and Groups | Use LDAP accounts for login (SSSD) | New |

Note: the official list says "SELinux" for mandatory access control, while Ubuntu ships AppArmor. Practise AppArmor as the Ubuntu default and keep SELinux basics warm (Task 12, and Chapter 1).

## Study plan

Ten weeks at 6-8 hours a week. Weights drive the time split: Operations and Networking get the most.

| Week | Focus | Hands-on tasks | Resources |
|---|---|---|---|
| 1 | Lab build, Git, baseline timed run | Lab setup, 34-35 | Ubuntu Server docs, man git |
| 2 | Users, sudo, env, limits, ACLs | 43-46 | man useradd, limits.conf, setfacl |
| 3 | systemd services, timers, cron, processes | 2-5, 36-40 | man systemd.service, systemd.timer |
| 4 | apt, repos, sysctl, boot recovery | 1, 6-8 | man apt, sources.list, sysctl.d |
| 5 | netplan, resolved, time, SSH | 13-17 | netplan.readthedocs.io, man sshd_config |
| 6 | ufw, NAT, routes, bond, bridge, Nginx LB | 18-23 | man ufw, ufw-framework, nginx docs |
| 7 | Partitions, filesystems, LVM, swap | 24-27, 31, 33 | man lvm, lvextend, mkswap |
| 8 | NFS, NBD, autofs, I/O perf, LDAP | 28-30, 32, 47 | Ubuntu Server docs (NFS, SSSD, LDAP) |
| 9 | libvirt, Docker, AppArmor, SELinux, TLS | 9-12, 41-42 | man virsh, apparmor.d, openssl-x509 |
| 10 | killer.sh session 1, fix gaps, session 2, book | Redo weakest 10 | killer.sh (included with exam) |

Free resources:
- LFS101 "Introduction to Linux" (free, Linux Foundation / edX)
- Ubuntu Server documentation: https://documentation.ubuntu.com/server/
- Netplan documentation: https://netplan.readthedocs.io/
- man pages and /usr/share/doc on your lab VMs (the same help you get in the exam)

Official, paid:
- LFS207 Linux System Administration Essentials (sold as a bundle with the exam)
- killer.sh LFCS simulator: two sessions come free with the exam purchase; save them for weeks 9-10

Weekly rhythm: 2 short weekday sessions (read plus one task each) and one long weekend session (4-6 tasks timed, then redo the misses from memory).

## Lab setup

Target: two Ubuntu Server 24.04 LTS VMs on your Windows 11 machine, with spare disks and extra NICs. Cost: zero.

| VM | Role | Host-only IP | Extra hardware |
|---|---|---|---|
| lfcs1 | Main practice box | 192.168.56.10 | 3 x 2 GB disks, 2 extra NICs |
| lfcs2 | NFS/NBD/LDAP/Git server, client tests | 192.168.56.11 | none |

Option A: VirtualBox (recommended; easy extra disks and NICs). Install VirtualBox 7.x, download the Ubuntu 24.04.x live server ISO from https://ubuntu.com/download/server, then run in PowerShell:

```powershell
$VBox = "C:\Program Files\Oracle\VirtualBox\VBoxManage.exe"
$Iso  = "$HOME\Downloads\ubuntu-24.04.x-live-server-amd64.iso"   # set real name
$HostOnly = "VirtualBox Host-Only Ethernet Adapter"

foreach ($vm in "lfcs1","lfcs2") {
  $dir = "$HOME\VirtualBox VMs\$vm"
  & $VBox createvm --name $vm --ostype Ubuntu_64 --register
  & $VBox modifyvm $vm --memory 3072 --cpus 2 --nested-hw-virt on
  & $VBox modifyvm $vm --nic1 nat --nic2 hostonly --hostonlyadapter2 $HostOnly
  & $VBox storagectl $vm --name SATA --add sata --controller IntelAhci --portcount 6
  $sa = @("--storagectl","SATA","--device","0")
  & $VBox createmedium disk --filename "$dir\$vm-os.vdi" --size 25600
  & $VBox storageattach $vm @sa --port 0 --type hdd --medium "$dir\$vm-os.vdi"
  & $VBox storageattach $vm @sa --port 5 --type dvddrive --medium $Iso
}

# lfcs1 only: two NICs on an internal network (bond/bridge) and 3 spare disks
& $VBox modifyvm lfcs1 --nic3 intnet --intnet3 labnet --nic4 intnet --intnet4 labnet
foreach ($n in 1..3) {
  $d = "$HOME\VirtualBox VMs\lfcs1\data$n.vdi"
  & $VBox createmedium disk --filename $d --size 2048
  & $VBox storageattach lfcs1 @sa --port $n --type hdd --medium $d
}
& $VBox startvm lfcs1
& $VBox startvm lfcs2
```

Install Ubuntu Server on each VM: keep the default "Use an entire disk" with "Set up this disk as an LVM group" ticked, install OpenSSH server, skip snaps. Do not pick the minimized install (it strips man pages; if you did, run `sudo unminimize`).

After first boot, on both VMs:

```bash
sudo apt update && sudo apt full-upgrade -y
sudo apt install -y man-db manpages vim git curl tree acl lvm2 xfsprogs \
  sysstat iotop tcpdump nfs-common apparmor-utils bash-completion
sudo hostnamectl set-hostname lfcs1.lab.local     # lfcs2.lab.local on the other
lsblk                                            # lfcs1: sda plus sdb, sdc, sdd
ip -br link                                      # enp0s3 (NAT), enp0s8, enp0s9, enp0s10
```

Set the host-only address once (Task 13 does it properly; this is enough to SSH in from Windows):

```bash
sudo ip addr add 192.168.56.10/24 dev enp0s8     # .11 on lfcs2
sudo ip link set enp0s8 up
```

Snapshots are your reset button. Power the VMs off and take a clean snapshot before you start the tasks:

```powershell
& $VBox snapshot lfcs1 take clean-install
& $VBox snapshot lfcs2 take clean-install
# later, with the VM powered off:
& $VBox snapshot lfcs1 restore clean-install
```

Notes:
- If Hyper-V or WSL2 is enabled, VirtualBox still runs but nested KVM may be unavailable. Task 9 then falls back to `--virt-type qemu` (slow but fine for a tiny CirrOS guest).
- No spare disks? Loop devices work for Tasks 24-27: `truncate -s 2G /var/tmp/d1.img && sudo losetup -fP --show /var/tmp/d1.img`.
- Option B (no VirtualBox): `winget install Canonical.Multipass`, then `multipass launch 24.04 --name lfcs1 --cpus 2 --memory 3G --disk 25G`. Easy, but extra NICs and disks are harder, so use loop devices.
- For Task 12 (SELinux) reuse the Rocky/Alma 9 VM from Chapter 1.

## Hands-on tasks

All tasks assume Ubuntu Server 24.04 LTS, run as a sudo user, lfcs1 = 192.168.56.10 and lfcs2 = 192.168.56.11. Every change must survive a reboot unless the task says otherwise. Task counts follow the weights: Operations 12, Networking 11, Storage 10, Essential Commands 9, Users and Groups 5.

### Task 1: Kernel parameters, runtime and persistent

**Task:** On lfcs1, set `vm.swappiness` to 10 for the running system only. Make IPv4 forwarding and `net.core.somaxconn = 4096` persistent across reboots.

**Solution:**
```bash
sudo sysctl -w vm.swappiness=10                  # runtime only, gone after reboot

sudo tee /etc/sysctl.d/60-lfcs.conf >/dev/null <<'EOF'
net.ipv4.ip_forward = 1
net.core.somaxconn = 4096
EOF
sudo sysctl --system                             # load every sysctl.d file now
```

**Verify:**
```bash
sysctl vm.swappiness net.ipv4.ip_forward net.core.somaxconn
grep -r somaxconn /etc/sysctl.d/
```

### Task 2: Troubleshoot a runaway process

**Task:** A CPU hog is running. Find the process using the most CPU, lower its priority to nice 15, then stop it gracefully. Start `tar` backups at nice 10 from now on.

**Solution:**
```bash
yes > /dev/null &                                # simulate the hog
ps -eo pid,user,ni,pcpu,comm --sort=-pcpu | head -5
PID=$(pgrep -x yes)
sudo renice -n 15 -p "$PID"
kill -TERM "$PID"                                # use -KILL only if TERM fails
nice -n 10 tar czf /tmp/etc.tgz /etc 2>/dev/null
```

**Verify:**
```bash
pgrep -x yes || echo "no hog running"
ps -o pid,ni,comm -p "$PID" 2>/dev/null || echo "process gone"
```

### Task 3: Fix a service that will not start

**Task:** Nginx on lfcs1 fails to start. Find the cause from the logs, fix it, and make sure it starts at boot.

**Solution:**
```bash
# setup the fault
sudo apt install -y nginx
echo "server { listen 80 }" | sudo tee /etc/nginx/conf.d/broken.conf
sudo systemctl restart nginx                     # fails

# diagnose
systemctl status nginx --no-pager
journalctl -u nginx -b --no-pager | tail -20
sudo nginx -t                                    # points at broken.conf (missing ;)
sudo ss -tlnp 'sport = :80'                      # also rule out a port clash

# fix
sudo rm /etc/nginx/conf.d/broken.conf
sudo nginx -t && sudo systemctl enable --now nginx
```

**Verify:**
```bash
systemctl is-active nginx; systemctl is-enabled nginx
curl -sI http://localhost | head -1
```

### Task 4: Schedule jobs with cron and at

**Task:** As user `deploy`, run `/usr/local/bin/backup.sh` at 02:30 every weekday. Add a system cron job that runs `/usr/local/bin/cleanup.sh` as root every 15 minutes. Schedule a one-off job with `at` that logs a message at 23:00 today.

**Solution:**
```bash
sudo useradd -m -s /bin/bash deploy
printf '#!/bin/bash\ndate >> /tmp/backup.log\n' | sudo tee /usr/local/bin/backup.sh
sudo cp /usr/local/bin/backup.sh /usr/local/bin/cleanup.sh
sudo chmod 755 /usr/local/bin/backup.sh /usr/local/bin/cleanup.sh

(sudo crontab -u deploy -l 2>/dev/null; echo "30 2 * * 1-5 /usr/local/bin/backup.sh") \
  | sudo crontab -u deploy -

echo "*/15 * * * * root /usr/local/bin/cleanup.sh" | sudo tee /etc/cron.d/cleanup
sudo chmod 644 /etc/cron.d/cleanup

sudo apt install -y at
echo 'logger "at job ran"' | at 23:00
```

**Verify:**
```bash
sudo crontab -u deploy -l
cat /etc/cron.d/cleanup
atq
```

### Task 5: systemd timer instead of cron

**Task:** Create `logrotate-app.service` and a timer that runs it daily at 03:15. If the machine was off at that time, the job must run at next boot.

**Solution:**
```bash
sudo tee /etc/systemd/system/logrotate-app.service >/dev/null <<'EOF'
[Unit]
Description=Compress old app logs

[Service]
Type=oneshot
ExecStart=/usr/bin/find /var/log -name "*.log.1" -exec gzip -f {} +
EOF

sudo tee /etc/systemd/system/logrotate-app.timer >/dev/null <<'EOF'
[Unit]
Description=Daily app log compression

[Timer]
OnCalendar=*-*-* 03:15:00
Persistent=true

[Install]
WantedBy=timers.target
EOF

sudo systemctl daemon-reload
sudo systemctl enable --now logrotate-app.timer
```

**Verify:**
```bash
systemctl list-timers logrotate-app.timer
systemd-analyze calendar "*-*-* 03:15:00"
sudo systemctl start logrotate-app.service && systemctl status logrotate-app --no-pager
```

### Task 6: Package queries, pinning and verification

**Task:** Show the installed and candidate versions of `nginx`, hold it so upgrades skip it, find which package owns `/usr/bin/dig`, list files installed by `curl`, and check whether any file of the `nginx-common` package has been modified.

**Solution:**
```bash
apt-cache policy nginx
apt list -a nginx 2>/dev/null
sudo apt-mark hold nginx

dpkg -S /usr/bin/dig                             # works for installed packages
sudo apt install -y apt-file && sudo apt-file update
apt-file search bin/dig                          # works for packages not installed

dpkg -L curl
sudo dpkg --verify nginx-common                  # no output = files unchanged
```

**Verify:**
```bash
apt-mark showhold
sudo apt upgrade -s | grep -i nginx || echo "nginx held"
```

### Task 7: Add a third-party APT repository the modern way

**Task:** Add the official nginx.org stable repository for Ubuntu 24.04 using a dedicated keyring and a deb822 `.sources` file. Do not install from it; just make the packages visible.

**Solution:**
```bash
sudo apt-mark unhold nginx
curl -fsSL https://nginx.org/keys/nginx_signing.key \
  | sudo gpg --dearmor -o /usr/share/keyrings/nginx.gpg

sudo tee /etc/apt/sources.list.d/nginx.sources >/dev/null <<'EOF'
Types: deb
URIs: http://nginx.org/packages/ubuntu
Suites: noble
Components: nginx
Signed-By: /usr/share/keyrings/nginx.gpg
EOF
sudo apt update
```

**Verify:**
```bash
apt-cache policy nginx | grep -A1 nginx.org
ls /etc/apt/sources.list.d/
```

Clean up afterwards if you prefer the Ubuntu build: `sudo rm /etc/apt/sources.list.d/nginx.sources && sudo apt update`.

### Task 8: Recover from a bad fstab and a damaged filesystem

**Task:** A typo in `/etc/fstab` could stop lfcs1 booting. Make an optional data mount non-fatal, check and repair an unmounted ext4 filesystem, and know how to get a root shell on Ubuntu when root is locked.

**Solution:**
```bash
# 1. Validate fstab before any reboot
sudo findmnt --verify --verbose
# optional mounts get nofail so boot continues if the device is missing:
# UUID=...  /data1  ext4  defaults,nofail  0  2

# 2. Check/repair an unmounted filesystem (use a loop device to practise)
truncate -s 200M /var/tmp/fs.img
LOOP=$(sudo losetup -f --show /var/tmp/fs.img)
sudo mkfs.ext4 -q "$LOOP"
sudo e2fsck -f -y "$LOOP"                        # never on a mounted filesystem
sudo losetup -d "$LOOP"

# 3. Root shell when boot hangs (console access):
# hold Shift (BIOS) or Esc (UEFI) -> GRUB -> press e on the Ubuntu entry
# append to the line starting with "linux":   init=/bin/bash
# Ctrl+X to boot, then:
#   mount -o remount,rw /
#   vim /etc/fstab            # fix the entry
#   sync; exec /sbin/init     # or: reboot -f
```

**Verify:**
```bash
sudo findmnt --verify && echo "fstab OK"
sudo mount -a && echo "all mounts OK"
```

Why `init=/bin/bash`: Ubuntu locks the root password, so `rescue.target` and `emergency.target` refuse to open a shell.

### Task 9: Manage a virtual machine with libvirt

**Task:** Install KVM/libvirt on lfcs1, import the CirrOS test image as VM `vm1` with 512 MiB RAM and 1 vCPU on the `default` network, make it start at host boot, then raise its memory to 768 MiB in the persistent config.

**Solution:**
```bash
sudo apt install -y qemu-kvm libvirt-daemon-system libvirt-clients virtinst
sudo usermod -aG libvirt,kvm "$USER"             # log out/in, or use sudo below
kvm-ok 2>/dev/null || ls /dev/kvm                # no /dev/kvm -> add --virt-type qemu

cd /var/lib/libvirt/images
sudo curl -LO https://download.cirros-cloud.net/0.6.2/cirros-0.6.2-x86_64-disk.img
sudo cp cirros-0.6.2-x86_64-disk.img vm1.qcow2

sudo virsh net-start default 2>/dev/null; sudo virsh net-autostart default
sudo virt-install --name vm1 --memory 512 --vcpus 1 \
  --disk /var/lib/libvirt/images/vm1.qcow2 --import \
  --osinfo detect=on,require=off --network network=default \
  --graphics none --noautoconsole

sudo virsh autostart vm1
sudo virsh shutdown vm1
sudo virsh setmaxmem vm1 768M --config
sudo virsh setmem vm1 768M --config
sudo virsh start vm1
```

**Verify:**
```bash
sudo virsh list --all
sudo virsh dominfo vm1 | grep -E 'State|Max memory|Autostart|CPU\(s\)'
sudo virsh domifaddr vm1
```

Other verbs worth knowing: `virsh console vm1` (exit with Ctrl+]), `virsh destroy` (hard stop), `virsh undefine vm1 --remove-all-storage`, `virsh edit vm1`.

### Task 10: Run and build containers with Docker

**Task:** Install Docker from the Ubuntu archive. Run `nginx:alpine` as container `web`, publishing host port 8080, serving `/srv/web` read-only, and restarting unless stopped. Build an image `api:1.0` from a Dockerfile for a small Node app and run it on port 3000, bound to localhost only.

**Solution:**
```bash
sudo apt install -y docker.io
sudo systemctl enable --now docker
sudo usermod -aG docker "$USER"                  # new login needed

sudo mkdir -p /srv/web && echo "hello lfcs" | sudo tee /srv/web/index.html
sudo docker run -d --name web -p 8080:80 --restart unless-stopped \
  -v /srv/web:/usr/share/nginx/html:ro nginx:alpine

mkdir -p ~/api && cd ~/api
cat > server.js <<'EOF'
require('http').createServer((q, s) => s.end('api ok\n')).listen(3000);
EOF
cat > Dockerfile <<'EOF'
FROM node:20-alpine
WORKDIR /app
COPY server.js .
EXPOSE 3000
CMD ["node", "server.js"]
EOF
sudo docker build -t api:1.0 .
sudo docker run -d --name api -p 127.0.0.1:3000:3000 --restart unless-stopped api:1.0
```

**Verify:**
```bash
sudo docker ps --format '{{.Names}} {{.Ports}} {{.Status}}'
sudo docker inspect -f '{{.HostConfig.RestartPolicy.Name}}' web
curl -s localhost:8080; curl -s localhost:3000
```

Trap: ports published with `-p 8080:80` bypass ufw rules because Docker writes its own iptables chains. Bind to `127.0.0.1` or filter in the `DOCKER-USER` chain. Podman is also in the archive (`apt install podman`) if a task asks for it; the CLI is the same.

### Task 11: Confine a script with AppArmor

**Task:** Write an AppArmor profile for `/usr/local/bin/report.sh`. The script may append to `/var/log/report.log` and run `date`, but must be denied reading `/etc/hostname`. Load it in enforce mode, then show how to switch it to complain mode.

**Solution:**
```bash
sudo tee /usr/local/bin/report.sh >/dev/null <<'EOF'
#!/bin/bash
date >> /var/log/report.log
cat /etc/hostname
EOF
sudo chmod 755 /usr/local/bin/report.sh

sudo tee /etc/apparmor.d/usr.local.bin.report.sh >/dev/null <<'EOF'
#include <tunables/global>

/usr/local/bin/report.sh {
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/consoles>

  /usr/local/bin/report.sh r,
  /usr/bin/bash ix,
  /usr/bin/date ix,
  /usr/bin/cat ix,
  /var/log/report.log w,
}
EOF
sudo apparmor_parser -r /etc/apparmor.d/usr.local.bin.report.sh

# switch modes (from apparmor-utils)
sudo aa-complain /usr/local/bin/report.sh
sudo aa-enforce  /usr/local/bin/report.sh
```

**Verify:**
```bash
sudo aa-status | grep -A2 report
sudo /usr/local/bin/report.sh                   # cat: /etc/hostname: Permission denied
tail -1 /var/log/report.log                     # date line was written
sudo journalctl -k --since "5 min ago" | grep 'apparmor="DENIED"'
```

If other harmless denials appear, `sudo aa-logprof` walks you through adding rules.

### Task 12: SELinux basics (Rocky/Alma 9 VM)

**Task:** The official objective names SELinux. On an RHEL-family VM, serve web content from `/srv/web` under Apache, let httpd connect to a backend, and add port 8081 to the web port type.

**Solution:**
```bash
sudo dnf install -y httpd policycoreutils-python-utils
sudo mkdir -p /srv/web && echo ok | sudo tee /srv/web/index.html
sudo semanage fcontext -a -t httpd_sys_content_t "/srv/web(/.*)?"
sudo restorecon -Rv /srv/web
sudo setsebool -P httpd_can_network_connect on
sudo semanage port -a -t http_port_t -p tcp 8081
```

**Verify:**
```bash
getenforce
ls -Zd /srv/web
getsebool httpd_can_network_connect
sudo semanage port -l | grep ^http_port_t
```

### Task 13: Static IPv4 and IPv6 with netplan

**Task:** On lfcs1, give `enp0s8` the static addresses 192.168.56.10/24 and fd00:56::10/64, DNS 192.168.56.11 then 1.1.1.1, search domain `lab.local`. Keep DHCP on `enp0s3`. Apply without locking yourself out.

**Solution:**
```bash
sudo tee /etc/netplan/60-hostonly.yaml >/dev/null <<'EOF'
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s8:
      dhcp4: false
      dhcp6: false
      accept-ra: false
      addresses:
        - 192.168.56.10/24
        - "fd00:56::10/64"
      nameservers:
        addresses: [192.168.56.11, 1.1.1.1]
        search: [lab.local]
EOF
sudo chmod 600 /etc/netplan/60-hostonly.yaml
sudo netplan generate                            # syntax check
sudo netplan try                                 # auto-rollback after 120 s
sudo netplan apply
```

**Verify:**
```bash
ip -br addr show enp0s8
networkctl status enp0s8 --no-pager
resolvectl dns enp0s8; resolvectl domain enp0s8
ping -c1 192.168.56.11; ping -6 -c1 fd00:56::11   # after lfcs2 gets .11 / ::11
```

Repeat on lfcs2 with .11 and ::11. Do not add a default route on enp0s8; the NAT NIC already has one.

### Task 14: Hostname and name resolution

**Task:** Set the hostname to `lfcs1.lab.local`. Make `lfcs2` and `lfcs2.lab.local` resolve to 192.168.56.11 locally. Configure systemd-resolved globally to use 9.9.9.9 as a fallback DNS server.

**Solution:**
```bash
sudo hostnamectl set-hostname lfcs1.lab.local
echo "192.168.56.11 lfcs2.lab.local lfcs2" | sudo tee -a /etc/hosts

sudo mkdir -p /etc/systemd/resolved.conf.d
sudo tee /etc/systemd/resolved.conf.d/lab.conf >/dev/null <<'EOF'
[Resolve]
FallbackDNS=9.9.9.9
EOF
sudo systemctl restart systemd-resolved
```

**Verify:**
```bash
hostnamectl --static
getent hosts lfcs2                                # uses nsswitch: files then dns
resolvectl status | head -20
resolvectl query ubuntu.com
ls -l /etc/resolv.conf                            # symlink to the 127.0.0.53 stub
```

### Task 15: Time zone and NTP synchronisation

**Task:** Set the time zone to Asia/Karachi. Make systemd-timesyncd use `ntp.ubuntu.com` and `0.pool.ntp.org`. Then, on lfcs2, replace timesyncd with chrony and let the 192.168.56.0/24 network use it as an NTP server.

**Solution:**
```bash
# lfcs1: timesyncd (Ubuntu 24.04 default)
sudo timedatectl set-timezone Asia/Karachi
sudo mkdir -p /etc/systemd/timesyncd.conf.d
sudo tee /etc/systemd/timesyncd.conf.d/lab.conf >/dev/null <<'EOF'
[Time]
NTP=ntp.ubuntu.com 0.pool.ntp.org
EOF
sudo timedatectl set-ntp true
sudo systemctl restart systemd-timesyncd

# lfcs2: chrony as server (installing chrony removes systemd-timesyncd)
sudo apt install -y chrony
echo "allow 192.168.56.0/24" | sudo tee /etc/chrony/conf.d/lab-server.conf
sudo systemctl restart chrony
sudo ufw allow from 192.168.56.0/24 to any port 123 proto udp
```

**Verify:**
```bash
timedatectl                                   # "System clock synchronized: yes"
timedatectl timesync-status                   # lfcs1
chronyc sources -v                            # lfcs2
sudo chronyc clients                          # lfcs2, once lfcs1 points at it
```

### Task 16: Harden the OpenSSH server (socket-activated on 24.04)

**Task:** On lfcs1, make sshd listen on port 2222 (and 22 during the change), disable root login and password authentication. Keep the change in a drop-in file.

**Solution:**
```bash
sudo ufw allow 2222/tcp
sudo tee /etc/ssh/sshd_config.d/10-lfcs.conf >/dev/null <<'EOF'
Port 22
Port 2222
PermitRootLogin no
PasswordAuthentication no
KbdInteractiveAuthentication no
EOF
sudo sshd -t                                     # syntax check first
# Ubuntu 24.04 uses ssh.socket: ports are read at daemon-reload by a generator
sudo systemctl daemon-reload
sudo systemctl restart ssh.socket
```

**Verify:**
```bash
sudo ss -tlnp | grep -E ':(22|2222)\b'
sudo sshd -T | grep -Ei '^(port|permitrootlogin|passwordauthentication)'
ssh -p 2222 -o PasswordAuthentication=no localhost true && echo ok
```

Trap: sshd uses the first value it reads, and files in `sshd_config.d` load in name order. A cloud image's `50-cloud-init.conf` can set `PasswordAuthentication yes`, so your file must sort earlier (`10-`).

### Task 17: SSH client keys and config

**Task:** From lfcs2, create an ed25519 key, install it for user `deploy` on lfcs1 (port 2222), and create a client alias `app1` so that `ssh app1` connects as deploy with that key.

**Solution:**
```bash
# on lfcs1 first: give deploy a temporary way in, or copy the key as your sudo user
# on lfcs2:
ssh-keygen -t ed25519 -f ~/.ssh/id_lab -N "" -C "lab key"
cat ~/.ssh/id_lab.pub | ssh -p 2222 youruser@192.168.56.10 \
  "sudo install -d -m 700 -o deploy -g deploy ~deploy/.ssh && \
   sudo tee -a ~deploy/.ssh/authorized_keys >/dev/null && \
   sudo chown deploy:deploy ~deploy/.ssh/authorized_keys && \
   sudo chmod 600 ~deploy/.ssh/authorized_keys"

cat >> ~/.ssh/config <<'EOF'
Host app1
    HostName 192.168.56.10
    Port 2222
    User deploy
    IdentityFile ~/.ssh/id_lab
    IdentitiesOnly yes
EOF
chmod 600 ~/.ssh/config
```

Note: `~deploy` expands on lfcs1 because the whole command runs there. `ssh-copy-id -i ~/.ssh/id_lab -p 2222 deploy@host` is simpler when password login is still on.

**Verify:**
```bash
ssh app1 'whoami; hostname'
ssh -G app1 | grep -E '^(hostname|port|user|identityfile) '
```

### Task 18: Packet filtering with ufw

**Task:** On lfcs1: deny incoming by default, allow outgoing, allow SSH (22 and 2222) only from 192.168.56.0/24, allow HTTP and HTTPS from anywhere, and rate-limit port 2222. Delete the rule for port 443 again, then log denied packets.

**Solution:**
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow from 192.168.56.0/24 to any port 22 proto tcp
sudo ufw limit from 192.168.56.0/24 to any port 2222 proto tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable                                  # answer y; SSH rules exist first
sudo ufw status numbered
sudo ufw delete allow 443/tcp                    # or: ufw delete <number>
sudo ufw logging low
```

**Verify:**
```bash
sudo ufw status verbose
sudo ufw show added
nc -zv 192.168.56.10 80                          # from lfcs2
sudo journalctl -k | grep 'UFW BLOCK' | tail -3
```

Remove the earlier broad `ufw allow 2222/tcp` rule if it is still listed, or the limit rule is moot.

### Task 19: Port redirection and NAT (masquerade)

**Task:** On lfcs1, redirect incoming TCP 80 on `enp0s8` to local port 3000. Also make lfcs1 a NAT gateway: hosts on 10.50.0.0/24 (internal NICs) leave via `enp0s3` with masquerading. Everything must persist with ufw.

**Solution:**
```bash
# forwarding must be on (Task 1) and ufw must allow routed traffic
sudo sed -i 's/^DEFAULT_FORWARD_POLICY=.*/DEFAULT_FORWARD_POLICY="ACCEPT"/' \
  /etc/default/ufw

# add a nat table at the very top of /etc/ufw/before.rules (before *filter)
sudo cp /etc/ufw/before.rules /etc/ufw/before.rules.bak
sudo sed -i '1i\
*nat\
:PREROUTING ACCEPT [0:0]\
:POSTROUTING ACCEPT [0:0]\
-A PREROUTING -i enp0s8 -p tcp --dport 80 -j REDIRECT --to-ports 3000\
-A POSTROUTING -s 10.50.0.0/24 -o enp0s3 -j MASQUERADE\
COMMIT\
' /etc/ufw/before.rules

sudo ufw allow in on enp0s8 to any port 3000 proto tcp   # filter sees port 3000
sudo ufw reload

# a test backend on 3000
python3 -m http.server 3000 --directory /srv/web &
```

**Verify:**
```bash
sudo iptables -t nat -S | grep -E 'REDIRECT|MASQUERADE'
curl -s http://192.168.56.10/                    # run on lfcs2
sysctl net.ipv4.ip_forward
```

Trap: PREROUTING only sees packets arriving from the network. `curl localhost:80` on lfcs1 itself is not redirected; that needs an OUTPUT-chain rule.

### Task 20: Static routes

**Task:** Traffic to 10.20.0.0/16 must go via 192.168.56.1 on `enp0s8`. Add it now for testing, then make it persistent with netplan.

**Solution:**
```bash
sudo ip route add 10.20.0.0/16 via 192.168.56.1 dev enp0s8     # runtime only

# persistent: add under enp0s8 in /etc/netplan/60-hostonly.yaml
#      routes:
#        - to: 10.20.0.0/16
#          via: 192.168.56.1
sudo netplan try && sudo netplan apply
```

The resulting `enp0s8` block:

```yaml
    enp0s8:
      dhcp4: false
      dhcp6: false
      accept-ra: false
      addresses:
        - 192.168.56.10/24
        - "fd00:56::10/64"
      routes:
        - to: 10.20.0.0/16
          via: 192.168.56.1
      nameservers:
        addresses: [192.168.56.11, 1.1.1.1]
        search: [lab.local]
```

**Verify:**
```bash
ip route show 10.20.0.0/16
ip route get 10.20.1.1                           # shows via 192.168.56.1 dev enp0s8
```

### Task 21: Bond two NICs (active-backup)

**Task:** Bond `enp0s9` and `enp0s10` into `bond0` in active-backup mode with `enp0s9` primary and 100 ms link monitoring. Address 10.50.0.10/24.

**Solution:**
```bash
sudo tee /etc/netplan/70-bond.yaml >/dev/null <<'EOF'
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s9: {dhcp4: false}
    enp0s10: {dhcp4: false}
  bonds:
    bond0:
      interfaces: [enp0s9, enp0s10]
      addresses: [10.50.0.10/24]
      parameters:
        mode: active-backup
        primary: enp0s9
        mii-monitor-interval: 100
EOF
sudo chmod 600 /etc/netplan/70-bond.yaml
sudo netplan apply
```

**Verify:**
```bash
cat /proc/net/bonding/bond0 | grep -E 'Mode|Currently Active|Slave Interface'
ip -br addr show bond0
sudo ip link set enp0s9 down; grep 'Currently Active' /proc/net/bonding/bond0
sudo ip link set enp0s9 up
```

### Task 22: Bridge interface

**Task:** Remove the bond, then create bridge `br0` containing `enp0s9`, with address 10.60.0.10/24, STP off. (Bridges are what libvirt guests attach to for LAN access.)

**Solution:**
```bash
sudo rm /etc/netplan/70-bond.yaml
sudo ip link delete bond0 2>/dev/null
sudo tee /etc/netplan/70-bridge.yaml >/dev/null <<'EOF'
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s9: {dhcp4: false}
  bridges:
    br0:
      interfaces: [enp0s9]
      addresses: [10.60.0.10/24]
      parameters:
        stp: false
        forward-delay: 0
EOF
sudo chmod 600 /etc/netplan/70-bridge.yaml
sudo netplan apply
```

**Verify:**
```bash
bridge link show
ip -d link show br0 | grep -o 'bridge.*stp_state [0-9]'
ip -br addr show br0
```

### Task 23: Reverse proxy and load balancer with Nginx

**Task:** Serve `app.lab.local` on port 80 with Nginx, balancing across two backends on 127.0.0.1:3001 and 127.0.0.1:3002 using least connections, passing the client IP headers. Remove the default site.

**Solution:**
```bash
mkdir -p /tmp/b1 /tmp/b2
echo backend-1 > /tmp/b1/index.html; echo backend-2 > /tmp/b2/index.html
python3 -m http.server 3001 --bind 127.0.0.1 --directory /tmp/b1 &
python3 -m http.server 3002 --bind 127.0.0.1 --directory /tmp/b2 &

sudo tee /etc/nginx/sites-available/app >/dev/null <<'EOF'
upstream app_backend {
    least_conn;
    server 127.0.0.1:3001 max_fails=3 fail_timeout=10s;
    server 127.0.0.1:3002 max_fails=3 fail_timeout=10s;
}

server {
    listen 80;
    server_name app.lab.local;

    location / {
        proxy_pass http://app_backend;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
EOF
sudo ln -sf /etc/nginx/sites-available/app /etc/nginx/sites-enabled/app
sudo rm -f /etc/nginx/sites-enabled/default
sudo nginx -t && sudo systemctl reload nginx
```

**Verify:**
```bash
for i in 1 2 3 4; do curl -s -H 'Host: app.lab.local' http://127.0.0.1/; done
kill %1                                            # stop backend-1
curl -s -H 'Host: app.lab.local' http://127.0.0.1/ # still answers (backend-2)
```

If Task 19's redirect is active on enp0s8, test via 127.0.0.1 as above. HAProxy (`apt install haproxy`) is an acceptable alternative if a task names it.

### Task 24: Partition, format and mount persistently

**Task:** On `/dev/sdb` create a GPT label with two equal partitions. Format the first ext4 (label `data1`) and the second XFS (label `data2`). Mount them at `/data1` and `/data2` by UUID at boot.

**Solution:**
```bash
sudo parted -s /dev/sdb mklabel gpt \
  mkpart data1 ext4 1MiB 50% mkpart data2 xfs 50% 100%
sudo mkfs.ext4 -L data1 /dev/sdb1
sudo mkfs.xfs  -L data2 /dev/sdb2
sudo mkdir -p /data1 /data2

U1=$(sudo blkid -s UUID -o value /dev/sdb1)
U2=$(sudo blkid -s UUID -o value /dev/sdb2)
echo "UUID=$U1 /data1 ext4 defaults 0 2" | sudo tee -a /etc/fstab
echo "UUID=$U2 /data2 xfs  defaults 0 0" | sudo tee -a /etc/fstab
sudo systemctl daemon-reload
sudo mount -a
```

**Verify:**
```bash
lsblk -f /dev/sdb
findmnt /data1; findmnt /data2
sudo findmnt --verify
```

### Task 25: Create an LVM volume

**Task:** Using `/dev/sdc`, create volume group `vg_app` and a 1 GiB logical volume `lv_web` with ext4, mounted persistently at `/srv/web`.

**Solution:**
```bash
sudo pvcreate /dev/sdc
sudo vgcreate vg_app /dev/sdc
sudo lvcreate -n lv_web -L 1G vg_app
sudo mkfs.ext4 /dev/vg_app/lv_web
sudo mkdir -p /srv/web
echo "/dev/vg_app/lv_web /srv/web ext4 defaults 0 2" | sudo tee -a /etc/fstab
sudo systemctl daemon-reload && sudo mount -a
```

**Verify:**
```bash
sudo pvs; sudo vgs; sudo lvs
df -h /srv/web
```

### Task 26: Grow LVM storage online

**Task:** Add `/dev/sdd` to `vg_app`, grow `lv_web` by 1.5 GiB with its filesystem in one step, and give the Ubuntu root LV all free space left in `ubuntu-vg`.

**Solution:**
```bash
sudo pvcreate /dev/sdd
sudo vgextend vg_app /dev/sdd
sudo lvextend -r -L +1.5G /dev/vg_app/lv_web     # -r resizes ext4/xfs too

sudo vgs ubuntu-vg                               # installer often leaves VFree
sudo lvextend -r -l +100%FREE /dev/ubuntu-vg/ubuntu-lv
```

**Verify:**
```bash
sudo lvs -o lv_name,vg_name,lv_size
df -h /srv/web /
```

Shrinking: ext4 can shrink only when unmounted (`lvreduce -r`); XFS cannot shrink at all.

### Task 27: Add swap space

**Task:** Add a 512 MiB swap file `/swapfile2` with priority 10, and a 256 MiB swap LV `lv_swap` in `vg_app` with priority 5. Both persistent.

**Solution:**
```bash
sudo fallocate -l 512M /swapfile2
sudo chmod 600 /swapfile2
sudo mkswap /swapfile2
sudo swapon -p 10 /swapfile2
echo "/swapfile2 none swap sw,pri=10 0 0" | sudo tee -a /etc/fstab

sudo lvcreate -n lv_swap -L 256M vg_app
sudo mkswap /dev/vg_app/lv_swap
sudo swapon -p 5 /dev/vg_app/lv_swap
echo "/dev/vg_app/lv_swap none swap sw,pri=5 0 0" | sudo tee -a /etc/fstab
```

**Verify:**
```bash
swapon --show
free -h
sudo swapoff -a && sudo swapon -a && swapon --show   # proves fstab entries work
```

### Task 28: NFS server and client

**Task:** On lfcs2, export `/srv/share` read-write to 192.168.56.0/24. On lfcs1, mount it at `/mnt/share` at boot without hanging the boot if lfcs2 is down.

**Solution:**
```bash
# lfcs2
sudo apt install -y nfs-kernel-server
sudo mkdir -p /srv/share && sudo chown nobody:nogroup /srv/share
echo "/srv/share 192.168.56.0/24(rw,sync,no_subtree_check)" | sudo tee -a /etc/exports
sudo exportfs -ra
sudo ufw allow from 192.168.56.0/24 to any port nfs

# lfcs1
sudo apt install -y nfs-common
sudo mkdir -p /mnt/share
echo "lfcs2:/srv/share /mnt/share nfs defaults,_netdev,nofail 0 0" \
  | sudo tee -a /etc/fstab
sudo systemctl daemon-reload && sudo mount /mnt/share
```

**Verify:**
```bash
sudo exportfs -v                                  # lfcs2
showmount -e lfcs2                                # lfcs1
findmnt /mnt/share
touch /mnt/share/hello && ls -l /mnt/share
```

### Task 29: Network block device (NBD)

**Task:** On lfcs2, export a 1 GiB image file as NBD export `disk1`. On lfcs1, attach it as `/dev/nbd0`, format it ext4 and mount it at `/mnt/nbd`. Then detach it cleanly.

**Solution:**
```bash
# lfcs2
sudo apt install -y nbd-server
sudo mkdir -p /srv/nbd && sudo truncate -s 1G /srv/nbd/disk1.img
sudo chown nbd:nbd /srv/nbd/disk1.img
sudo tee /etc/nbd-server/config >/dev/null <<'EOF'
[generic]
    user = nbd
    group = nbd
    allowlist = true
[disk1]
    exportname = /srv/nbd/disk1.img
EOF
sudo systemctl restart nbd-server
sudo ufw allow from 192.168.56.0/24 to any port 10809 proto tcp

# lfcs1
sudo apt install -y nbd-client
sudo modprobe nbd
sudo nbd-client -N disk1 lfcs2 /dev/nbd0
sudo mkfs.ext4 -q /dev/nbd0
sudo mkdir -p /mnt/nbd && sudo mount /dev/nbd0 /mnt/nbd
```

**Verify:**
```bash
nbd-client -l lfcs2                               # lists exports (allowlist=true)
lsblk /dev/nbd0; findmnt /mnt/nbd
sudo umount /mnt/nbd && sudo nbd-client -d /dev/nbd0
```

iSCSI is the other common block-over-network option (`targetcli` on the server, `open-iscsi` / `iscsiadm` on the client); know that it exists.

### Task 30: Automount with autofs and systemd

**Task:** On lfcs1, use autofs so that accessing `/nfs/share` mounts `lfcs2:/srv/share` on demand and unmounts after 60 s idle. Then show the systemd-native alternative for `/mnt/share`.

**Solution:**
```bash
sudo apt install -y autofs
echo "/nfs /etc/auto.nfs --timeout=60" | sudo tee /etc/auto.master.d/nfs.autofs
echo "share -rw,soft lfcs2:/srv/share" | sudo tee /etc/auto.nfs
sudo systemctl restart autofs
# wildcard form for many exports:  *  -rw  lfcs2:/srv/&

# systemd alternative: fstab line for /mnt/share becomes
# (one line in the real file)
# lfcs2:/srv/share /mnt/share nfs
#   noauto,x-systemd.automount,x-systemd.idle-timeout=60,_netdev 0 0
```

**Verify:**
```bash
ls /nfs                                           # empty: nothing mounted yet
ls /nfs/share                                     # triggers the mount
mount | grep /nfs/share
systemctl list-units --type=automount             # for the systemd variant
```

### Task 31: Virtual filesystems (tmpfs, /proc, /sys)

**Task:** Mount a 256 MiB tmpfs at `/mnt/scratch` with sticky world-writable permissions, persistent. Then read the I/O scheduler of `/dev/sda` from sysfs and the kernel command line from procfs.

**Solution:**
```bash
sudo mkdir -p /mnt/scratch
echo "tmpfs /mnt/scratch tmpfs size=256M,mode=1777 0 0" | sudo tee -a /etc/fstab
sudo systemctl daemon-reload && sudo mount /mnt/scratch

cat /sys/block/sda/queue/scheduler
cat /proc/cmdline
sudo mount -o remount,size=512M /mnt/scratch     # runtime resize
```

**Verify:**
```bash
findmnt /mnt/scratch
df -h /mnt/scratch; stat -c '%A' /mnt/scratch    # drwxrwxrwt
```

### Task 32: Monitor storage performance

**Task:** Generate write load on `/data1`, then identify the busiest disk, its utilisation and wait time, and the process responsible.

**Solution:**
```bash
sudo apt install -y sysstat iotop
sudo dd if=/dev/zero of=/data1/load bs=1M count=800 oflag=direct &
iostat -xz 2 3                                   # watch %util, w_await, wMB/s
pidstat -d 2 3                                   # per-process kB_wr/s
sudo iotop -o -b -n 3                            # only processes doing I/O
wait; sudo rm -f /data1/load
```

**Verify:**
```bash
iostat -dx sdb 1 1 | tail -2
vmstat 1 3                                       # "wa" column = CPU waiting on I/O
```

### Task 33: Check and tune filesystems

**Task:** On `/data1` (ext4), reduce reserved blocks to 1% and change the label to `appdata`. Run a read-only consistency check of the XFS filesystem on `/dev/sdb2`, then relabel it `archive`.

**Solution:**
```bash
sudo tune2fs -m 1 /dev/sdb1
sudo e2label /dev/sdb1 appdata

sudo umount /data2
sudo xfs_repair -n /dev/sdb2                     # -n = check only, no changes
sudo xfs_admin -L archive /dev/sdb2
sudo mount /data2                                # fstab uses UUID, so still works
```

**Verify:**
```bash
sudo tune2fs -l /dev/sdb1 | grep -E 'volume name|Reserved block count'
lsblk -o NAME,FSTYPE,LABEL /dev/sdb
```

### Task 34: Git basics in a repository

**Task:** In `~/infra`, initialise a repo on branch `main`, commit an `nginx.conf`, create branch `feature/tls`, commit a change there, merge it back into `main`, tag the result `v1.0`, and undo the last commit safely with a new commit.

**Solution:**
```bash
git config --global user.name "Rizwan Khalid"
git config --global user.email "rizwan@lab.local"
git config --global init.defaultBranch main

mkdir -p ~/infra && cd ~/infra && git init
echo "worker_processes auto;" > nginx.conf
git add nginx.conf && git commit -m "Add base nginx config"
git switch -c feature/tls
echo "# tls enabled" >> nginx.conf
git commit -am "Enable TLS"
git switch main
git merge --no-ff feature/tls -m "Merge feature/tls"
git tag -a v1.0 -m "First release"
git revert --no-edit -m 1 HEAD                   # HEAD is the merge commit
```

**Verify:**
```bash
git log --oneline --graph --all
git tag -n
git status -s
```

Note: HEAD is a merge commit, so `git revert -m 1 HEAD` is the form that works; plain `git revert HEAD` is for normal commits.

### Task 35: Git remotes over SSH

**Task:** On lfcs2, create a bare repository `/srv/git/infra.git`. From lfcs1, add it as `origin`, push `main` and tags, then clone it into `/tmp/infra-clone` and confirm the history matches.

**Solution:**
```bash
# lfcs2
sudo mkdir -p /srv/git && sudo chown "$USER": /srv/git
git init --bare /srv/git/infra.git

# lfcs1
cd ~/infra
git remote add origin youruser@lfcs2:/srv/git/infra.git
git push -u origin main --tags
git clone youruser@lfcs2:/srv/git/infra.git /tmp/infra-clone
```

**Verify:**
```bash
git -C ~/infra remote -v
git -C /tmp/infra-clone log --oneline -3
git -C ~/infra status -sb                         # "## main...origin/main"
```

### Task 36: Create a systemd service for a Node.js app

**Task:** Run `/opt/api/server.js` as system user `nodeapp` under systemd service `api`, with `NODE_ENV=production`, restart on failure after 3 s, started after the network is online and enabled at boot.

**Solution:**
```bash
sudo apt install -y nodejs
sudo useradd -r -s /usr/sbin/nologin -d /opt/api nodeapp
sudo mkdir -p /opt/api
echo "require('http').createServer((q,s)=>s.end('ok\n')).listen(4000);" \
  | sudo tee /opt/api/server.js
sudo chown -R nodeapp:nodeapp /opt/api

sudo tee /etc/systemd/system/api.service >/dev/null <<'EOF'
[Unit]
Description=Demo Node API
Wants=network-online.target
After=network-online.target

[Service]
User=nodeapp
Group=nodeapp
WorkingDirectory=/opt/api
Environment=NODE_ENV=production
ExecStart=/usr/bin/node /opt/api/server.js
Restart=on-failure
RestartSec=3

[Install]
WantedBy=multi-user.target
EOF
sudo systemctl daemon-reload
sudo systemctl enable --now api
```

**Verify:**
```bash
systemctl status api --no-pager
curl -s localhost:4000
sudo kill -9 "$(systemctl show -p MainPID --value api)"; sleep 4
systemctl show -p NRestarts api                   # increments after the crash
```

### Task 37: Constrain a service with a drop-in

**Task:** Without editing `api.service`, limit it to 256 MiB of memory, 50% of one CPU, 4096 open files and 64 tasks.

**Solution:**
```bash
sudo mkdir -p /etc/systemd/system/api.service.d
sudo tee /etc/systemd/system/api.service.d/limits.conf >/dev/null <<'EOF'
[Service]
MemoryMax=256M
CPUQuota=50%
LimitNOFILE=4096
TasksMax=64
EOF
sudo systemctl daemon-reload
sudo systemctl restart api
# interactive equivalent: sudo systemctl edit api
```

**Verify:**
```bash
systemctl show api -p MemoryMax -p CPUQuotaPerSecUSec -p LimitNOFILE -p TasksMax
systemctl cat api                                 # shows the drop-in
grep 'open files' /proc/$(systemctl show -p MainPID --value api)/limits
```

### Task 38: Determine a service's constraints and dependencies

**Task:** For the `api` service, report: its main PID and user, the ports it listens on, its number of open files versus its limit, its cgroup memory use, the shared libraries `node` needs, and which units it depends on.

**Solution:**
```bash
PID=$(systemctl show -p MainPID --value api)
ps -o pid,user,rss,cmd -p "$PID"
sudo ss -tlnp | grep "pid=$PID"
sudo ls /proc/"$PID"/fd | wc -l
grep 'open files' /proc/"$PID"/limits
systemctl show api -p MemoryCurrent -p MemoryMax
ldd /usr/bin/node | head
systemctl list-dependencies api --no-pager
```

**Verify:**
```bash
systemd-cgtop -1 -n 1 | grep api
sudo lsof -p "$PID" | head
```

### Task 39: Monitor system performance

**Task:** Record a quick health snapshot: load average, top CPU and memory consumers, memory pressure, CPU steal/iowait, errors logged this boot, and the slowest units at boot. Enable sysstat history collection.

**Solution:**
```bash
uptime
ps -eo pid,user,pcpu,pmem,comm --sort=-pcpu | head -6
ps -eo pid,user,pcpu,pmem,comm --sort=-pmem | head -6
free -h
vmstat 2 5                                       # r, si/so, wa, st
mpstat -P ALL 2 1
journalctl -p err -b --no-pager | tail -20
systemd-analyze blame | head

sudo sed -i 's/^ENABLED=.*/ENABLED="true"/' /etc/default/sysstat
sudo systemctl enable --now sysstat
```

**Verify:**
```bash
systemctl list-timers | grep sysstat
sar -u 1 3                                       # history appears after ~10 min
```

### Task 40: Troubleshoot a full disk

**Task:** `/` reports full. Find the largest directories and files, find space held by deleted-but-open files and release it, check inode usage, and cap the journal at 200 MiB.

**Solution:**
```bash
# setup: a deleted log still held open
sudo fallocate -l 500M /var/tmp/big.log
sudo sh -c 'tail -f /var/tmp/big.log >/dev/null &'
sudo rm /var/tmp/big.log

df -hT /
df -i /
sudo du -xh / --max-depth=1 2>/dev/null | sort -h | tail
sudo find / -xdev -type f -size +100M -exec ls -lh {} + 2>/dev/null
sudo lsof +L1                                    # deleted files still open
sudo pkill -f 'tail -f /var/tmp/big.log'          # or: truncate /proc/PID/fd/N

journalctl --disk-usage
sudo journalctl --vacuum-size=200M
sudo mkdir -p /etc/systemd/journald.conf.d
printf '[Journal]\nSystemMaxUse=200M\n' \
  | sudo tee /etc/systemd/journald.conf.d/size.conf
sudo systemctl restart systemd-journald
sudo apt clean
```

**Verify:**
```bash
df -h /
sudo lsof +L1 | grep big.log || echo "released"
journalctl --disk-usage
```

### Task 41: Create and inspect TLS certificates

**Task:** Create a 2048-bit RSA key and a self-signed certificate for `app.lab.local` (SAN including the IP 192.168.56.10) valid for 365 days. Also create a CSR from the same key. Show subject, SANs, and expiry, prove key and certificate match, and test whether it expires within 30 days.

**Solution:**
```bash
sudo openssl req -x509 -newkey rsa:2048 -nodes -days 365 \
  -keyout /etc/ssl/private/app.key -out /etc/ssl/certs/app.crt \
  -subj "/CN=app.lab.local" \
  -addext "subjectAltName=DNS:app.lab.local,IP:192.168.56.10"
sudo chmod 600 /etc/ssl/private/app.key

sudo openssl req -new -key /etc/ssl/private/app.key -out /tmp/app.csr \
  -subj "/CN=app.lab.local"
```

**Verify:**
```bash
openssl x509 -in /etc/ssl/certs/app.crt -noout -subject -dates -ext subjectAltName
openssl req -in /tmp/app.csr -noout -subject -verify
diff <(openssl x509 -in /etc/ssl/certs/app.crt -noout -pubkey) \
     <(sudo openssl pkey -in /etc/ssl/private/app.key -pubout) && echo "match"
openssl x509 -in /etc/ssl/certs/app.crt -noout -checkend 2592000 \
  && echo "valid > 30 days"
```

### Task 42: Deploy the certificate and trust it

**Task:** Serve `app.lab.local` over HTTPS on 443 with the Task 41 certificate, redirect HTTP to HTTPS, and add the certificate to the system trust store so `curl` accepts it without `-k`.

**Solution:**
```bash
sudo tee /etc/nginx/sites-available/app-tls >/dev/null <<'EOF'
server {
    listen 443 ssl;
    server_name app.lab.local;
    ssl_certificate     /etc/ssl/certs/app.crt;
    ssl_certificate_key /etc/ssl/private/app.key;
    location / { proxy_pass http://app_backend; }
}
server {
    listen 80;
    server_name app.lab.local;
    return 301 https://$host$request_uri;
}
EOF
sudo rm -f /etc/nginx/sites-enabled/app          # replace the port-80 vhost
sudo ln -sf /etc/nginx/sites-available/app-tls /etc/nginx/sites-enabled/
# app_backend upstream is defined in sites-available/app; move it to conf.d:
sudo sed -n '/^upstream/,/^}/p' /etc/nginx/sites-available/app \
  | sudo tee /etc/nginx/conf.d/upstream-app.conf
sudo nginx -t && sudo systemctl reload nginx
sudo ufw allow 443/tcp

sudo cp /etc/ssl/certs/app.crt /usr/local/share/ca-certificates/app-lab.crt
sudo update-ca-certificates
echo "127.0.0.1 app.lab.local" | sudo tee -a /etc/hosts
```

**Verify:**
```bash
curl -sI http://app.lab.local | grep -i location
curl -s https://app.lab.local/                   # no -k needed
openssl s_client -connect app.lab.local:443 -servername app.lab.local </dev/null \
  2>/dev/null | openssl x509 -noout -subject -enddate
```

### Task 43: Users, groups and sudo

**Task:** Create group `developers` (GID 3000). Create `dev1` and `dev2` with home directories, bash, and `developers` as a supplementary group. Force `dev1` to change password at next login and expire passwords every 90 days with 7 days warning. Let `developers` restart the `api` service via sudo without a password, and nothing else. Lock `dev2`. Create a shared directory `/srv/dev` where new files inherit the group.

**Solution:**
```bash
sudo groupadd -g 3000 developers
sudo useradd -m -s /bin/bash -G developers dev1
sudo useradd -m -s /bin/bash -G developers dev2
echo 'dev1:ChangeMe#2026' | sudo chpasswd
sudo chage -d 0 -M 90 -W 7 dev1
sudo usermod -L dev2                              # or: passwd -l dev2

echo '%developers ALL=(root) NOPASSWD: /usr/bin/systemctl restart api' \
  | sudo tee /etc/sudoers.d/developers
sudo chmod 440 /etc/sudoers.d/developers
sudo visudo -cf /etc/sudoers.d/developers

sudo mkdir -p /srv/dev
sudo chgrp developers /srv/dev
sudo chmod 2770 /srv/dev
```

**Verify:**
```bash
id dev1; getent group developers
sudo chage -l dev1
sudo passwd -S dev2                               # "L" = locked
sudo -l -U dev1
ls -ld /srv/dev                                   # drwxrws---
```

### Task 44: Shell environment, per-user and system-wide

**Task:** For all users' login shells set `APP_ENV=lab` and add `/opt/tools/bin` to PATH. New users must get an alias `ll='ls -alF --color=auto'` and `EDITOR=vim`. For `dev1` only, set `HISTSIZE=5000`. Set `COMPANY=acme` for every PAM session, including non-shell ones.

**Solution:**
```bash
sudo tee /etc/profile.d/lab.sh >/dev/null <<'EOF'
export APP_ENV=lab
case ":$PATH:" in *":/opt/tools/bin:"*) ;; *) PATH="$PATH:/opt/tools/bin" ;; esac
export PATH
EOF

printf "alias ll='ls -alF --color=auto'\nexport EDITOR=vim\n" \
  | sudo tee -a /etc/skel/.bashrc

echo 'HISTSIZE=5000' | sudo tee -a /home/dev1/.bashrc
echo 'COMPANY=acme' | sudo tee -a /etc/environment   # KEY=value, read by pam_env
```

**Verify:**
```bash
sudo useradd -m -s /bin/bash dev3
sudo -iu dev3 bash -ic 'alias ll; echo $EDITOR $APP_ENV $COMPANY; echo $PATH'
sudo -iu dev1 bash -ic 'echo $HISTSIZE'
```

Remember: `/etc/profile.d` is read by login shells; `~/.bashrc` by interactive shells (Ubuntu's `~/.profile` sources it); `/etc/skel` only affects users created afterwards.

### Task 45: Per-user resource limits

**Task:** Members of `developers` get a soft limit of 200 processes and a hard limit of 300. `dev1` gets 4096 soft and 8192 hard open files.

**Solution:**
```bash
sudo tee /etc/security/limits.d/90-developers.conf >/dev/null <<'EOF'
@developers  soft  nproc   200
@developers  hard  nproc   300
dev1         soft  nofile  4096
dev1         hard  nofile  8192
EOF
```

**Verify:**
```bash
sudo -iu dev1 bash -c 'ulimit -Su; ulimit -Hu; ulimit -Sn; ulimit -Hn'
ssh dev1@localhost 'ulimit -u'                    # if dev1 has a key or password
```

Trap: limits are applied by `pam_limits` at session start (ssh, login, sudo). On Ubuntu, `su` does not load it unless you uncomment the `pam_limits.so` line in `/etc/pam.d/su`. Services ignore limits.conf; use `LimitNPROC=` / `LimitNOFILE=` in the unit (Task 37).

### Task 46: POSIX ACLs

**Task:** On `/srv/project` (owned by root, mode 750), give `dev2` read-write access and the `developers` group read-only access, including to all files created there in future. Then remove `dev2`'s access.

**Solution:**
```bash
sudo mkdir -p /srv/project && sudo chmod 750 /srv/project
sudo setfacl -m u:dev2:rwx /srv/project
sudo setfacl -m g:developers:rx /srv/project
sudo setfacl -d -m u:dev2:rwx /srv/project        # default ACL for new files
sudo setfacl -d -m g:developers:rx /srv/project
sudo touch /srv/project/notes.txt

sudo setfacl -x u:dev2 /srv/project               # remove later
sudo setfacl -d -x u:dev2 /srv/project
```

**Verify:**
```bash
getfacl /srv/project
getfacl /srv/project/notes.txt                     # inherited entries + mask
ls -ld /srv/project                                # trailing "+" = ACL present
```

### Task 47: LDAP accounts via SSSD

**Task:** On lfcs2, run an OpenLDAP server for `dc=lab,dc=local` containing POSIX user `alice` (UID 5001) in group `devs` (GID 5000). On lfcs1, configure SSSD so `alice` resolves and can log in, with her home created on first login.

**Solution:**
```bash
# lfcs2: server
sudo apt install -y slapd ldap-utils             # set an admin password
sudo dpkg-reconfigure slapd                      # DNS domain: lab.local, org: lab
slappasswd -s 'Alice#2026'                       # copy the {SSHA} hash
cat > /tmp/users.ldif <<'EOF'
dn: ou=people,dc=lab,dc=local
objectClass: organizationalUnit
ou: people

dn: ou=groups,dc=lab,dc=local
objectClass: organizationalUnit
ou: groups

dn: cn=devs,ou=groups,dc=lab,dc=local
objectClass: posixGroup
cn: devs
gidNumber: 5000
memberUid: alice

dn: uid=alice,ou=people,dc=lab,dc=local
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: alice
cn: Alice Lab
sn: Lab
uidNumber: 5001
gidNumber: 5000
homeDirectory: /home/alice
loginShell: /bin/bash
userPassword: {SSHA}PASTE_HASH_HERE
EOF
ldapadd -x -D cn=admin,dc=lab,dc=local -W -f /tmp/users.ldif
sudo ufw allow from 192.168.56.0/24 to any port 389 proto tcp

# lfcs1: client
sudo apt install -y sssd-ldap ldap-utils libnss-sss libpam-sss
sudo tee /etc/sssd/sssd.conf >/dev/null <<'EOF'
[sssd]
services = nss, pam
domains = lab

[domain/lab]
id_provider = ldap
auth_provider = ldap
ldap_uri = ldap://192.168.56.11
ldap_search_base = dc=lab,dc=local
ldap_id_use_start_tls = false
ldap_auth_disable_tls_never_use_in_production = true
cache_credentials = true
EOF
sudo chmod 600 /etc/sssd/sssd.conf               # sssd refuses other modes
sudo systemctl restart sssd
sudo pam-auth-update --enable mkhomedir
```

**Verify:**
```bash
ldapsearch -x -H ldap://192.168.56.11 -b dc=lab,dc=local uid=alice uidNumber
getent passwd alice; id alice
grep -E '^(passwd|group):' /etc/nsswitch.conf     # should include sss
su - alice -c 'pwd; id'                          # /home/alice created
```

The no-TLS options are for the lab only. In production use `ldaps://` or StartTLS with `ldap_tls_cacert`.

## Practice questions

1. Which single command loads every file under `/etc/sysctl.d/` into the running kernel?
2. You are editing netplan over SSH. Which command applies the change but rolls it back automatically if you do not confirm?
3. On Ubuntu 24.04 you added `Port 2222` to an sshd drop-in and ran `systemctl restart ssh`, but nothing listens on 2222. Why, and what fixes it?
4. Which command shows the DNS servers and search domains systemd-resolved uses for each interface?
5. How do you stop `apt upgrade` from upgrading the `nginx` package, and how do you list such packages?
6. What is the difference between `dpkg -S /usr/bin/dig` and `apt-file search bin/dig`?
7. Multiple choice. Which rule allows SSH only from 10.0.0.0/8? (a) `ufw allow 22/tcp from 10.0.0.0/8` (b) `ufw allow from 10.0.0.0/8 to any port 22 proto tcp` (c) `ufw permit ssh 10.0.0.0/8` (d) `ufw route allow 22 10.0.0.0/8`
8. ufw denies all incoming traffic, yet a container started with `docker run -p 8080:80` is reachable from other hosts. Why? Name one fix.
9. You redirected port 80 to 3000 in the PREROUTING chain. Remote clients work, but `curl localhost:80` on the same host fails. Why?
10. What one command grows `/dev/vg_app/lv_web` by 2 GiB and resizes its filesystem too?
11. True or false: an XFS filesystem can be shrunk with `lvreduce -r`.
12. Which two fstab options should an NFS mount have so that boot is not blocked when the server is down?
13. Two swap areas have priorities 5 and 10. Which one is used first?
14. In the autofs map line `* -rw lfcs2:/home/&`, what do `*` and `&` mean?
15. `df` reports `/var` 100% full, but `du -sh /var` shows far less. What is the likely cause and which command confirms it?
16. `df -h` shows free space but writes fail with "No space left on device". What do you check next?
17. Explain soft versus hard limits in `/etc/security/limits.conf`.
18. A file has the ACL entry `user:bob:rw-`. You run `chmod g=r file`. What are bob's effective permissions now, and why?
19. What is wrong with the line `export COMPANY=acme` in `/etc/environment`?
20. You want every user created from now on to have an alias. Which file do you edit?
21. Which command puts the AppArmor profile for `/usr/local/bin/report.sh` into complain mode, and where do denials appear?
22. On an RHEL-family host, files copied to a custom web root have the wrong SELinux type after a relabel. Which two commands give a permanent fix?
23. What does `Persistent=true` do in a systemd `.timer` unit?
24. What does the cron schedule `*/15 9-17 * * 1-5` mean?
25. Which `virsh` commands make VM `vm1` start at host boot and set its maximum memory to 2 GiB for the next boot?
26. Which Docker restart policy restarts a container after a daemon or host restart, but not after you stopped it by hand?
27. What load-balancing method does an Nginx `upstream` use by default, and which directive changes it to fewest active connections?
28. Which OpenSSL command exits non-zero if a certificate expires within 7 days?
29. You pushed a bad commit to a shared branch. What is the safe way to undo it?
30. Write the netplan fragment that adds a persistent route to 10.20.0.0/16 via 192.168.56.1.
31. Which bonding mode gives failover without any switch configuration?
32. `timedatectl` shows "System clock synchronized: no". Name three things to check.
33. Which command shows which process is listening on TCP port 8080?
34. An Ubuntu server hangs in boot because of a bad fstab entry, and the emergency shell says the root account is locked. How do you get a root shell?
35. `ldapsearch` finds `alice`, but `getent passwd alice` returns nothing on the SSSD client. Name three likely causes.
36. A service must be allowed 65536 open files. Why does adding it to `/etc/security/limits.conf` not work, and what does?

### Answers

1. `sudo sysctl --system`. It reads `/etc/sysctl.d/*.conf`, `/run/sysctl.d`, `/usr/lib/sysctl.d` and `/etc/sysctl.conf` in order.
2. `sudo netplan try`. It reverts after 120 seconds unless you press Enter.
3. Ubuntu 24.04 starts sshd through `ssh.socket`; ports come from a generator. Run `systemctl daemon-reload` then `systemctl restart ssh.socket`.
4. `resolvectl status` (or `resolvectl dns` and `resolvectl domain`).
5. `sudo apt-mark hold nginx`; list with `apt-mark showhold`, undo with `apt-mark unhold`.
6. `dpkg -S` searches only installed packages; `apt-file` searches the repository file lists, so it finds packages you have not installed.
7. (b). ufw syntax is `allow from SRC to any port N proto tcp`.
8. Docker adds its own iptables NAT and FORWARD rules, which are evaluated before ufw's input rules. Publish on `127.0.0.1:` or add rules to the `DOCKER-USER` chain.
9. Locally generated packets do not pass PREROUTING. You need a matching rule in the nat OUTPUT chain.
10. `sudo lvextend -r -L +2G /dev/vg_app/lv_web`. `-r` calls `fsadm` to resize ext4 or XFS.
11. False. XFS can only grow; back up, recreate and restore to shrink.
12. `_netdev` (wait for the network) and `nofail` (do not fail boot); `x-systemd.automount` also helps.
13. Priority 10. Higher priority swap is used first; equal priorities are striped.
14. `*` matches any key looked up under the mount point; `&` is replaced by that key, so `/home/bob` mounts `lfcs2:/home/bob`.
15. A process still holds a deleted file open. `sudo lsof +L1` lists them; restart the process or truncate via `/proc/PID/fd/N`.
16. Inodes: `df -i`. Many tiny files (sessions, cache) can exhaust inodes while blocks remain free.
17. The soft limit is the enforced default a user can raise up to the hard limit; the hard limit is the ceiling only root can raise.
18. `r--`. With ACLs, the group permission bits become the ACL mask, which caps named-user and group entries.
19. `/etc/environment` is read by `pam_env`, not by a shell. Use plain `KEY=value` lines with no `export`.
20. `/etc/skel/.bashrc` (skeleton files are copied at `useradd -m` time only).
21. `sudo aa-complain /usr/local/bin/report.sh`. Denials and complain-mode events go to the kernel log (`journalctl -k`), or `/var/log/audit/audit.log` if auditd runs.
22. `semanage fcontext -a -t httpd_sys_content_t "/srv/web(/.*)?"` then `restorecon -Rv /srv/web`.
23. It stores the last run time on disk and runs a missed job once at next boot if the system was off when it was due.
24. Every 15 minutes from 09:00 to 17:45, Monday to Friday.
25. `virsh autostart vm1` and `virsh setmaxmem vm1 2G --config` (plus `virsh setmem ... --config` if needed).
26. `unless-stopped`. `always` would also restart a container you had stopped once the daemon restarts.
27. Round robin by default; `least_conn;` inside the `upstream` block.
28. `openssl x509 -in cert.crt -noout -checkend 604800` (seconds).
29. `git revert <commit>` creates a new commit that undoes it, so shared history is not rewritten.
30. Under the interface: `routes:` then a list item `- to: 10.20.0.0/16` with `via: 192.168.56.1`, then `netplan apply`.
31. `active-backup` (mode 1).
32. That NTP is on (`timedatectl set-ntp true`), that `systemd-timesyncd` or `chronyd` is running (`timedatectl timesync-status`, `chronyc sources`), and that UDP 123 and DNS for the NTP host work.
33. `sudo ss -tlnp 'sport = :8080'` (or `sudo lsof -i :8080`).
34. Edit the GRUB entry, append `init=/bin/bash`, boot, `mount -o remount,rw /`, fix `/etc/fstab`, then `sync` and `reboot -f`.
35. `sssd.conf` not mode 0600 (sssd will not start), sssd not running or wrong `ldap_search_base`, or `/etc/nsswitch.conf` missing `sss`; clear stale cache with `sss_cache -E`.
36. limits.conf is applied by PAM at login sessions; systemd services do not use PAM. Set `LimitNOFILE=65536` in a unit drop-in and restart.

## Exam-day tips

Delivery rules (official):
- Remote exam through the PSI Bridge secure browser. Run the system check well before the day.
- Bring a valid, unexpired, government-issued photo ID (passport or national ID card). The first and last name must exactly match the name on your exam checklist.
- Test alone in a private, quiet, well-lit room with a clear desk: no phone, smartwatch, notes or second screen. Only clear liquids.
- You stay on camera and talk only to the proctor.
- Allowed help inside the exam: man pages, docs under `/usr/share/doc`, and distribution packages. No web browsing.
- Results arrive by email within 24 hours. A No Pass unlocks your free retake in the portal.

Environment habits (from the official LFCS instructions):
- Each task names a host. SSH to it from the base system, and exit back to base before the next task. Nested SSH (host to host) is not supported.
- Never reboot the base system. Rebooting a task node is fine when needed.
- Use `sudo -i` for root. Vim, nano and emacs are available.
- Terminal copy/paste is usually Ctrl+Shift+C / Ctrl+Shift+V; re-read the instructions page just before the exam.

Time management:
- 17-20 tasks in 120 minutes is about 6 minutes each. Read all tasks first; do the quick, high-value ones first.
- Flag and skip anything that eats more than 10 minutes; come back once the easy points are banked.
- Leave 10 minutes at the end to re-check persistence on the tasks you flagged.

Common traps:
- Runtime-only fixes. Most tasks are graded after a reboot or re-check: use fstab, netplan, sysctl.d, `systemctl enable`, `ufw` (not raw iptables), `crontab`.
- Wrong host. Check `hostname` before every change.
- netplan YAML indentation and file mode 600; always `netplan generate` or `netplan try` first.
- `ssh.socket` on 24.04 (Task 16) and sshd first-match rules in `sshd_config.d`.
- Enabling ufw before allowing SSH on a remote host.
- Forgetting `daemon-reload` after editing units or fstab.
- `usermod -G` without `-a` wipes existing supplementary groups.
- Mounting by `/dev/sdX` when the task says UUID or label.
- Exact names and paths: graders check them literally.
- Search man pages fast: `man -k keyword`, `/pattern` inside man, and `EXAMPLES` sections (`man 5 crontab`, `man systemd.timer`, `man 5 exports`, `man netplan`).

## Readiness checklist

- [ ] Lab built: two Ubuntu 24.04 VMs, spare disks, extra NICs, clean snapshots
- [ ] I can set sysctl values at runtime and persistently without looking anything up
- [ ] I can diagnose a failed service with `systemctl status`, `journalctl -u` and a config test
- [ ] I can write a cron entry, an `/etc/cron.d` file and a systemd timer from memory
- [ ] I can hold, query, verify packages and add a repo with a keyring and `.sources` file
- [ ] I can recover a system with a broken fstab using `init=/bin/bash`
- [ ] I can create, start, autostart and resize a libvirt VM with `virt-install` and `virsh`
- [ ] I can run, publish, persist and build Docker containers
- [ ] I can write, load and switch modes of an AppArmor profile; I know the SELinux basics
- [ ] I can configure static IPv4/IPv6, DNS and routes with netplan and `netplan try`
- [ ] I can set hostname, `/etc/hosts`, resolved settings, time zone and NTP (timesyncd, chrony)
- [ ] I can harden sshd on 24.04 and set up client keys and `~/.ssh/config`
- [ ] I can write ufw rules, and port redirection and masquerade in `before.rules`
- [ ] I can build a bond and a bridge with netplan and prove failover
- [ ] I can configure Nginx as a reverse proxy and load balancer, with TLS
- [ ] I can partition, format and mount by UUID; check and repair ext4 and XFS
- [ ] I can create, extend and add PVs to LVM, and grow the Ubuntu root LV
- [ ] I can add swap files and swap LVs with priorities
- [ ] I can set up NFS server and client, NBD, autofs and systemd automount
- [ ] I can find I/O bottlenecks with `iostat`, `pidstat` and `iotop`
- [ ] I can use Git: branch, merge, tag, revert, push to a bare remote
- [ ] I can write a systemd unit with restart policy and resource limits in a drop-in
- [ ] I can find and free disk space, including deleted-open files and inodes
- [ ] I can create, inspect, match and deploy certificates, and trust a CA
- [ ] I can manage users, groups, password aging, sudoers drop-ins and setgid dirs
- [ ] I can set environment variables in the right file for each scope
- [ ] I can set limits for users (limits.d) and for services (unit `Limit*=`)
- [ ] I can set and remove access and default ACLs and explain the mask
- [ ] I can configure an SSSD LDAP client and verify with `getent` and `id`
- [ ] I completed all 47 tasks at least twice, the second time without notes
- [ ] killer.sh session 1 done, gaps fixed; session 2 scored comfortably above 67%
- [ ] ID checked against my exam checklist name; PSI system check passed; room ready

## Sources

- LFCS certification page (price, duration, format, domains, validity, retake, simulator): https://training.linuxfoundation.org/certification/linux-foundation-certified-sysadmin-lfcs/
- LFCS exam update announcement (effective 11 May 2023, domain weights, distribution-independent): https://training.linuxfoundation.org/blog/updated-linux-foundation-certified-system-administrator-lfcs-exam/
- Important Instructions: LFCS (17-20 tasks, 67% pass mark, allowed resources, SSH and reboot rules): https://docs.linuxfoundation.org/tc-docs/certification/instructions-lfcs-and-lfce
- Certification exam retake policy: https://training.linuxfoundation.org/about/policies-2-2026/certification-exam-retake-policy/
- Certification FAQ (renewal, results timing): https://training.linuxfoundation.org/about/faqs/certification-faq/
- Candidate handbook, exam rules and policies: https://docs.linuxfoundation.org/tc-docs/certification/lf-handbook2/exam-rules-and-policies
- Candidate handbook, identification and authentication: https://docs.linuxfoundation.org/tc-docs/certification/lf-handbook2/candidate-identification-and-authentication
- Candidate handbook, exam scoring and notification: https://docs.linuxfoundation.org/tc-docs/certification/lf-handbook2/exam-scoring-and-notification
- Candidate handbook, repurchasing the exam: https://docs.linuxfoundation.org/tc-docs/certification/lf-handbook2/repurchasing-the-exam
- killer.sh LFCS simulator: https://killer.sh/lfcs
- Ubuntu Server documentation: https://documentation.ubuntu.com/server/
- Netplan documentation: https://netplan.readthedocs.io/
- Ubuntu Server download: https://ubuntu.com/download/server
- Unverified: the exact Ubuntu release used in the live exam environment (official pages say only that the exam is distribution-independent).
