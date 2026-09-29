# Chapter 4: Cisco NetAcad Linux Unhatched & Linux Essentials

This guide prepares you; you take every course exam and certification exam yourself.

As of September 2026. Facts below were checked against netacad.com, credly.com, lpi.org and pearsonvue.com (see Sources). Anything not confirmed on an official page is marked "unverified".

## At a glance

| Item | Linux Unhatched | Linux Essentials |
|---|---|---|
| Provider | Cisco NetAcad, built with NDG | Cisco NetAcad, built with NDG |
| Cost | Free | Free |
| Delivery | Self-paced online (or via an academy) | Self-paced online (or via an academy) |
| Listed length | 8 hours | 70 hours |
| Listed level | Beginner | Intermediate (Credly: Beginner) |
| Structure | 1 chapter + 1 final assessment | 18 modules, chapter exams, midterm, finals |
| Labs | Guided in-browser VM activities | 18 labs listed on netacad.com |
| Lab environment | Browser-based Linux VM, nothing to install | Browser-based Linux VM, nothing to install |
| Languages | EN, DE, ES, FR, IT, PT | English (as listed) |
| Badge | "Linux Unhatched" course badge | "Linux Essentials" course badge |
| Badge platform | Credly, issued by Cisco | Credly, issued by Cisco |
| How badge is earned | Passing score on the comprehensive exam | Passing score on the comprehensive exam |
| Badge pass mark | 70%, first attempt counts (unverified) | 70%, first attempt counts (unverified) |
| Expiry | None stated | None stated |

Optional paid next step: LPI Linux Essentials certificate.

| Item | LPI Linux Essentials (010-160) |
|---|---|
| Exam code / version | 010-160, objectives version 1.6 |
| Price | USD 120 (US); USD 100 / USD 80 in reduced tiers; EUR 110 |
| Format | 40 questions, 60 minutes, multiple choice |
| Passing score | 500 on a 200-800 scale |
| Delivery | Pearson VUE test center or OnVUE online proctoring |
| Prerequisites | None; you need an LPI ID before booking |
| Validity | Lifetime |
| Retake | Wait 1 week after 1st attempt, 14 days after later ones |
| Languages | EN, DE, JA, PT-BR (VUE); lpi.org also lists FR, ES |
| Discount via NetAcad | NDG lists a coupon; self-paced: unverified |

Why this fits you: it is the quick win of the guide. You already live in a Linux shell every day, so both courses are mostly a confirmation exercise that produces two shareable Credly badges in 2-3 weeks at zero cost. The LPI certificate is optional; it is a foundational credential, so only pay for it if you want a vendor-neutral line on your CV before tackling LFCS or RHCSA.

Notes on the badge facts:

- Credly lists the earning criterion for both badges as achieving a passing score on a comprehensive exam. The exact 70% threshold and "only the first attempt counts" come from Cisco community answers, not a page I could load; treat both as unverified and behave as if the first attempt is the one that matters.
- The Linux Essentials Credly badge text describes 24 prescriptive labs; netacad.com lists 18 labs; the NDG page lists 13 module labs plus 4 challenge labs. The count depends on course version; the content is the same.
- The Credly Linux Unhatched badge lists these skills: absolute and relative paths, basic regular expressions, command line syntax, common text editors, directories, files, permissions, processes, root and system users.
- The Credly Linux Essentials badge lists: open vs closed source applications, basic hardware concepts, Linux OS components, command line, file management, creating and restoring backups, system security, user/group permissions, basic scripting. Credly shows it as type Professional Certification, level Beginner/Foundational.
- The Unhatched page points you on to Linux Essentials or Linux 1; Linux 1 and Linux 2 are separate, paid NetAcad courses aimed at LPIC-1 and are out of scope here.
- After finishing a course, NetAcad sends a Credly invitation to the email on your NetAcad account; accept it on Credly to make the badge public and shareable on LinkedIn.

## Objectives map

The NetAcad Linux Essentials course is built to align with LPI 010-160, so the LPI topics below are the objectives for both. Unhatched covers a subset (mostly 2.x, 3.x and 5.3).

