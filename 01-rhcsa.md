# Chapter 1: Red Hat RHCSA (EX200)

This guide prepares you; you sit the exam and every assessment yourself.

As of September 2026.

**Version alert:** this chapter follows RHEL 9 conventions, as requested. But the official EX200 page now says the exam is **based on RHEL 10**. Its current objective list adds Flatpak and systemd timers and no longer lists containers. Whether a RHEL 9 version of EX200 can still be booked is **unverified**. Check the version on the booking screen before you pay. Almost every command below works the same on RHEL 9 and RHEL 10. Tasks that apply to only one version are labelled.

## At a glance

| Fact | Detail |
|---|---|
| Credential | Red Hat Certified System Administrator (RHCSA) |
| Exam code | EX200 |
| Current exam version | Based on RHEL 10 (official page, Sept 2026) |
| RHEL 9 version still bookable | Unverified - confirm at scheduling |
| Format | 100% hands-on tasks on live systems; no multiple choice |
| Duration | 3 hours (unverified - third-party sources) |
| Price | About US$500 list; varies by region (unverified) |
| Passing score | 210 of 300 (unverified - community-reported) |
| Delivery | Remote exam (from home) or Red Hat testing station |
| Remote kit | Gov photo ID, bootable Live USB, external webcam, mic |
| Allowed resources | Docs on the exam system only (man, /usr/share/doc) |
| Not allowed | Internet, notes, books, own documentation |
| Results | By email within 5 business days; per-area breakdown |
| Retake | One free retake per paid first attempt |
| Validity | Current for 3 years from the date earned |
| Prerequisite | None required; RH124 + RH134 or RH199 suggested |

Why it fits you: you already run Linux in production, so the RHCSA builds on skills you have instead of starting from zero. The main work is learning the RHEL-specific tools you rarely touch on Ubuntu (SELinux, LVM, firewalld, nmcli, autofs, tuned). It is also the prerequisite for RHCE (Ansible), which fits naturally with the deployment automation you already do.

## Objectives map

The areas below follow the official EX200 objective list, reworded. The last row applies only if you get the RHEL 9 version of the exam.

| Objective area | What you must be able to do | Your strength |
|---|---|---|
| Essential tools | Shell, redirection, grep/regex, ssh, su | Strong |
| Essential tools (files) | tar/gzip/bzip2, links, ugo/rwx, man/info | Strong |
| Manage software | Configure dnf repos; install/remove RPMs | Refresh |
| Manage software (Flatpak) | Add Flatpak remotes; install/remove apps | New |
| Simple shell scripts | if/test/[ ], for loops, args, command output | Strong |
| Operate running systems | Boot, reboot, targets, interrupt boot | New |
| Operate running systems | Kill/renice processes, tuned profiles | Refresh |
| Operate running systems | journalctl, persistent journal, scp/sftp | Refresh |
| Configure local storage | GPT partitions, PV/VG/LV, swap, UUID/label | New |
| Create file systems | vfat/ext4/xfs, NFS, autofs, grow LVs | New |
| File system permissions | Diagnose and fix permission problems | Refresh |
| Deploy and maintain | at, cron, systemd timers, services | Refresh |
| Deploy and maintain | Default target, chrony, dnf, GRUB changes | New |
| Basic networking | IPv4/IPv6 with nmcli, hostname, resolution | Refresh |
| Basic networking | Restrict access with firewalld | New |
| Users and groups | Users, groups, password aging, sudo | Refresh |
| Security | umask, SSH keys, firewalld | Refresh |
| Security (SELinux) | Modes, contexts, port labels, booleans | New |
| Containers (RHEL 9 only) | podman images, rootless, systemd, storage | Refresh |

## Study plan

Ten weeks at 5 to 8 hours a week. Each week, do the tasks for that area in the lab twice: once while reading, and once from memory a few days later.

| Week | Focus | Tasks | Resources |
|---|---|---|---|
| 1 | Build lab, snapshots, local repo | Lab setup | Rocky/Alma docs, Hyper-V docs |
| 2 | Essential tools, docs, scripts | 1-6, 10-11 | man pages, RHEL 9 docs (free) |
| 3 | Software, Flatpak, users, sudo | 7-9, 36-39 | RHEL 9 "Managing software" docs |
| 4 | Boot targets, root reset, processes | 12-18 | RHEL 9 "Configuring basic sysadmin" |
| 5 | Partitions, LVM, swap | 19-25 | RHEL 9 "Managing storage devices" |
| 6 | File systems, NFS, autofs | 26-30 | RHEL 9 "Managing file systems" |
| 7 | Scheduling, chrony, GRUB, networking | 31-35, 40-42 | RHEL 9 networking docs |
| 8 | SELinux, firewalld, SSH, umask | 43-48 | RHEL 9 "Using SELinux" docs |
| 9 | Containers (if RHEL 9 exam) + weak areas | 49-50 | RHEL 9 "Building containers" docs |
| 10 | Two timed 3-hour mock runs + review | All | Your own task list; practice Qs |

Resources:
- Free: the RHEL 9 product documentation at https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9 (use the RHEL 10 docs if you book the RHEL 10 exam).
- Free: the man pages and `/usr/share/doc` on your lab VM. These are the only resources you get in the exam, so practise using them.
- Free: Rocky Linux or AlmaLinux 9 ISOs (compatible rebuilds of RHEL, no account needed).
- Official (paid): RH124 and RH134, or the RH199 rapid-track course. You don't need these, given your background.
- Optional: the Red Hat Developer subscription gives a free RHEL licence, but it needs an account. That is your choice to make; the Rocky/Alma lab works without one.

## Lab setup

You're on Windows 11 Pro, so Hyper-V is free and built in. WSL2 is not suitable: it has no GRUB, no boot targets and no real block devices, so you couldn't practise the root reset, LVM or fstab. Build two VMs:

- **server** (192.168.50.1): serves a dnf repo, an NFS export and NTP. You don't need to be careful with this one.
- **client** (192.168.50.10): the "exam box". Has two extra blank disks. Take a snapshot when it's clean and roll back to it often.