| Objective area | What you must be able to do | Your current strength |
|---|---|---|
| 1.1 Linux evolution and distros | Name major distros, families and where Linux runs | Strong |
| 1.2 Major open source apps | Match apps to jobs; know deb vs rpm packaging | Strong |
| 1.3 Open source licensing | Tell copyleft (GPL) from permissive (MIT, BSD) | Refresh |
| 1.4 ICT skills | Desktop basics, privacy, passwords, basic encryption | Refresh |
| 2.1 Command line basics | Shell syntax, variables, quoting, history | Strong |
| 2.2 Getting help | man sections, `man -k`, `info`, `--help` | Strong |
| 2.3 Directories and listing | Absolute vs relative paths, hidden files, `ls` flags | Strong |
| 2.4 Create, move, delete | `mkdir -p`, `cp -r`, `mv`, `rm -r`, globbing | Strong |
| 3.1 Archiving | `tar` with gzip/bzip2/xz, `zip`/`unzip` | Refresh |
| 3.2 Search and extract | `grep`, basic regex, pipes, redirection, `sort`, `cut` | Strong |
| 3.3 Scripts | Shebang, arguments, `if`, `for`, exit codes | Refresh |
| 4.1 Choosing an OS | Release cycles, LTS vs rolling, Linux vs others | Strong |
| 4.2 Hardware | CPU, RAM, disks, partitions, `/dev`, drivers | Refresh |
| 4.3 Where data is stored | `/etc`, `/var/log`, `/proc`, processes, logs | Strong |
| 4.4 Networking | IP, gateway, DNS, `ip`, `ss`, `/etc/hosts` | Refresh |
| 5.1 Security and user types | root, system and regular users; `sudo`, `su` | Strong |
| 5.2 Users and groups | `useradd`, `groupadd`, `usermod`, `passwd`, `userdel` | Refresh |
| 5.3 Permissions and ownership | `chmod` symbolic and octal, `chown`, `umask` | Strong |
| 5.4 Special files and dirs | Sticky bit, SUID, SGID, hard and symbolic links | Refresh |

LPI weights (sum of sub-objectives): Topic 1 = 7, Topic 2 = 9, Topic 3 = 9, Topic 4 = 8, Topic 5 = 7. Scripting (3.3) is the single heaviest objective at weight 4.

## Study plan

Budget: 5-8 hours per week around a full-time job. You can skim much of the reading; spend the time on labs, the scripting module and licensing/hardware/networking theory, which is where the exam asks things you do not use daily.

| Week | Hours | Course work | Labs and practice | Resources |
|---|---|---|---|---|
| 1 | 6-7 | Unhatched in full + final; LE modules 1-6 | Build WSL2 lab; Tasks 1-5 | NetAcad Unhatched and LE |
| 2 | 7-8 | LE modules 7-12; midterm | Tasks 6-11; Questions 1-18 | NetAcad LE, learning.lpi.org |
| 3 | 7-8 | LE modules 13-18; comprehensive final | Tasks 12-19; Questions 19-35 | NetAcad LE, Credly |
| 4 (optional) | 4-6 | Re-read LPI 010 objectives | Redo weak tasks; book 010-160 | lpi.org, OnVUE |

LE = Linux Essentials. Week 1 is where you earn the first badge (Unhatched); week 3 ends with the second (Linux Essentials). Modules 7-12 cover files, archiving, text and scripting; 13-18 cover storage, networking, security, users, permissions and special files.

Rules of thumb:

- Do every chapter quiz before the midterm and finals; they are the only practice for the NetAcad exam question style.
- Take the comprehensive final only once you score 85%+ on this chapter's practice questions without looking.
- LPI publishes free official study material at https://learning.lpi.org; use it for Topic 1 (licensing, communities) and Topic 4 (hardware, networking) which are the theory-heavy parts.

## Lab setup

Option A: NetAcad's own environment (zero setup). Both courses embed a browser-based Linux VM in the lab pages. Use it for the graded course labs. Its state may reset between sessions, so do not rely on it for multi-day work.

Option B: WSL2 on your Windows 11 machine (recommended for the labs below). Run in an elevated PowerShell:

```powershell
wsl --install -d Ubuntu-24.04
wsl --list --verbose
wsl --set-default-version 2
```

Reboot if asked, open "Ubuntu 24.04" from the Start menu, create your Linux user, then:

```bash
sudo apt update && sudo apt -y full-upgrade
sudo apt -y install man-db manpages zip unzip bzip2 xz-utils tree psmisc \
  iproute2 iputils-ping dnsutils file less nano vim
# Ubuntu minimal images strip man pages; restore them:
sudo unminimize        # answer y; skip if the command is not found
mkdir -p ~/lab && cd ~/lab
```

Snapshot WSL before destructive labs (users, permissions under `/srv`):

```powershell
wsl --export Ubuntu-24.04 C:\wsl\ubuntu-le-clean.tar
# restore later if needed:
# wsl --unregister Ubuntu-24.04
# wsl --import Ubuntu-24.04 C:\wsl\Ubuntu C:\wsl\ubuntu-le-clean.tar
```

Option C: any Linux VM (Hyper-V "Quick Create" Ubuntu, VirtualBox, or a spare cloud VM). All labs below use only standard GNU/Linux tools and work on Ubuntu 22.04/24.04, Debian 12 and Rocky/Alma 9 (replace `apt` with `dnf`).

WSL2 caveats: `last` may show no history (no login records), and `dmesg` needs `sudo`. Everything else behaves like a normal Ubuntu system.

## Hands-on tasks

All labs assume Ubuntu 24.04 in WSL2 and start in `~/lab` unless stated.

### Task 1: Navigate and get help

**Task:** Print your working directory, move to `/etc` using an absolute path, then back to your home with a shortcut. List all files in `/etc` including hidden ones in long format, find the man page section for the `passwd` file format, and list all man pages whose description mentions "archive".

**Solution:**

```bash
pwd
cd /etc
cd ~            # or just: cd
ls -la /etc | head
man -f passwd   # same as whatis passwd: shows passwd(1) and passwd(5)
man 5 passwd    # file format page; q to quit
man -k archive  # same as apropos archive
type cd ls      # builtin vs file on disk
ls --help | head -5
```

**Verify:**

```bash
man -f passwd | grep '(5)'
cd /etc && pwd && cd - >/dev/null && pwd
```

### Task 2: Create, copy, move and delete with globbing

**Task:** In `~/lab/proj`, create directories `src`, `docs` and `tmp/a/b` in one command. Create `report1.txt` to `report5.txt` in `docs`. Copy all reports ending in an odd digit to `tmp`, rename `docs/report5.txt` to `docs/final.txt`, then delete `tmp` and everything in it.

**Solution:**

```bash
mkdir -p ~/lab/proj/{src,docs,tmp/a/b}
cd ~/lab/proj
touch docs/report{1..5}.txt
cp docs/report[135].txt tmp/
ls tmp
mv docs/report5.txt docs/final.txt
rm -r tmp
```

**Verify:**

```bash
ls ~/lab/proj/docs     # final.txt report1.txt report2.txt report3.txt report4.txt
test -d ~/lab/proj/tmp && echo "tmp still exists" || echo "tmp removed"
```

### Task 3: Search and extract data

**Task:** Using `/etc/passwd`, count how many accounts use `/bin/bash` as their shell, print only the usernames and home directories of those accounts sorted alphabetically, and show the 5 most common login shells with counts.

**Solution:**

```bash
grep -c '/bin/bash$' /etc/passwd
grep '/bin/bash$' /etc/passwd | cut -d: -f1,6 | sort
cut -d: -f7 /etc/passwd | sort | uniq -c | sort -rn | head -5
```

**Verify:**

```bash
awk -F: '$7 == "/bin/bash"' /etc/passwd | wc -l    # must match the grep -c result
```

### Task 4: Pipes and redirection

**Task:** Run `ls` on `/etc` and on a directory that does not exist. Send normal output to `out.txt`, errors to `err.txt`. Then run it again appending both streams to `all.log`. Finally, list `/usr/bin`, show it on screen and save a copy to `bin.txt` at the same time, and discard all output from `find / -name shadow`.

**Solution:**

```bash
cd ~/lab
ls /etc /nope > out.txt 2> err.txt
ls /etc /nope >> all.log 2>&1
ls /usr/bin | tee bin.txt | wc -l
find / -name shadow > /dev/null 2>&1
```

**Verify:**

```bash
cat err.txt          # contains "No such file or directory"
grep -c nope all.log # 1
wc -l bin.txt
```

### Task 5: Basic regular expressions

**Task:** Create a file with sample log lines and use `grep` to show: lines that start with `ERROR`, lines ending in a 3-digit number, lines that do not contain `DEBUG`, and case-insensitive matches for `timeout`.

**Solution:**

```bash
cd ~/lab
cat > app.log <<'EOF'
INFO server started on port 3000
DEBUG cache warmup
ERROR db connection Timeout after 500
WARN slow query 120
error lowercase message
ERROR payment timeout code 504
EOF
grep '^ERROR' app.log
grep -E '[0-9]{3}$' app.log
grep -v 'DEBUG' app.log
grep -i 'timeout' app.log
grep -E '^(ERROR|WARN)' app.log | wc -l
```

**Verify:**

```bash
grep -c '^ERROR' app.log        # 2
grep -cE '[0-9]{3}$' app.log    # 3
grep -ci 'timeout' app.log      # 2
```

### Task 6: Archive and compress

**Task:** Create a gzip-compressed tar archive of `~/lab/proj`, list its contents without extracting, extract it into `/tmp/restore`, then create a bzip2 and an xz version and a zip file. Compare sizes.

**Solution:**

```bash
cd ~/lab
tar -czf proj.tar.gz -C ~/lab proj
tar -tzf proj.tar.gz
mkdir -p /tmp/restore && tar -xzf proj.tar.gz -C /tmp/restore
tar -cjf proj.tar.bz2 -C ~/lab proj
tar -cJf proj.tar.xz -C ~/lab proj
zip -r proj.zip proj
gzip -k app.log     # -k keeps the original
ls -lh proj.* app.log*
```

**Verify:**

```bash
ls /tmp/restore/proj/docs
file proj.tar.gz proj.tar.bz2 proj.tar.xz proj.zip
unzip -l proj.zip | tail -1
gunzip -t app.log.gz && echo "gzip OK"
```

### Task 7: First script with arguments and exit codes

**Task:** Write `greet.sh` that prints "Hello, NAME" for every argument given. With no arguments, it prints a usage message to stderr and exits with status 1.

**Solution:**