Step 1: enable Hyper-V (in an admin PowerShell, then reboot).

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```

Step 2: download the Rocky Linux 9 DVD ISO (https://rockylinux.org/download) or AlmaLinux 9 (https://almalinux.org/get-almalinux/) to `C:\ISO\`.

Step 3: create a private lab switch and both VMs (admin PowerShell).

```powershell
New-VMSwitch -Name LabNet -SwitchType Internal
$iso = "C:\ISO\Rocky-9-latest-x86_64-dvd.iso"
foreach ($n in "server","client") {
  New-VM -Name $n -MemoryStartupBytes 2GB -Generation 2 `
    -NewVHDPath "C:\VMs\$n.vhdx" -NewVHDSizeBytes 20GB -SwitchName "Default Switch"
  Set-VMProcessor -VMName $n -Count 2
  Set-VMFirmware -VMName $n -SecureBootTemplate MicrosoftUEFICertificateAuthority
  Add-VMNetworkAdapter -VMName $n -SwitchName LabNet
  Add-VMDvdDrive -VMName $n -Path $iso
  Set-VMFirmware -VMName $n -FirstBootDevice (Get-VMDvdDrive -VMName $n)
}
New-VHD -Path C:\VMs\client-d1.vhdx -SizeBytes 5GB -Dynamic
New-VHD -Path C:\VMs\client-d2.vhdx -SizeBytes 5GB -Dynamic
Add-VMHardDiskDrive -VMName client -Path C:\VMs\client-d1.vhdx
Add-VMHardDiskDrive -VMName client -Path C:\VMs\client-d2.vhdx
Start-VM server, client
```

Step 4: install both VMs as "Server with GUI" or "Minimal Install", and set a root password. After installing, remove the DVD from the boot order (keep the ISO attached to **server** for the repo), then take a snapshot:

```powershell
Checkpoint-VM -Name client -SnapshotName clean
# roll back later with:
Restore-VMSnapshot -VMName client -Name clean -Confirm:$false
```

Step 5: on **server**, give the LabNet NIC a static address and publish the DVD as a repo over HTTP. Run `nmcli dev` to find the name of the second NIC (for example `eth1`).

```bash
nmcli con add con-name labnet ifname eth1 type ethernet \
  ipv4.method manual ipv4.addresses 192.168.50.1/24
nmcli con up labnet
mkdir -p /var/www/html/repo
echo '/dev/sr0 /var/www/html/repo iso9660 ro,nofail 0 0' >> /etc/fstab
systemctl daemon-reload && mount -a
dnf install -y httpd nfs-utils chrony
systemctl enable --now httpd
firewall-cmd --permanent --add-service={http,nfs,rpc-bind,mountd,ntp}
firewall-cmd --reload
```

Step 6: on **server**, create NFS exports for the NFS and autofs tasks.

```bash
mkdir -p /export/share /rhome/{alice,bob}
echo "hello from nfs" > /export/share/readme.txt
useradd -u 3001 alice; useradd -u 3002 bob
chown alice: /rhome/alice; chown bob: /rhome/bob
cat > /etc/exports <<'EOF'
/export/share 192.168.50.0/24(rw,sync)
/rhome        192.168.50.0/24(rw,sync)
EOF
systemctl enable --now nfs-server
exportfs -rv
```

Step 7: on **server**, turn it into an NTP source for the lab.

```bash
echo 'allow 192.168.50.0/24' >> /etc/chrony.conf
echo 'local stratum 8' >> /etc/chrony.conf
systemctl restart chronyd
```

Step 8: on **client**, disable the installer's DVD repos by adding `enabled=0` to the Rocky repo files in `/etc/yum.repos.d/`. Then configure the lab repos yourself (Task 7). That matches the exam, where you're usually given repo URLs.

Disk names: Hyper-V shows extra disks as `/dev/sdb` and `/dev/sdc`. The exam usually uses `/dev/vdb` (KVM). The tasks below use `/dev/vdb` and `/dev/vdc`, so substitute your own names (check with `lsblk`).

## Hands-on tasks

Do these tasks as root on **client** unless a task says otherwise. The exam requires that every change **survives a reboot**, so reboot and re-verify after each block of tasks.

### Task 1: Find files by owner and copy them

**Task:** Find all regular files owned by user `alice` anywhere on the system and copy them, keeping their directory structure and attributes, into `/root/alice-files`.

**Solution:**
```bash
useradd alice 2>/dev/null; touch /tmp/a1; chown alice /tmp/a1
mkdir -p /root/alice-files
find / -user alice -type f -not -path '/proc/*' \
  -exec cp -a --parents {} /root/alice-files/ \; 2>/dev/null
```

**Verify:**
```bash
find /root/alice-files -type f
ls -l /root/alice-files/tmp/a1
```

### Task 2: grep with regular expressions and redirection

**Task:** Write every line of `/etc/passwd` that belongs to a user with a 4-digit UID to `/root/uid4.txt`. Put every non-comment, non-blank line of `/etc/ssh/sshd_config` into `/root/sshd-active.txt`.

**Solution:**
```bash
grep -E '^[^:]+:[^:]*:[0-9]{4}:' /etc/passwd > /root/uid4.txt
grep -Ev '^[[:space:]]*(#|$)' /etc/ssh/sshd_config > /root/sshd-active.txt
```

**Verify:**
```bash
cat /root/uid4.txt
grep -c '^#' /root/sshd-active.txt   # expect 0
```

### Task 3: Create compressed archives

**Task:** Create a gzip archive of `/etc` at `/root/etc.tar.gz` and a bzip2 archive at `/root/etc.tar.bz2`. Extract `etc/hosts` from the bzip2 archive into `/tmp/restore`.

**Solution:**
```bash
tar -czf /root/etc.tar.gz /etc
tar -cjf /root/etc.tar.bz2 /etc
mkdir -p /tmp/restore
tar -xjf /root/etc.tar.bz2 -C /tmp/restore etc/hosts
```

**Verify:**
```bash
file /root/etc.tar.gz /root/etc.tar.bz2
tar -tjf /root/etc.tar.bz2 | head
diff /etc/hosts /tmp/restore/etc/hosts && echo same
```

### Task 4: Hard and soft links

**Task:** Create `/data/report.txt`, a hard link to it at `/data/report.hard`, and a symbolic link to it at `/root/report.link`.

**Solution:**
```bash
mkdir -p /data && echo "q3 numbers" > /data/report.txt
ln /data/report.txt /data/report.hard
ln -s /data/report.txt /root/report.link
```

**Verify:**
```bash
ls -li /data/report.txt /data/report.hard   # same inode, link count 2
ls -l /root/report.link                     # -> /data/report.txt
cat /root/report.link
```

### Task 5: Standard permissions and ownership

**Task:** Create `/data/secret.txt`, owned by `alice` and group `wheel`. The owner can read and write it, the group can read it, and nobody else has any access.

**Solution:**
```bash
touch /data/secret.txt
chown alice:wheel /data/secret.txt
chmod 640 /data/secret.txt      # or: chmod u=rw,g=r,o= /data/secret.txt
```

**Verify:**
```bash
stat -c '%A %U %G %n' /data/secret.txt   # -rw-r----- alice wheel
```

### Task 6: Find answers in the system documentation

**Task:** Without using the internet, find the man page that documents the `/etc/fstab` format, the config file example for `autofs`, and every man page related to `semanage`.

**Solution:**
```bash
man 5 fstab
ls /usr/share/doc/ | grep -i autofs; man 5 auto.master
man -k semanage          # if empty, rebuild the index: mandb
```

**Verify:**
```bash
whatis fstab
man -k semanage | head
```

### Task 7: Configure dnf repositories

**Task:** Configure the system to use the repositories at `http://192.168.50.1/repo/BaseOS` and `http://192.168.50.1/repo/AppStream`, with GPG checking disabled.

**Solution:**
```bash
cat > /etc/yum.repos.d/lab.repo <<'EOF'
[lab-baseos]
name=Lab BaseOS
baseurl=http://192.168.50.1/repo/BaseOS
enabled=1
gpgcheck=0

[lab-appstream]
name=Lab AppStream
baseurl=http://192.168.50.1/repo/AppStream
enabled=1
gpgcheck=0
EOF
dnf clean all
```

Alternative: run `dnf config-manager --add-repo http://192.168.50.1/repo/BaseOS` (from dnf-plugins-core), then add `gpgcheck=0` to the file it generates.

**Verify:**
```bash
dnf repolist
dnf list available | head
```

### Task 8: Install, query and remove packages

**Task:** Install the package that provides the `semanage` command and the `autofs` package. Remove `nano` if it is installed. Find out which package owns `/etc/chrony.conf`.

**Solution:**
```bash
dnf provides '*/semanage'          # policycoreutils-python-utils
dnf install -y policycoreutils-python-utils autofs
dnf remove -y nano
rpm -qf /etc/chrony.conf
```

**Verify:**
```bash
rpm -q policycoreutils-python-utils autofs
rpm -q nano        # "package nano is not installed"
dnf history | head -5
```

### Task 9: Configure a Flatpak remote and install an app (RHEL 10 objective)

**Task:** Add the Flathub remote system-wide, install `org.gnome.Calculator` from it, then remove it. In the exam you'll be given the remote URL to use instead.

**Solution:**
```bash
dnf install -y flatpak
flatpak remote-add --if-not-exists flathub \
  https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak install -y flathub org.gnome.Calculator
flatpak uninstall -y org.gnome.Calculator
```

**Verify:**
```bash
flatpak remotes --show-details
flatpak list --app     # empty after the uninstall
```

### Task 10: Script with arguments, conditions and a loop

**Task:** Write `/usr/local/bin/mkusers`, which takes one argument: a file with one username per line. For each name it creates the user if the user doesn't exist, and otherwise prints `exists: NAME`. If the argument is missing or the file can't be read, it prints a usage message to stderr and exits with status 1.

**Solution:**
```bash
cat > /usr/local/bin/mkusers <<'EOF'
#!/bin/bash
if [ $# -ne 1 ] || [ ! -r "$1" ]; then
  echo "Usage: $0 USERFILE" >&2
  exit 1
fi
for u in $(cat "$1"); do
  if id "$u" &>/dev/null; then
    echo "exists: $u"
  else
    useradd "$u" && echo "created: $u"
  fi
done
EOF
chmod 755 /usr/local/bin/mkusers
```

**Verify:**
```bash
printf 'tom\njerry\nroot\n' > /tmp/names
mkusers /tmp/names          # created tom, created jerry, exists: root
mkusers; echo "rc=$?"       # usage, rc=1
```

### Task 11: Script that processes command output

**Task:** Write `/usr/local/bin/bigfiles`, which lists every file larger than the size given as its first argument (for example `10M`) under `/var`, one per line, in the format `SIZE PATH`. Save its output for `5M` to `/root/big.txt`.

**Solution:**
```bash
cat > /usr/local/bin/bigfiles <<'EOF'
#!/bin/bash
limit=${1:-10M}
find /var -type f -size +"$limit" 2>/dev/null | while read -r f; do
  size=$(du -h "$f" | cut -f1)
  echo "$size $f"
done
EOF
chmod 755 /usr/local/bin/bigfiles
bigfiles 5M > /root/big.txt
```

**Verify:**
```bash
cat /root/big.txt
bash -n /usr/local/bin/bigfiles && echo "syntax ok"
```

### Task 12: Set and switch boot targets

**Task:** Make the system boot into the text-mode multi-user target by default. Switch to it now without rebooting.

**Solution:**
```bash
systemctl get-default
systemctl set-default multi-user.target
systemctl isolate multi-user.target
```

**Verify:**
```bash
systemctl get-default                 # multi-user.target
ls -l /etc/systemd/system/default.target
systemctl is-active graphical.target  # inactive
```

### Task 13: Reset a forgotten root password (interrupt the boot)

**Task:** You don't know the root password. Reset it to `Lab-Root-2026` using the console, and keep SELinux working.

**Solution:**
```text
1. Reboot. At the GRUB menu press an arrow key to stop the countdown.
   (If the menu is hidden, hold Shift or press Esc during boot.)
2. Highlight the default kernel entry and press e.
3. Go to the end of the line starting with "linux" and append:  rd.break
4. Press Ctrl+x to boot. You land in an emergency shell (switch_root:/#).
```
```bash
mount -o remount,rw /sysroot
chroot /sysroot
passwd root                 # type Lab-Root-2026 twice
touch /.autorelabel         # fixes the SELinux label on /etc/shadow
exit                        # leave the chroot
exit                        # continue booting; relabel then reboot happen
```

**Verify:**
```bash
# After the automatic relabel and reboot, log in as root with the new password.
ls -Z /etc/shadow          # system_u:object_r:shadow_t:s0
getenforce                 # Enforcing
```

### Task 14: Boot once into rescue or emergency target

**Task:** For one boot only, start the system in `rescue.target` from GRUB. Then return to normal operation.

**Solution:**
```text
At GRUB press e, append to the "linux" line:  systemd.unit=rescue.target
Press Ctrl+x, then enter the root password when asked.
(Use systemd.unit=emergency.target for an even more minimal shell,
 where / is mounted read-only.)
```
```bash
systemctl default          # from the rescue shell, continue to default target
```

**Verify:**
```bash
systemctl get-default      # unchanged: the edit was for one boot only
cat /proc/cmdline          # no systemd.unit= after a normal reboot
```

### Task 15: Identify and stop processes

**Task:** Start `sleep 3000` as user `alice` in the background. Find the processes using the most CPU. Stop alice's sleep process gracefully, and force-kill it only if it ignores that.

**Solution:**
```bash
su - alice -c 'nohup sleep 3000 >/dev/null 2>&1 &'
ps -eo pid,user,%cpu,%mem,cmd --sort=-%cpu | head
pgrep -u alice -a sleep
pkill -TERM -u alice sleep
# only if still running:
pkill -KILL -u alice sleep
```

**Verify:**
```bash
pgrep -u alice sleep || echo "no sleep processes for alice"
```

### Task 16: Adjust process scheduling priority

**Task:** Start `sha256sum /dev/zero` with a nice value of 10. Then change the running process to nice value 15.

**Solution:**
```bash
nice -n 10 sha256sum /dev/zero &
pid=$(pgrep -f 'sha256sum /dev/zero')
renice -n 15 -p "$pid"
```

**Verify:**
```bash
ps -o pid,ni,cmd -p "$pid"      # NI column shows 15
kill "$pid"
```

### Task 17: Select a tuning profile

**Task:** Make sure `tuned` is running and enabled, and set the system to the profile it recommends.

**Solution:**
```bash
dnf install -y tuned
systemctl enable --now tuned
tuned-adm recommend             # e.g. virtual-guest
tuned-adm profile "$(tuned-adm recommend)"
```

**Verify:**
```bash
tuned-adm active
tuned-adm verify
systemctl is-enabled tuned
```

### Task 18: Persistent journal and log searching

**Task:** Keep the systemd journal across reboots. Then show all messages of priority `err` or higher from the current boot, and the `sshd` messages from the last hour.

**Solution:**
```bash
mkdir -p /etc/systemd/journald.conf.d
cat > /etc/systemd/journald.conf.d/persist.conf <<'EOF'
[Journal]
Storage=persistent
EOF
systemctl restart systemd-journald
journalctl -b -p err
journalctl -u sshd --since "1 hour ago"
```

**Verify:**
```bash
ls -d /var/log/journal/*     # machine-id directory exists
# after a reboot:
journalctl --list-boots      # more than one boot listed
```

### Task 19: Transfer files securely

**Task:** Copy `/etc/hosts` from the client to `/tmp/` on the server, pull `/export/share/readme.txt` back with sftp, and mirror `/etc/yum.repos.d` to the server with rsync over SSH.

**Solution:**
```bash
scp /etc/hosts root@192.168.50.1:/tmp/client-hosts
sftp root@192.168.50.1 <<'EOF'
get /export/share/readme.txt /root/readme.txt
EOF
dnf install -y rsync
rsync -av -e ssh /etc/yum.repos.d/ root@192.168.50.1:/tmp/repos/
```

**Verify:**
```bash
ssh root@192.168.50.1 'ls -l /tmp/client-hosts /tmp/repos'
cat /root/readme.txt
```

### Task 20: Create GPT partitions

**Task:** On `/dev/vdb`, create a GPT label and three partitions: 1 GiB for XFS data, 512 MiB for swap, and the rest for LVM.

**Solution:**
```bash
parted -s /dev/vdb mklabel gpt
parted -s /dev/vdb mkpart data xfs 1MiB 1025MiB
parted -s /dev/vdb mkpart swap1 linux-swap 1025MiB 1537MiB
parted -s /dev/vdb mkpart lvm1 1537MiB 100%
parted -s /dev/vdb set 3 lvm on
udevadm settle
```

**Verify:**
```bash
parted -s /dev/vdb print
lsblk /dev/vdb
```

### Task 21: Physical volumes, a volume group and a logical volume

**Task:** Create volume group `vgdata` on `/dev/vdb3` with a 16 MiB extent size. Create logical volume `lvdata` of exactly 20 extents, formatted as ext4 and mounted persistently at `/mnt/lvdata` by UUID.

**Solution:**
```bash
pvcreate /dev/vdb3
vgcreate -s 16M vgdata /dev/vdb3
lvcreate -l 20 -n lvdata vgdata          # 20 x 16 MiB = 320 MiB
mkfs.ext4 /dev/vgdata/lvdata
mkdir -p /mnt/lvdata
echo "UUID=$(blkid -s UUID -o value /dev/vgdata/lvdata) /mnt/lvdata ext4 defaults 0 0" \
  >> /etc/fstab
systemctl daemon-reload
mount -a
```

**Verify:**
```bash
vgdisplay vgdata | grep 'PE Size'     # 16.00 MiB
lvs -o lv_name,seg_size_pe vgdata     # 20
findmnt --verify
df -h /mnt/lvdata
```

### Task 22: Mount a file system by label

**Task:** Format `/dev/vdb1` as XFS with the label `DATA` and mount it persistently at `/data1` using the label.

**Solution:**
```bash
mkfs.xfs -f -L DATA /dev/vdb1
mkdir -p /data1
echo 'LABEL=DATA /data1 xfs defaults 0 0' >> /etc/fstab
systemctl daemon-reload
mount -a
```

**Verify:**
```bash
blkid /dev/vdb1          # LABEL="DATA" TYPE="xfs"
findmnt /data1
```

### Task 23: Add a swap partition without disturbing existing swap

**Task:** Turn `/dev/vdb2` into swap, activate it, and make it persistent. Leave the existing swap in place.

**Solution:**
```bash
mkswap /dev/vdb2
echo "UUID=$(blkid -s UUID -o value /dev/vdb2) none swap defaults 0 0" >> /etc/fstab
systemctl daemon-reload
swapon -a
```

**Verify:**
```bash
swapon --show            # original swap plus /dev/vdb2
free -h
```

### Task 24: Add swap on a logical volume

**Task:** Add a 256 MiB logical volume `lvswap` in `vgdata` and use it as extra persistent swap.

**Solution:**
```bash
lvcreate -L 256M -n lvswap vgdata
mkswap /dev/vgdata/lvswap
echo '/dev/vgdata/lvswap none swap defaults 0 0' >> /etc/fstab
swapon -a
```

**Verify:**
```bash
swapon --show | grep dm-
lvs vgdata
```

### Task 25: Remove a logical volume cleanly

**Task:** Create a temporary LV `lvtemp` (100 MiB, XFS, mounted at `/mnt/temp` in fstab), then delete it completely without leaving a broken fstab entry.

**Solution:**
```bash
lvcreate -L 100M -n lvtemp vgdata && mkfs.xfs /dev/vgdata/lvtemp
mkdir -p /mnt/temp
echo '/dev/vgdata/lvtemp /mnt/temp xfs defaults 0 0' >> /etc/fstab
systemctl daemon-reload && mount -a
# now remove it:
umount /mnt/temp
sed -i '\#/dev/vgdata/lvtemp#d' /etc/fstab
systemctl daemon-reload
lvremove -y /dev/vgdata/lvtemp
```

**Verify:**
```bash
lvs vgdata                 # no lvtemp
grep lvtemp /etc/fstab || echo "fstab clean"
findmnt --verify
```

### Task 26: Create and mount a VFAT file system

**Task:** Create a 200 MiB LV `lvvfat` in `vgdata`, format it as VFAT, and mount it persistently at `/mnt/vfat` so that user `alice` owns the files in it.

**Solution:**
```bash
dnf install -y dosfstools
lvcreate -L 200M -n lvvfat vgdata
mkfs.vfat /dev/vgdata/lvvfat
mkdir -p /mnt/vfat
echo "/dev/vgdata/lvvfat /mnt/vfat vfat uid=$(id -u alice),gid=$(id -g alice) 0 0" \
  >> /etc/fstab
systemctl daemon-reload && mount -a
```

**Verify:**
```bash
findmnt /mnt/vfat           # FSTYPE vfat
su - alice -c 'touch /mnt/vfat/ok && ls -l /mnt/vfat'
```

### Task 27: Extend a logical volume and its file system

**Task:** Grow `lvdata` to 500 MiB, together with its ext4 file system, while it stays mounted. If the VG is short of space, add `/dev/vdc` to it first.

**Solution:**
```bash
vgs vgdata                          # check VFree
pvcreate /dev/vdc && vgextend vgdata /dev/vdc     # only if needed
lvextend -r -L 500M /dev/vgdata/lvdata
# -r resizes the file system too (resize2fs for ext4, xfs_growfs for xfs)
```

**Verify:**
```bash
lvs /dev/vgdata/lvdata
df -h /mnt/lvdata                   # about 480M usable
```

### Task 28: Mount an NFS share persistently

**Task:** Mount `192.168.50.1:/export/share` at `/mnt/nfs` persistently.

**Solution:**
```bash
dnf install -y nfs-utils
showmount -e 192.168.50.1
mkdir -p /mnt/nfs
echo '192.168.50.1:/export/share /mnt/nfs nfs defaults,_netdev 0 0' >> /etc/fstab
systemctl daemon-reload
mount -a
```

**Verify:**
```bash
findmnt -t nfs,nfs4
cat /mnt/nfs/readme.txt
```

### Task 29: Automount network home directories with autofs

**Task:** When a user logs in, `/rhome/USERNAME` must be automounted read-write from `192.168.50.1:/rhome/USERNAME`. Users `alice` (UID 3001) and `bob` (UID 3002) must exist locally with those home directories.

**Solution:**
```bash
dnf install -y autofs nfs-utils
useradd -u 3001 -M -d /rhome/alice alice 2>/dev/null \
  || usermod -u 3001 -d /rhome/alice alice
useradd -u 3002 -M -d /rhome/bob bob
echo '/rhome /etc/auto.rhome' > /etc/auto.master.d/rhome.autofs
echo '* -rw,sync 192.168.50.1:/rhome/&' > /etc/auto.rhome
systemctl enable --now autofs
```

If `alice` was created earlier with another UID, `usermod -u` changes it. Also fix the ownership of any files alice owns (see Task 1) with `find / -user OLDUID -exec chown alice {} +`.

**Verify:**
```bash
ls /rhome                    # empty until accessed
su - bob -c 'pwd; touch ~/x; ls -l ~'
findmnt /rhome/bob           # nfs4 mount appears
```

### Task 30: Fix a permission problem on a shared directory

**Task:** Members of group `devs` (`tom`, `jerry`) must be able to create and edit files in `/srv/devs`. New files must belong to group `devs` automatically. Users outside the group get no access. Also give `alice` read-only access to the directory using an ACL.

**Solution:**
```bash
groupadd devs
usermod -aG devs tom; usermod -aG devs jerry
mkdir -p /srv/devs
chgrp devs /srv/devs
chmod 2770 /srv/devs                        # setgid + rwx for owner/group
setfacl -m u:alice:rx /srv/devs
setfacl -d -m u:alice:rx /srv/devs          # default ACL for new files
```

**Verify:**
```bash
ls -ld /srv/devs                            # drwxrws---+ root devs
su - tom -c 'touch /srv/devs/t1'; ls -l /srv/devs/t1   # group devs
su - alice -c 'ls /srv/devs; touch /srv/devs/no'      # ls works, touch denied
getfacl /srv/devs
```

### Task 31: Schedule a recurring job with cron

**Task:** As user `tom`, run `logger "tom-cron"` at 14:23 every day. As root, run `/usr/bin/df -h > /root/df.log` every 15 minutes on weekdays.

**Solution:**
```bash
crontab -u tom -e
# add:  23 14 * * * /usr/bin/logger "tom-cron"
crontab -e
# add:  */15 * * * 1-5 /usr/bin/df -h > /root/df.log
```

**Verify:**
```bash
crontab -l -u tom
crontab -l
systemctl is-active crond
```

### Task 32: Schedule a one-time job with at

**Task:** In five minutes, write the output of `date` to `/root/at.txt`, once.

**Solution:**
```bash
dnf install -y at
systemctl enable --now atd
echo 'date > /root/at.txt' | at now + 5 minutes
```

**Verify:**
```bash
atq                     # one job queued
at -c "$(atq | awk 'NR==1{print $1}')" | tail -3
# after 5 minutes:
cat /root/at.txt
```

### Task 33: Schedule a job with a systemd timer (RHEL 10 objective)

**Task:** Every day at 02:00, archive `/etc` to `/root/etc-DATE.tgz` using a systemd service and timer called `etcbackup`. If the machine was off at 02:00, run the job at the next boot.

**Solution:**
```bash
cat > /etc/systemd/system/etcbackup.service <<'EOF'
[Unit]
Description=Archive /etc

[Service]
Type=oneshot
ExecStart=/bin/bash -c 'tar -czf /root/etc-$(date +%%F).tgz /etc'
EOF
cat > /etc/systemd/system/etcbackup.timer <<'EOF'
[Unit]
Description=Daily /etc archive

[Timer]
OnCalendar=*-*-* 02:00:00
Persistent=true

[Install]
WantedBy=timers.target
EOF
systemctl daemon-reload
systemctl enable --now etcbackup.timer
```

**Verify:**
```bash
systemctl list-timers etcbackup.timer
systemctl start etcbackup.service && ls -l /root/etc-*.tgz
systemd-analyze calendar '*-*-* 02:00:00'
```

### Task 34: Manage services and start them at boot

**Task:** Install `httpd`, make it start at boot, and start it now. Stop and disable `cups` if it is present. Make sure nothing else can start `cups`.

**Solution:**
```bash
dnf install -y httpd
systemctl enable --now httpd
systemctl disable --now cups 2>/dev/null
systemctl mask cups 2>/dev/null
```

**Verify:**
```bash
systemctl is-enabled httpd; systemctl is-active httpd
systemctl is-enabled cups     # masked (or not found)
```

### Task 35: Configure a time service client

**Task:** Sync time from `192.168.50.1` using chrony, and remove the default pool servers.

**Solution:**
```bash
dnf install -y chrony
sed -i 's/^pool /#pool /' /etc/chrony.conf
echo 'server 192.168.50.1 iburst' >> /etc/chrony.conf
systemctl enable chronyd
systemctl restart chronyd
timedatectl set-ntp true
```

**Verify:**
```bash
chronyc sources -v        # ^* 192.168.50.1 once synced
timedatectl               # System clock synchronized: yes
```

### Task 36: Create users and groups

**Task:** Create group `sysadmins` with GID 4000. Create user `harry` with UID 2001 as a supplementary member of `sysadmins`, and user `sarah`, who has no interactive shell and is not in `sysadmins`. Set both passwords to `Lab-Pass-2026`.

**Solution:**
```bash
groupadd -g 4000 sysadmins
useradd -u 2001 -G sysadmins harry
useradd -s /sbin/nologin sarah
echo 'Lab-Pass-2026' | passwd --stdin harry
echo 'Lab-Pass-2026' | passwd --stdin sarah
```

**Verify:**
```bash
id harry                        # uid=2001 ... groups=...,4000(sysadmins)
getent passwd sarah             # ends in /sbin/nologin
getent group sysadmins
```

### Task 37: Password aging

**Task:** Make `harry`'s password expire every 90 days with a 7-day warning, and force him to change it at his next login. Every user created from now on must get a maximum password age of 60 days.

**Solution:**
```bash
chage -M 90 -W 7 harry
chage -d 0 harry
sed -i 's/^PASS_MAX_DAYS.*/PASS_MAX_DAYS\t60/' /etc/login.defs
```

**Verify:**
```bash
chage -l harry
grep ^PASS_MAX_DAYS /etc/login.defs
useradd testage && chage -l testage | grep Maximum    # 60
```

### Task 38: Modify and lock accounts

**Task:** Add `sarah` to group `devs` without removing her from any other group. Set her account to expire on 2026-12-31. Lock `tom`'s password.

**Solution:**
```bash
usermod -aG devs sarah
usermod -e 2026-12-31 sarah         # or: chage -E 2026-12-31 sarah
usermod -L tom                      # or: passwd -l tom
```

**Verify:**
```bash
id sarah
chage -l sarah | grep 'Account expires'
passwd -S tom                       # shows the password as locked
```

### Task 39: Configure privileged access with sudo

**Task:** Members of `sysadmins` can run any command as root through sudo. User `sarah` can run only `/usr/bin/systemctl restart httpd`, without a password.

**Solution:**
```bash
echo '%sysadmins ALL=(ALL) ALL' > /etc/sudoers.d/sysadmins
echo 'sarah ALL=(root) NOPASSWD: /usr/bin/systemctl restart httpd' \
  > /etc/sudoers.d/sarah
chmod 440 /etc/sudoers.d/sysadmins /etc/sudoers.d/sarah
visudo -c
```

**Verify:**
```bash
sudo -l -U harry
sudo -l -U sarah
```

### Task 40: Configure IPv4 and IPv6 with nmcli

**Task:** On the LabNet interface (`eth1`), set IPv4 `192.168.50.10/24` with gateway and DNS `192.168.50.1`, and IPv6 `fd00:50::10/64`. The connection must come up automatically at boot.

**Solution:**
```bash
nmcli dev status
nmcli con add con-name lab-static ifname eth1 type ethernet \
  ipv4.method manual ipv4.addresses 192.168.50.10/24 \
  ipv4.gateway 192.168.50.1 ipv4.dns 192.168.50.1 \
  ipv6.method manual ipv6.addresses fd00:50::10/64 \
  connection.autoconnect yes
nmcli con up lab-static
```

To change an existing connection, use `nmcli con mod NAME ...` and then `nmcli con up NAME`.

**Verify:**
```bash
ip -br addr show eth1
nmcli -f ipv4.addresses,ipv6.addresses,connection.autoconnect con show lab-static
ping -c2 192.168.50.1
```

### Task 41: Hostname and name resolution

**Task:** Set the hostname to `client.lab.example.com`, and make `server.lab.example.com` (alias `server`) resolve to `192.168.50.1` locally.

**Solution:**
```bash
hostnamectl set-hostname client.lab.example.com
echo '192.168.50.1 server.lab.example.com server' >> /etc/hosts
```

**Verify:**
```bash
hostnamectl status | head -3
getent hosts server
cat /etc/resolv.conf     # DNS set by NetworkManager from Task 40
```

### Task 42: Modify the boot loader

**Task:** Add the kernel argument `audit=1` to every installed kernel, and make the GRUB menu wait 10 seconds.

**Solution:**
```bash
grubby --update-kernel=ALL --args="audit=1"
sed -i 's/^GRUB_TIMEOUT=.*/GRUB_TIMEOUT=10/' /etc/default/grub
grub2-mkconfig -o /boot/grub2/grub.cfg
```

On RHEL 9 the right path is `/boot/grub2/grub.cfg` on both BIOS and UEFI; the EFI file is only a stub that points to it. On a UEFI VM whose menu is hidden, also run `grub2-editenv - unset menu_auto_hide`.

**Verify:**
```bash
grubby --info=DEFAULT | grep args
grep GRUB_TIMEOUT /etc/default/grub
# after reboot:
grep -o 'audit=1' /proc/cmdline
```

### Task 43: Restrict access with firewalld

**Task:** Permanently allow HTTP and TCP port 8080 in the default zone. Reject SSH from `192.168.60.0/24` only.

**Solution:**
```bash
systemctl enable --now firewalld
firewall-cmd --permanent --add-service=http
firewall-cmd --permanent --add-port=8080/tcp
firewall-cmd --permanent --add-rich-rule='rule family="ipv4" \
  source address="192.168.60.0/24" service name="ssh" reject'
firewall-cmd --reload
```

**Verify:**
```bash
firewall-cmd --list-all
firewall-cmd --permanent --list-rich-rules
```

### Task 44: Default file permissions (umask)

**Task:** New files created by `harry` in his login shells must be `640` and new directories `750`.

**Solution:**
```bash
echo 'umask 027' >> /home/harry/.bashrc
```

**Verify:**
```bash
su - harry -c 'umask; touch f; mkdir d; ls -ld f d'
# 0027, -rw-r----- f, drwxr-x--- d
```

### Task 45: SSH key-based authentication

**Task:** Let root on the client log in to `harry@192.168.50.1` with an Ed25519 key and no password. On the client, turn off password logins for root over SSH.

**Solution:**
```bash
ssh root@192.168.50.1 'useradd harry; echo Lab-Pass-2026 | passwd --stdin harry'
ssh-keygen -t ed25519 -N '' -f ~/.ssh/id_ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub harry@192.168.50.1
echo 'PermitRootLogin prohibit-password' > /etc/ssh/sshd_config.d/40-local.conf
sshd -t && systemctl reload sshd
```

sshd uses the first value it finds for a setting, and it reads the `sshd_config.d` files in lexical order. A low number such as `40-` therefore wins over the RHEL-provided `50-redhat.conf`.

**Verify:**
```bash
ssh -o BatchMode=yes harry@192.168.50.1 hostname
sshd -T | grep -i permitrootlogin
```

### Task 46: Set the SELinux mode persistently

**Task:** SELinux is currently permissive. Make it enforcing now and after every reboot.

**Solution:**
```bash
setenforce 1
sed -i 's/^SELINUX=.*/SELINUX=enforcing/' /etc/selinux/config
```

If `getenforce` says `Disabled`, the kernel might have been booted with `selinux=0`. Remove that with `grubby --update-kernel=ALL --remove-args=selinux`, run `touch /.autorelabel`, and reboot.

**Verify:**
```bash
getenforce                       # Enforcing
grep ^SELINUX= /etc/selinux/config
sestatus
```

### Task 47: Fix SELinux file contexts for a web root

**Task:** Serve files from `/srv/web` with httpd. Make the SELinux context persistent so that a full relabel doesn't break it.

**Solution:**
```bash
mkdir -p /srv/web && echo "lab web" > /srv/web/index.html
cat > /etc/httpd/conf.d/srvweb.conf <<'EOF'
DocumentRoot "/srv/web"
<Directory "/srv/web">
    Require all granted
</Directory>
EOF
semanage fcontext -a -t httpd_sys_content_t '/srv/web(/.*)?'
restorecon -Rv /srv/web
systemctl restart httpd
```

**Verify:**
```bash
ls -Zd /srv/web /srv/web/index.html     # httpd_sys_content_t
semanage fcontext -l -C                 # your local rule
curl -s http://localhost/                # lab web
```

### Task 48: SELinux port labels and booleans

**Task:** Make httpd also listen on TCP port 82 with SELinux enforcing, and open that port in the firewall. Allow httpd to serve users' `~/public_html` directories, and make that setting persistent.

**Solution:**
```bash
echo 'Listen 82' > /etc/httpd/conf.d/port82.conf
semanage port -a -t http_port_t -p tcp 82
firewall-cmd --permanent --add-port=82/tcp && firewall-cmd --reload
systemctl restart httpd
getsebool -a | grep httpd_enable_homedirs
setsebool -P httpd_enable_homedirs on
```

If something is denied, check `ausearch -m AVC -ts recent`. If `setroubleshoot-server` is installed, `journalctl -t setroubleshoot` shows a suggested fix.

**Verify:**
```bash
semanage port -l | grep '^http_port_t'   # includes 82
ss -tlnp | grep ':82'
curl -s http://localhost:82/
semanage boolean -l -C                   # httpd_enable_homedirs (on, on)
```

### Task 49: Find, inspect and run container images (RHEL 9 exam version)

**Task:** As a regular user, find the UBI 9 httpd image, inspect it without pulling it, pull it, and run it detached as `web` on host port 8080. Serve content from `~/web` on the host, with the correct SELinux label.

**Solution:**
```bash
dnf install -y container-tools            # as root
# then SSH in as harry (not su), because rootless podman needs a real session:
ssh harry@localhost
podman search registry.access.redhat.com/ubi9/httpd
skopeo inspect docker://registry.access.redhat.com/ubi9/httpd-24
mkdir -p ~/web && echo "from container" > ~/web/index.html
podman run -d --name web -p 8080:8080 \
  -v ~/web:/var/www/html:Z registry.access.redhat.com/ubi9/httpd-24
```

**Verify:**
```bash
podman ps
curl -s http://localhost:8080/        # from container
ls -Zd ~/web                          # container_file_t
```

### Task 50: Run a container as a systemd user service (RHEL 9 exam version)

**Task:** Make harry's `web` container start at boot as a systemd user service, even when harry is not logged in.

**Solution:**
```bash
# as harry, in an SSH session:
mkdir -p ~/.config/systemd/user
cd ~/.config/systemd/user
podman generate systemd --name web --new --files
podman stop web && podman rm web
systemctl --user daemon-reload
systemctl --user enable --now container-web.service
loginctl enable-linger harry
```

`podman generate systemd` prints a deprecation notice on later RHEL 9 releases, but it works. The newer method is a Quadlet file, `~/.config/containers/systemd/web.container`, followed by `systemctl --user daemon-reload`.

**Verify:**
```bash
systemctl --user is-enabled container-web.service
loginctl show-user harry -p Linger       # Linger=yes
# reboot, then without logging in as harry:
curl -s http://client:8080/
```

## Practice questions

1. Which command makes the system boot to the text-mode target from now on?
2. In the `rd.break` root-password reset, what happens if you skip `touch /.autorelabel`?
3. After `rd.break` you run `passwd` and get "Authentication token manipulation error". Which step did you probably skip?
4. httpd returns 403 for files in `/srv/web`, and `ls -Z` shows `default_t`. Which two commands fix it persistently?
5. httpd won't start after you add `Listen 8888`, and the log says "Permission denied" on bind. SELinux is enforcing. What is the fix?
6. You ran `firewall-cmd --add-service=http` and it worked, but the rule is gone after a reboot. Why?
7. You ran `firewall-cmd --permanent --add-port=82/tcp`, but the port is still closed. What did you forget?
8. Which two approaches make the journal persistent?
9. Which command finds the package that provides the `semanage` binary?
10. What single command grows LV `/dev/vg1/lv1` by 500 MiB and grows its XFS file system too?
11. Can you shrink an XFS file system? What would you do if you needed it smaller?
12. Which mount option in `/etc/fstab` stops an NFS mount from being attempted before the network is up?
13. In the autofs map line `* -rw 10.0.0.5:/homes/&`, what do `*` and `&` mean?
14. Which command sets an existing user's maximum password age to 60 days?
15. Where do you set the default maximum password age for users created in the future?
16. What does the setgid bit do on a directory?
17. Give the numeric mode for `rwxrws---`.
18. With `umask 027`, what permissions do new files and new directories get?
19. Why does `ln /data/a /home/b` fail with "Invalid cross-device link" when `/home` is a separate file system?
20. What command changes the nice value of running PID 4321 to 10?
21. Which command shows the tuned profile recommended for this machine?
22. Write the cron schedule field for "02:30 every Monday to Friday".
23. What does `Persistent=true` do in a systemd timer?
24. In `chronyc sources` output, what does the `^*` marker mean?
25. Which command adds the kernel argument `quiet` to every installed kernel?
26. You changed `ipv4.addresses` with `nmcli con mod`, but `ip addr` still shows the old address. What next?
27. After you edit fstab and reboot, the system drops into emergency mode. How do you recover, and how could you have caught this before rebooting?
28. A rootless container service stops as soon as its user logs out. Which command fixes this?
29. `systemctl --user` fails with "Failed to connect to bus" after you ran `su - harry`. Why, and what should you do instead?
30. Which grep command prints the lines of a file that are neither comments nor blank?
31. Which tar command creates a bzip2 archive of `/etc` at `/root/etc.tar.bz2`?
32. In a bash script, what do `$#`, `$1` and `$?` hold?
33. Which sudoers line lets group `ops` run any command as root without a password, and where should you put it?
34. `getenforce` prints `Permissive`. Which two commands make it enforcing immediately and after reboots?
35. Which command adds a Flatpak remote named `flathub` system-wide from a `.flatpakrepo` URL?

### Answers

1. `systemctl set-default multi-user.target`. It changes the `default.target` symlink, so it persists; `isolate` only switches the running system.
2. `/etc/shadow` is left with the wrong SELinux label, so logins fail after reboot while SELinux is enforcing. The relabel fixes the label on the next boot.
3. You didn't run `mount -o remount,rw /sysroot` (or didn't `chroot /sysroot`), so the root file system was still read-only.
4. `semanage fcontext -a -t httpd_sys_content_t '/srv/web(/.*)?'` and then `restorecon -Rv /srv/web`. `chcon` alone doesn't survive a relabel.
5. `semanage port -a -t http_port_t -p tcp 8888`, then restart httpd. Also open the port in firewalld if clients need to reach it.
6. Without `--permanent`, the change applies only to the runtime configuration. Add it again with `--permanent`, then run `--reload`, or run `firewall-cmd --runtime-to-permanent`.
7. `firewall-cmd --reload`. Permanent rules don't take effect until a reload or reboot.
8. Create `/var/log/journal` (with the default `Storage=auto`), or set `Storage=persistent` in journald.conf or a drop-in file. Then restart systemd-journald.
9. `dnf provides '*/semanage'`, which shows the package `policycoreutils-python-utils`.
10. `lvextend -r -L +500M /dev/vg1/lv1`. The `-r` option calls `xfs_growfs` for you.
11. No, XFS can only grow. Back it up, recreate it at the smaller size, and restore the data.
12. `_netdev`. It marks the mount as needing the network, so systemd orders it after the network is online.
13. `*` matches any key (the directory name being accessed), and `&` is replaced with that key in the source path.
14. `chage -M 60 USER`.
15. `PASS_MAX_DAYS` in `/etc/login.defs`. It applies only to users created after the change.
16. New files and subdirectories inherit the directory's group instead of the creator's primary group.
17. `2770`: setgid (2), then rwx (7), rwx (7) and no access (0).
18. Files get `640` (666 minus 027) and directories get `750` (777 minus 027).
19. A hard link is another directory entry for the same inode, and inode numbers are unique only within one file system. Use `ln -s` instead.
20. `renice -n 10 -p 4321`. Only root can lower a nice value.
21. `tuned-adm recommend`. Apply it with `tuned-adm profile NAME` and check it with `tuned-adm active`.
22. `30 2 * * 1-5`.
23. If the machine was off when the timer should have fired, the job runs once at the next boot. The timer's last run time is stored on disk.
24. `^` means the source is a server, and `*` means it is the source chrony is currently synchronised to.
25. `grubby --update-kernel=ALL --args="quiet"`.
26. Run `nmcli con up NAME` (or `nmcli dev reapply IFACE`). `con mod` only changes the saved profile.
27. Enter the root password in emergency mode, run `mount -o remount,rw /`, fix `/etc/fstab`, and reboot. Before rebooting, `systemctl daemon-reload`, then `mount -a` and `findmnt --verify` would have caught the error.
28. `loginctl enable-linger USER`. It keeps that user's systemd instance running without a login session.
29. `su` doesn't create a login session with its own user bus. Log in over SSH as that user (or at the console) instead.
30. `grep -Ev '^[[:space:]]*(#|$)' FILE`.
31. `tar -cjf /root/etc.tar.bz2 /etc`. Use `-z` for gzip and `-J` for xz.
32. `$#` is the number of arguments, `$1` is the first argument, and `$?` is the exit status of the last command.
33. `%ops ALL=(ALL) NOPASSWD: ALL` in a file under `/etc/sudoers.d/`. Check it with `visudo -c`.
34. `setenforce 1` (runtime), and set `SELINUX=enforcing` in `/etc/selinux/config` (persistent).
35. `flatpak remote-add --if-not-exists flathub URL`. System-wide is the default when you run it as root.