```bash
cd ~/lab
cat > greet.sh <<'EOF'
#!/bin/bash
if [ $# -lt 1 ]; then
  echo "Usage: $0 NAME..." >&2
  exit 1
fi
for name in "$@"; do
  echo "Hello, $name"
done
exit 0
EOF
chmod +x greet.sh
```

**Verify:**

```bash
./greet.sh; echo "exit=$?"          # usage message, exit=1
./greet.sh Ann "Bo Li"; echo "exit=$?"  # two lines, exit=0
```

### Task 8: Conditionals, tests and loops

**Task:** Write `check.sh` that takes a path and reports whether it is a directory, a regular file, or missing. For a directory, also print how many entries it contains. Then loop over `/etc/hosts /etc /nope` calling the script.

**Solution:**

```bash
cd ~/lab
cat > check.sh <<'EOF'
#!/bin/bash
p="$1"
if [ -d "$p" ]; then
  count=$(ls -A "$p" | wc -l)
  echo "$p is a directory with $count entries"
elif [ -f "$p" ]; then
  echo "$p is a regular file of $(wc -c < "$p") bytes"
else
  echo "$p does not exist" >&2
  exit 2
fi
EOF
chmod +x check.sh
for x in /etc/hosts /etc /nope; do ./check.sh "$x"; echo "rc=$?"; done
```

**Verify:**

```bash
./check.sh /nope 2>/dev/null; echo $?   # 2
./check.sh /etc | grep -q directory && echo PASS
```

### Task 9: Backup script with rotation

**Task:** Write `backup.sh SRC DEST` that creates a timestamped `.tar.gz` of SRC in DEST, reports failure with a non-zero exit code, and keeps only the 3 newest archives.

**Solution:**

```bash
cd ~/lab
cat > backup.sh <<'EOF'
#!/bin/bash
SRC="${1:-$HOME/lab/proj}"
DEST="${2:-$HOME/backups}"
[ -d "$SRC" ] || { echo "No such dir: $SRC" >&2; exit 1; }
mkdir -p "$DEST"
STAMP=$(date +%Y%m%d-%H%M%S)
NAME=$(basename "$SRC")
ARCHIVE="$DEST/$NAME-$STAMP.tar.gz"
if tar -czf "$ARCHIVE" -C "$(dirname "$SRC")" "$NAME"; then
  echo "Created $ARCHIVE"
else
  echo "Backup failed" >&2
  exit 2
fi
ls -1t "$DEST/$NAME"-*.tar.gz | tail -n +4 | xargs -r rm --
EOF
chmod +x backup.sh
for i in 1 2 3 4 5; do ./backup.sh; sleep 1; done
```

**Verify:**

```bash
ls -1 ~/backups | wc -l             # 3
./backup.sh /nope; echo "rc=$?"     # rc=1
tar -tzf "$(ls -1t ~/backups/*.tar.gz | head -1)" | head -3
```

### Task 10: Identify user types and account files

**Task:** Show your UID, GID and groups. List regular (human) accounts with UID 1000 or higher, list system accounts below 1000, show which accounts have a real login shell, and show who is logged in. Explain what is in `/etc/shadow` without printing hashes.

**Solution:**

```bash
id
whoami
awk -F: '$3 >= 1000 && $3 < 65534 {print $1, $3}' /etc/passwd
awk -F: '$3 < 1000 {print $1, $3}' /etc/passwd | head
grep -vE '(nologin|false)$' /etc/passwd | cut -d: -f1,7
who; w
ls -l /etc/passwd /etc/shadow /etc/group
sudo cut -d: -f1,3,5 /etc/shadow | head -3   # user, last change, max days
```

**Verify:**

```bash
id -u root                 # 0
stat -c '%a %U:%G' /etc/shadow   # 640 root:shadow on Ubuntu
```

### Task 11: Create and manage users and groups

**Task:** Create group `devs`. Create users `alice` and `bob` with home directories and bash as shell; add both to `devs` as a supplementary group. Set a password for `alice`, lock `bob`, then delete `bob` including his home directory.

**Solution:**

```bash
sudo groupadd devs
sudo useradd -m -s /bin/bash -G devs alice
sudo useradd -m -s /bin/bash bob
sudo usermod -aG devs bob      # -a is vital: without it other groups are replaced
sudo passwd alice              # type a lab-only password
sudo passwd -l bob
sudo passwd -S bob             # status shows L (locked)
sudo userdel -r bob
```

**Verify:**

```bash
getent group devs              # devs:x:GID:alice
id alice
getent passwd bob || echo "bob removed"
ls -ld /home/alice
```

### Task 12: Permissions with chmod and umask

**Task:** In `~/lab/perm`, create `script.sh`, `notes.txt` and `secret.txt`. Make `script.sh` 755 using symbolic mode, `notes.txt` 644 using octal, and `secret.txt` readable and writable by the owner only. Then set umask 027, create a new file and directory, and predict their modes.

**Solution:**

```bash
mkdir -p ~/lab/perm && cd ~/lab/perm
touch script.sh notes.txt secret.txt
chmod u=rwx,go=rx script.sh
chmod 644 notes.txt
chmod 600 secret.txt
umask 027
touch newfile; mkdir newdir
umask 022      # restore the default for the session
```

**Verify:**

```bash
stat -c '%a %n' script.sh notes.txt secret.txt newfile newdir
# 755 script.sh / 644 notes.txt / 600 secret.txt / 640 newfile / 750 newdir
```

### Task 13: Ownership and a shared group directory

**Task:** Create `/srv/team` owned by root with group `devs`. Members of `devs` must be able to create files there, other users must have no access, and new files must inherit the `devs` group. Change the owner of one file to `alice`.

**Solution:**

```bash
sudo mkdir -p /srv/team
sudo chown root:devs /srv/team
sudo chmod 2770 /srv/team        # 2 = SGID on a directory
sudo -u alice touch /srv/team/plan.txt
sudo touch /srv/team/root-made.txt
sudo chown alice /srv/team/root-made.txt
```

**Verify:**

```bash
ls -ld /srv/team                 # drwxrws--- root devs
sudo ls -l /srv/team             # both files show group devs
sudo -u nobody ls /srv/team; echo "rc=$?"   # Permission denied, rc=2
```

### Task 14: Special permissions and links

**Task:** Show the permission bits that make `/tmp` safe to share and let `passwd` change `/etc/shadow`. Create a sticky world-writable directory of your own. Create a hard link and a symbolic link to a file, show their inodes, then delete the original and observe which link still works.

**Solution:**

```bash
ls -ld /tmp                  # drwxrwxrwt: t = sticky bit
ls -l /usr/bin/passwd        # -rwsr-xr-x: s = SUID
sudo mkdir /srv/drop && sudo chmod 1777 /srv/drop
cd ~/lab && echo "data" > orig.txt
ln orig.txt hard.txt
ln -s orig.txt soft.txt
ls -li orig.txt hard.txt soft.txt
rm orig.txt
cat hard.txt; cat soft.txt
```

**Verify:**

```bash
stat -c '%a %n' /srv/drop     # 1777
ls -l soft.txt                # broken link, shown in red with ls --color
find ~/lab -xtype l           # lists soft.txt as a dangling symlink
```

### Task 15: Processes and job control

**Task:** Start two background `sleep` processes, one at a lower priority. List your jobs, show PID, parent PID, niceness and command for them, bring one to the foreground and stop it, resume it in the background, then kill both. Show memory and load average.

**Solution:**

```bash
sleep 600 &
nice -n 10 sleep 700 &
jobs -l
ps -o pid,ppid,ni,stat,cmd -C sleep
fg %1        # then press Ctrl+Z to stop it
bg %1
pgrep -a sleep
kill %1
pkill -f 'sleep 700'
free -h
uptime
top -b -n 1 | head -15
```

**Verify:**

```bash
pgrep sleep || echo "no sleep processes left"
cat /proc/loadavg
```

### Task 16: Where data is stored

**Task:** Find the CPU model and core count, total RAM, disk usage by filesystem, the size of `/var/log`, the kernel version, and the last 10 system log lines. Identify block devices.

**Solution:**

```bash
lscpu | grep -E 'Model name|^CPU\(s\)'
grep -c ^processor /proc/cpuinfo
grep MemTotal /proc/meminfo
df -h
sudo du -sh /var/log
uname -r
lsblk
sudo journalctl -n 10 --no-pager   # needs systemd (default on current WSL Ubuntu)
sudo dmesg | tail -5
ls /var/log
```

**Verify:**

```bash
nproc                       # equals the processor count above
cat /proc/version
```

### Task 17: Your computer on the network

**Task:** Show your IP addresses, default gateway and DNS configuration. Resolve a hostname, add a local name to `/etc/hosts`, test connectivity, and list listening TCP and UDP ports.

**Solution:**

```bash
ip addr show
ip route show default
cat /etc/resolv.conf
dig +short netacad.com        # or: host netacad.com
echo '127.0.0.1 devbox.local' | sudo tee -a /etc/hosts
getent hosts devbox.local
ping -c 3 devbox.local
ss -tuln
python3 -m http.server 8080 >/dev/null 2>&1 &
ss -tln | grep 8080
kill %%
```

**Verify:**

```bash
getent hosts devbox.local        # 127.0.0.1 devbox.local
ip -4 route | grep default       # shows "default via <gateway>"
```

### Task 18: Packages, licenses and distributions

**Task:** Identify your distribution and release, find which package owns `/bin/ls`, list installed packages whose name contains `ssh`, install `tree`, and find the license text shipped with Ubuntu for the GPL version 3.

**Solution:**

```bash
cat /etc/os-release
dpkg -S /bin/ls                 # coreutils
dpkg -l | grep ssh
apt show tree 2>/dev/null | head -8
sudo apt -y install tree
ls /usr/share/common-licenses/
head -5 /usr/share/common-licenses/GPL-3
less /usr/share/doc/coreutils/copyright
```