## Exam-day tips

Delivery rules:
- Remote exam: you need a valid government-issued photo ID, a bootable Live USB that you prepare beforehand with Red Hat's tool, an external webcam, a microphone, a USB 3.0 port and stable internet. Do the compatibility check days ahead, not on exam morning.
- You get no internet, notes or books. You can use the documentation installed on the exam systems: `man`, `man -k`, `--help` and `/usr/share/doc`. Practise finding things there (Task 6), for example the `semanage-fcontext(8)` man page, which has examples.
- Everything you configure is graded after the exam, usually after the systems reboot. Anything that isn't persistent counts as not done.

Time management (the 3-hour length is unverified - check your booking):
- Read every task first. Do the "gatekeeper" tasks first: a root password reset if one is asked for, then networking and hostname, then the repos. Many later tasks depend on these.
- Next, do the quick, independent tasks (users, sudo, cron, tuned, chrony, SELinux booleans). Then do storage, which is the slowest and riskiest.
- Reboot at least twice: once around the middle and once about 20 minutes before the end. Then run a quick check of every task.
- Keep a scratch list of the tasks you've done and verified.

Common traps:
- An fstab typo drops the system into emergency mode. After every fstab edit, run `systemctl daemon-reload`, `mount -a` and `findmnt --verify`.
- A firewalld rule added without `--permanent`, or with `--permanent` but no `--reload`.
- `semanage fcontext` without `restorecon`, or `chcon` instead of `semanage`.
- `setsebool` without `-P`.
- Configuring a service without `systemctl enable`.
- Running `systemctl --user` after `su`; SSH in as the user instead. Forgetting `loginctl enable-linger`.
- Rootless volume mounts without `:Z`, which fail under SELinux.
- An autofs map under `/etc/auto.master.d/` without the `.autofs` extension, which is ignored.
- LV sizes given in extents (`-l`) versus MiB (`-L`). Read carefully and check the PE size.
- Losing the network with a bad `nmcli` change on the interface you're connected through. Use the console for network changes.
- Leaving a relabel for the end: `/.autorelabel` can make the next boot take several minutes.