**Verify:**

```bash
grep '^VERSION_ID' /etc/os-release
tree -L 1 ~/lab | tail -1
dpkg -s tree | grep Status      # install ok installed
```

### Task 19: Capstone challenge

**Task:** Without looking at the earlier solutions: create group `ops` and user `carol` in it; create `/srv/logs-archive` owned by carol:ops with mode 2750; write `archive-logs.sh` that finds `*.log` files in a given directory older than N days (default 0 for the lab), archives them into a dated `.tar.gz` in `/srv/logs-archive`, prints how many files it archived, and exits 1 if none were found. Run it against `~/lab`.

**Solution:**

```bash
sudo groupadd ops
sudo useradd -m -s /bin/bash -g ops carol
sudo mkdir -p /srv/logs-archive
sudo chown carol:ops /srv/logs-archive
sudo chmod 2750 /srv/logs-archive
cat > ~/lab/archive-logs.sh <<'EOF'
#!/bin/bash
DIR="${1:?usage: $0 DIR [DAYS]}"
DAYS="${2:-0}"
OUT="/srv/logs-archive/logs-$(date +%F-%H%M%S).tar.gz"
# "not newer than N days ago" = at least N days old; N=0 means every existing file
mapfile -t files < <(find "$DIR" -maxdepth 1 -type f -name '*.log' \
  ! -newermt "$DAYS days ago")
if [ "${#files[@]}" -eq 0 ]; then
  echo "No log files found" >&2
  exit 1
fi
tar -czf "$OUT" "${files[@]}" && echo "Archived ${#files[@]} file(s) to $OUT"
EOF
chmod +x ~/lab/archive-logs.sh
sudo ~/lab/archive-logs.sh ~/lab 0
```

For real use you would run it from cron with a DAYS value such as 7. `-mtime +7` is the classic alternative, but note it means "more than 7 full days", which is why the lab uses `-newermt`.

**Verify:**

```bash
ls -ld /srv/logs-archive                   # drwxr-s--- carol ops
sudo ls -l /srv/logs-archive
sudo tar -tzf "$(sudo ls -1t /srv/logs-archive/*.tar.gz | head -1)"
sudo ~/lab/archive-logs.sh /etc 0; echo "rc=$?"   # rc=1, no *.log in /etc top level
```

## Practice questions

1. Which command shows the manual page for the format of the `/etc/passwd` file rather than the `passwd` command? A) `man passwd`  B) `man 5 passwd`  C) `help passwd`  D) `info 1 passwd`
2. Short answer: what single command searches the man page descriptions for the keyword "compress"?
3. You are in `/var/log/nginx`. Which path is relative? A) `/var/log`  B) `~/logs`  C) `../apt`  D) `/home/rizwan`
4. Which command creates `a/b/c` in one step, creating parents as needed? A) `mkdir a/b/c`  B) `mkdir -p a/b/c`  C) `mkdir -r a/b/c`  D) `touch -d a/b/c`
5. What does `ls -a` show that plain `ls` does not?
6. Which command copies the directory `site` and everything inside it to `backup`? A) `cp site backup`  B) `mv -r site backup`  C) `cp -r site backup`  D) `cp -a site`
7. After `cmd > out.txt 2>&1`, where do error messages go?
8. Which command prints only lines of `app.log` that do NOT contain `DEBUG`? A) `grep -i DEBUG app.log`  B) `grep -v DEBUG app.log`  C) `grep -c DEBUG app.log`  D) `grep ^DEBUG app.log`
9. In a basic regular expression, what do `^` and `$` match?
10. Which pipeline counts unique values in the 7th colon-separated field of `/etc/passwd`? A) `cut -f7 /etc/passwd | uniq | wc -l`  B) `cut -d: -f7 /etc/passwd | sort -u | wc -l`  C) `sort /etc/passwd | cut -d: -f7`  D) `wc -l /etc/passwd`
11. Which `tar` command extracts `site.tar.xz` into `/tmp/x`? A) `tar -czf site.tar.xz /tmp/x`  B) `tar -xJf site.tar.xz -C /tmp/x`  C) `tar -tJf site.tar.xz /tmp/x`  D) `tar -xzf site.tar.xz -d /tmp/x`
12. Short answer: which `tar` option lists an archive's contents without extracting?
13. What does `gzip file.log` do to the original `file.log` by default?
14. What is the purpose of the first line `#!/bin/bash` in a script?
15. Inside a script, what do `$#`, `$1` and `$?` hold?
16. A script runs `exit 3`. How can the caller see that value immediately afterwards?
17. What must you do before running `./deploy.sh` if it gives "Permission denied"?
18. Which test checks that `/etc/app` exists and is a directory? A) `[ -f /etc/app ]`  B) `[ -e /etc/app ]`  C) `[ -d /etc/app ]`  D) `[ -x /etc/app ]`
19. What octal mode corresponds to `rwxr-x---`?
20. With a umask of `027`, what permissions does a newly created regular file get?
21. What does `chmod g+s shared/` do on a directory?
22. Why can every user write to `/tmp` but not delete other users' files there?
23. What is the effect of the `s` in `-rwsr-xr-x` on `/usr/bin/passwd`?
24. Which command adds `alice` to the `docker` group while keeping her other supplementary groups? A) `usermod -G docker alice`  B) `usermod -aG docker alice`  C) `groupadd docker alice`  D) `useradd -G docker alice`
25. Which file stores password hashes, and who can read it?
26. On Ubuntu, what UID range is normally used for regular human accounts?
27. You delete a file that has one hard link and one symbolic link pointing to it. Which link still shows the data?
28. Which command shows every process on the system with its parent PID? A) `jobs`  B) `ps -ef`  C) `top -p 1`  D) `pgrep`
29. What does `nice -n 10 cmd` do, and can a normal user use `nice -n -5`?
30. Which command sends the default termination signal to process 4242, and what is that signal?
31. Which directory holds virtual files describing running processes and kernel state? A) `/etc`  B) `/var`  C) `/proc`  D) `/opt`
32. Which command shows the default gateway on a modern Linux system? A) `ifconfig -g`  B) `ip route show default`  C) `ss -r`  D) `hostname -g`
33. Which file contains local hostname-to-IP overrides checked before DNS on most systems?
34. Which license is copyleft: MIT, BSD 2-clause, Apache 2.0, or GPLv3?
35. Which distribution family uses `.rpm` packages: Debian/Ubuntu or RHEL/Fedora/Rocky?

### Answers

1. B. Section 5 holds file formats; `man passwd` opens section 1 (the command) first.
2. `man -k compress` (equivalent to `apropos compress`); it searches the whatis database.
3. C. `..` is relative to the current directory; `~` expands to an absolute home path.
4. B. `-p` creates missing parent directories and does not fail if they exist.
5. Hidden entries whose names start with a dot, plus `.` and `..`. (`-A` omits those two.)
6. C. `cp` needs `-r` (or `-a`) to copy directories; `mv` has no `-r`.
7. Into `out.txt` as well: stdout goes to the file first, then stderr is pointed at stdout.
8. B. `-v` inverts the match; `-i` ignores case and `-c` counts.
9. `^` anchors the start of a line, `$` anchors the end.
10. B. `uniq` only removes adjacent duplicates, so sort first; `-d:` sets the delimiter.
11. B. `-x` extract, `-J` xz, `-f` file, `-C` change to the target directory first.
12. `-t` (for example `tar -tzf file.tar.gz`).
13. Replaces it with `file.log.gz`; the original is removed unless you use `-k`.
14. The shebang tells the kernel which interpreter to run the script with.
15. Number of arguments, the first argument, and the exit status of the last command.
16. `echo $?` right after the script finishes, before running anything else.
17. Add execute permission, for example `chmod u+x deploy.sh` (or run `bash deploy.sh`).
18. C. `-d` is true only for directories; `-e` is true for any existing path.
19. 750: rwx = 7, r-x = 5, --- = 0.
20. 640 (rw-r-----): files start from 666, and 027 removes group write and all other bits.
21. Sets SGID: new files created inside inherit the directory's group.
22. `/tmp` is mode 1777; the sticky bit limits deletion to the file owner, dir owner or root.
23. SUID: the program runs with the file owner's (root's) privileges, so it can update shadow.
24. B. Without `-a`, `-G` replaces the whole supplementary group list.
25. `/etc/shadow`; only root and (on Ubuntu) members of the `shadow` group can read it.
26. 1000 and above (up to 60000 by default); system accounts use lower UIDs, root is 0.
27. The hard link: it points to the same inode. The symlink points to a name that is gone.
28. B. `-e` selects all processes, `-f` adds full format including PPID.
29. Starts cmd with lower priority (niceness 10); negative values need root.
30. `kill 4242` sends SIGTERM (15); `kill -9` would send SIGKILL.
31. C. `/proc` is a virtual filesystem generated by the kernel.
32. B. `ifconfig` is legacy and has no `-g`; `ss` shows sockets, not routes.
33. `/etc/hosts` (order is set by the `hosts:` line in `/etc/nsswitch.conf`).
34. GPLv3: derived works must be released under the same license. The others are permissive.
35. RHEL/Fedora/Rocky use RPM (`dnf`, `rpm`); Debian/Ubuntu use `.deb` (`apt`, `dpkg`).

## Exam-day tips

NetAcad course exams (for the Credly badges):

- The exams are taken online inside the course in your browser; they are not proctored. Official pages I could load do not publish a time limit, question count or number of attempts for the Unhatched or Essentials finals: unverified. Community answers say only the first attempt of the final counts toward the badge and the pass mark is 70%; plan on getting it right the first time.
- Do all chapter exams and the midterm first; the comprehensive final draws on the same pool of topics.
- Some items are "choose two/three" or drag-and-drop; read the instruction line before answering.
- Use a stable connection and a desktop browser; do not open the exam on a phone. Submit before closing the tab.
- After you pass, check the email tied to your NetAcad account for the Credly invitation and accept it; badge issue can take a little time.