## Readiness checklist

- [ ] Lab VMs built with snapshots, a local repo, an NFS export and an NTP source
- [ ] Can reset the root password with `rd.break` from memory, first time
- [ ] Can set, isolate and boot once into a target from GRUB
- [ ] Can configure dnf repos from a URL and install by provides
- [ ] Can add a Flatpak remote and install and remove an app
- [ ] Can write a script with args, `if`, `for` and exit codes without looking anything up
- [ ] Can kill and renice processes, and set a tuned profile
- [ ] Journal persists across reboots, and I can filter by unit, priority and time
- [ ] Can create GPT partitions, PVs, VGs (custom PE size) and LVs (by -l and -L)
- [ ] Can mount by UUID and by label, and add swap on a partition and on an LV
- [ ] Can create vfat, ext4 and xfs, and extend an LV with `-r`
- [ ] Can mount NFS in fstab and set up an autofs wildcard map
- [ ] Can fix shared-directory permissions with setgid and ACLs
- [ ] Can schedule with cron, at and a systemd timer
- [ ] Can configure a chrony client and add kernel args with grubby
- [ ] Can set static IPv4 and IPv6, and the hostname, with nmcli and hostnamectl
- [ ] Can use firewalld services, ports and rich rules permanently
- [ ] Can manage users, groups, password aging and sudoers.d files
- [ ] Can set a user's umask and set up SSH key login
- [ ] Can manage SELinux modes, fcontext, port labels and booleans; can read AVCs
- [ ] (RHEL 9 exam) Can run a rootless podman container as a user service with linger
- [ ] Have done two full timed mock runs, with every task persisting after a reboot
- [ ] Have confirmed the exam version (RHEL 9 or 10) and the duration on the booking page
- [ ] Remote exam Live USB and hardware check passed at least 3 days before

## Sources

- EX200 exam page (objectives, RHEL 10 basis, allowed resources): https://www.redhat.com/en/services/training/ex200-red-hat-certified-system-administrator-rhcsa-exam
- RHCSA certification page: https://www.redhat.com/en/services/certification/rhcsa
- Individual exams (remote or testing station, free retake, results in 5 days): https://www.redhat.com/en/services/certification/individual-exams
- Red Hat Certification program guide (3-year validity, retake policy, remote kit, results): https://docs.redhat.com/en/documentation/red_hat_learning_subscription/1-latest/html-single/red_hat_certification_program_guide/index
- RHEL 9 product documentation: https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9
- Rocky Linux downloads: https://rockylinux.org/download
- AlmaLinux downloads: https://almalinux.org/get-almalinux/
- Flathub setup (remote URL used in Task 9): https://flathub.org/setup
- Unverified items: price (about US$500, varies by region), duration (3 hours, reported by third-party prep sites), passing score (210/300, community-reported), and whether a RHEL 9 version of EX200 is still bookable. None of these appear on the official pages checked.