LPI 010-160 (optional, paid):

- Create an LPI ID at lpi.org first; you need it to schedule with Pearson VUE.
- OnVUE online: quiet private room, webcam, stable internet, clear desk, and run the Pearson system test beforehand. LPI states the OnVUE interface and proctors are English only.
- Bring government-issued photo ID that matches your registration name exactly (Pearson VUE standard rule; check the confirmation email for specifics).
- No notes, man pages or Linux shell during the exam; everything is from memory.
- 40 questions in 60 minutes is about 90 seconds each. Do one pass answering what you know, flag the rest, come back.
- LPI lists the format as multiple choice. Older LPI exams also used fill-in-the-blank items, so know exact command names and option spellings (unverified for the current version).
- Scaled score: 500 of 800 to pass. You get the result immediately at the end.

Common traps:

- `usermod -G` without `-a` silently removes other groups.
- `tar` compression letters: `z` gzip, `j` bzip2, `J` xz. `-C` goes before the directory argument when creating, and sets the target when extracting.
- `2>&1 > file` (wrong order) still prints errors to the screen; `> file 2>&1` is correct.
- `uniq` without `sort` misses non-adjacent duplicates.
- Default permissions come from 666 (files) and 777 (dirs) minus the umask; files never get execute by default.
- Deleting a symlink's target breaks the symlink; a hard link keeps the data alive.
- Licensing questions: "free" means freedom, not price; GPL is copyleft, MIT/BSD/Apache are permissive.
- Theory topics you rarely touch as a developer: hardware terms (RAM vs storage, `/dev/sda` vs `/dev/nvme0n1`), and privacy/ICT basics in Topic 1.4.

## Readiness checklist

- [ ] NetAcad account created and both courses enrolled (self-paced)
- [ ] WSL2 Ubuntu 24.04 lab built and exported as a clean snapshot
- [ ] Linux Unhatched final passed and Credly badge accepted
- [ ] Linux Essentials chapter exams and midterm done with 85%+
- [ ] Tasks 1-6 done (navigation, files, grep, redirection, regex, archiving)
- [ ] Tasks 7-9 done (scripts with arguments, tests, loops, exit codes, backups)
- [ ] Tasks 10-14 done (user types, users/groups, chmod/umask, SGID dir, links)
- [ ] Tasks 15-18 done (processes, hardware/storage, networking, packages/licenses)
- [ ] Task 19 capstone done from memory
- [ ] 30+ of 35 practice questions right without looking at answers
- [ ] Can explain GPL vs MIT, deb vs rpm, LTS vs rolling in one sentence each
- [ ] Linux Essentials comprehensive final passed and Credly badge accepted
- [ ] Both badges added to LinkedIn and CV
- [ ] Decision made on the paid LPI 010-160 (skip, or book OnVUE after week 4)
- [ ] If booking LPI: LPI ID created, OnVUE system test passed, ID ready

## Sources

- https://www.netacad.com/courses/linux-unhatched (course page: free, 8 hours, beginner, self-paced, languages, NDG)
- https://www.netacad.com/courses/linux-essentials (course page: free, 70 hours, intermediate, 18 labs, self-paced, LPI alignment, course badge)
- https://www.netacad.com/courses/linux-1 (paid follow-on course, LPIC-1 track)
- https://www.credly.com/org/cisco/badge/linux-unhatched (badge description, skills, earning criteria)
- https://www.credly.com/org/cisco/badge/linux-essentials (badge description, skills, earning criteria, type and level)
- https://www.netdevgroup.com/online/courses/open-source/linux-essentials (NDG course structure, exams, 010-160 alignment, coupon note)
- https://www.netdevgroup.com/online/courses/open-source/linux-unhatched (NDG Unhatched outline)
- https://learningnetwork.cisco.com/s/question/0D56e0000CCkHGtCQN/would-i-be-given-a-credly-badge-upon-completion-of-cisco-network-essentials-selfpaced-via-skillsforall (community source for the 70% / first attempt claim; unverified)
- https://www.lpi.org/our-certifications/linux-essentials-overview/ (exam code, version, format, delivery, validity, languages)
- https://www.lpi.org/our-certifications/exam-010-objectives/ (objectives and weights)
- https://www.lpi.org/exam-pricing/ (USD 120 / 100 / 80, EUR 110)
- https://www.lpi.org/about-lpi/frequently-asked-questions/ (200-800 scale, pass at 500, OnVUE requirements)
- https://www.lpi.org/policies/ (retake waiting periods)
- https://www.pearsonvue.com/us/en/lpi.html (LPI ID requirement, 010-160 details)
- https://learning.lpi.org (free official LPI study materials)
- https://learn.microsoft.com/windows/wsl/install (WSL2 installation)
