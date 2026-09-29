# Chapter 3: AWS Certified SysOps Administrator - Associate

This guide prepares you; you register for, sit, and pass the exam yourself.

**Name change first:** AWS renamed this credential. The SysOps Administrator - Associate exam (SOA-C02) ran for the last time on September 29, 2025. Its replacement, **AWS Certified CloudOps Engineer - Associate (exam code SOA-C03)**, has been live since September 30, 2025. Same exam code family (SOA), same level, updated content. Everything in this chapter targets SOA-C03. If you already held the SysOps cert you would not need to retake anything, but you don't, so SOA-C03 is your exam.

**Exam labs:** SOA-C02 used to include hands-on exam labs in a live AWS console. AWS removed them on March 28, 2023 ("until further notice"), and SOA-C03 launched as multiple choice and multiple response only. You will not be graded in a live console, but the labs below remain the fastest way to make the scenario questions easy.

As of September 2026.

## At a glance

| Item | Detail |
|---|---|
| Official name | AWS Certified CloudOps Engineer - Associate |
| Exam code | SOA-C03 (replaced SOA-C02 on Sep 30, 2025) |
| Exam guide version | 1.1, published June 1, 2026 |
| Format | Multiple choice and multiple response; no exam labs |
| Questions | 65 (50 scored, 15 unscored, not identified) |
| Duration | 130 minutes |
| Passing score | 720 on a 100-1,000 scaled score |
| Scoring | Compensatory: pass overall, not per domain |
| Guessing | No penalty; unanswered = wrong |
| Price | 150 USD (plus local tax where applicable) |
| Delivery | Pearson VUE test center or online proctored |
| Languages | English, Japanese, Korean, Simplified Chinese |
| 2026 change | Korean and Chinese versions retire after Nov 19, 2026 |
| Validity | 3 years |
| Retake | Wait 14 days after a fail; full fee each attempt |
| Prerequisites | None (AWS suggests 1 year of AWS ops) |
| Next version | No SOA-C03 replacement announced (checked Sep 2026) |

Domain weights (SOA-C03):

| Domain | Weight |
|---|---|
| 1. Monitoring, logging, analysis, remediation, performance | 22% |
| 2. Reliability and business continuity | 22% |
| 3. Deployment, provisioning, and automation | 22% |
| 4. Security and compliance | 16% |
| 5. Networking and content delivery | 18% |

Why this fits you: you already run Node.js behind Nginx with PM2 on Linux, so the ops mindset (logs, restarts, health checks, patching, backups) is there. This exam turns that into the AWS-native versions: CloudWatch instead of `tail -f`, Systems Manager instead of SSH loops, ALB plus Auto Scaling instead of one hand-built box. It is also the most hands-on AWS associate credential and a natural bridge from "I deploy apps" to "I operate the platform".

## Objectives map

Your strength is judged from your profile: strong Linux/Nginx/PM2/cron ops, lighter on AWS ops services and formal networking.

| Objective area | What you must be able to do | Your current strength |
|---|---|---|
| 1.1 Metrics, alarms, filters | CloudWatch agent, log groups, metric filters, alarms | Refresh |
| 1.1 Notifications, dashboards | SNS alerts, composite alarms, cross-account dashboards | New |
| 1.2 Identify and remediate | EventBridge rules, SSM Automation runbooks, Lambda fixes | New |
| 1.3 Compute performance | Right-size EC2, placement groups, Compute Optimizer | Refresh |
| 1.3 Storage performance | EBS gp3 tuning, S3 multipart, Transfer Acceleration | Refresh |
| 1.3 Database performance | RDS metrics, Performance Insights, RDS Proxy | New |
| 1.3 Shared storage | Choose EFS vs FSx vs S3; EFS lifecycle | New |
| 2.1 Scalability | Auto Scaling policies, caching (CloudFront, ElastiCache) | Refresh |
| 2.1 Database scaling | Read replicas, Aurora, DynamoDB capacity modes | New |
| 2.2 High availability | ELB and Route 53 health checks, Multi-AZ | Refresh |
| 2.3 Backup and restore | AWS Backup, snapshots, PITR, S3 versioning, DR tiers | Refresh |
| 3.1 Provisioning | AMIs, Image Builder, CloudFormation, CDK, StackSets, RAM | New |
| 3.1 Deployment issues | Fix stack errors, subnet sizing, permission failures | New |
| 3.1 Third-party IaC | Terraform and Git in AWS workflows | Refresh |
| 3.2 Automate operations | Systems Manager (Run Command, Patch, State Manager) | New |
| 3.2 Event-driven automation | Lambda, S3 notifications, EventBridge | Refresh |
| 4.1 IAM | Roles, MFA, policy conditions, resource policies | Refresh |
| 4.1 Audit access | CloudTrail, IAM Access Analyzer, policy simulator | New |
| 4.1 Multi-account | Organizations, SCPs, IAM Identity Center | New |
| 4.1 Compliance | Config rules, conformance packs, Trusted Advisor | New |
| 4.2 Data protection | KMS, ACM, Secrets Manager, Parameter Store | Refresh |
| 4.2 Findings | Security Hub, GuardDuty, Inspector, Macie | New |
| 5.1 VPC | Subnets, routes, IGW, NAT, SG vs NACL, endpoints | Refresh |
| 5.1 Network protection | WAF, Shield, Network Firewall, DNS Firewall | New |
| 5.2 DNS and delivery | Route 53 policies, Resolver, CloudFront, Global Accelerator | Refresh |
| 5.3 Troubleshooting | Flow logs, ELB logs, Reachability Analyzer, caching | Refresh |

AI-era additions in guide v1.1 (awareness level only): Amazon Bedrock, Kiro, AWS DevOps Agent, AWS Security Agent and AWS Health Dashboard were added to the in-scope list. Know what each does at a sentence level; expect them as options, not deep configuration.

## Study plan

Ten weeks at 5-8 hours per week. Do the labs in the order given; each week ends with a cleanup check in Billing.

| Week | Focus | Labs | Resources |
|---|---|---|---|
| 1 | Account, budget, IAM, CLI, exam guide | Tasks 1-2 | SOA-C03 exam guide; Skill Builder pretest |
| 2 | EC2, user data, IMDSv2, EBS | Tasks 3, 9 | EC2 User Guide; Skill Builder EC2 courses |
| 3 | CloudWatch agent, logs, alarms | Tasks 4-5 | CloudWatch User Guide; One Observability Workshop |
| 4 | Systems Manager, EventBridge | Tasks 6-8 | SSM User Guide; EventBridge User Guide |
| 5 | ELB, Auto Scaling, CloudFront | Tasks 10, 17 | ELB and EC2 Auto Scaling guides |
| 6 | S3, Lambda events, Backup, RDS | Tasks 11-12, 14, 20 | S3 and AWS Backup guides; RDS guide |
| 7 | VPC, Route 53, network troubleshooting | Tasks 13, 16 | VPC User Guide; Route 53 Developer Guide |
| 8 | CloudFormation, CDK, StackSets, RAM | Task 15 | CloudFormation User Guide; CDK Workshop |
| 9 | KMS, Config, CloudTrail, Organizations | Tasks 18-19 | Security pillar of Well-Architected |
| 10 | Practice questions, weak areas, book | Redo weakest 3 | Official Practice Question Set and Exam |

Free and official resources:

- Exam guide (free): https://docs.aws.amazon.com/aws-certification/latest/sysops-administrator-associate-03/sysops-administrator-associate-03.html
- AWS Skill Builder (skillbuilder.aws): the exam page lists a 4-step exam prep plan, Official Pretest, Official Practice Question Set, Official Practice Exam, flashcards, Builder Labs, Cloud Quest, SimuLearn and Jam. Several are free; some need a Skill Builder subscription (which items are free: unverified, check before paying).
- AWS Workshops catalog (free): https://catalog.workshops.aws (search "observability", "systems manager", "cloudformation").
- AWS Well-Architected Framework, Operational Excellence and Reliability pillars (free).
- Service user guides on docs.aws.amazon.com for every service in the objectives map.

Rule of thumb: for every lab, write down the one exam question you think it answers. Week 10 is only questions, reviewing every wrong answer against the docs.

## Lab setup

Everything runs in the AWS Free Tier, using the AWS CLI v2 from AWS CloudShell (free, already signed in, no local keys) or from WSL2 Ubuntu on your Windows machine. You create the account and do every sign-in yourself.

### Step 1: Account and plan

- Create an AWS account at https://aws.amazon.com/free yourself. Accounts opened after July 15, 2025 choose a **Free plan** or a **Paid plan**. Both get up to 200 USD in credits (100 USD at sign-up, up to 100 USD more for completing "Explore AWS" activities in Console Home).
- The Free plan never bills you, but the account closes 6 months after opening or when credits run out, and some services are restricted. If a lab step says a feature needs the Paid plan, skip it or decide yourself whether to upgrade.
- Free-tier eligible EC2 types for these accounts: t3.micro, t3.small, t4g.micro, t4g.small, c7i-flex.large, m7i-flex.large. The labs use t3.micro.
- Secure root: enable MFA on the root user, never create root access keys, and use an admin identity (IAM Identity Center user, or an IAM user with MFA) for daily work.

### Step 2: Region choice

Use **us-east-1** for all labs. Billing metrics, Route 53 health-check metrics and CloudFront certificates live there, which removes a whole class of "why can't I see the metric" problems.

### Step 3: CLI (pick one)

Option A, CloudShell: open the console in us-east-1 and click the CloudShell icon. The CLI, `jq`, `zip` and the Session Manager plugin are preinstalled. Your home directory (1 GB) persists between sessions.

Option B, WSL2 Ubuntu on Windows:

```bash
sudo apt update && sudo apt install -y unzip jq zip curl
curl -s "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o awscliv2.zip
unzip -q awscliv2.zip && sudo ./aws/install
aws --version
# Session Manager plugin (official AWS download location)
SMP=https://s3.amazonaws.com/session-manager-downloads/plugin/latest
curl -s -o smp.deb "$SMP/ubuntu_64bit/session-manager-plugin.deb"
sudo dpkg -i smp.deb
# Sign in through IAM Identity Center (you complete the browser sign-in)
aws configure sso --profile lab
export AWS_PROFILE=lab
aws sts get-caller-identity
```

### Step 4: Lab environment file

Every lab appends the IDs it creates to `~/lab.env`, so you can close the shell and continue later with `source ~/lab.env`.

```bash
cat > ~/lab.env <<EOF
export AWS_REGION=us-east-1
export AWS_DEFAULT_REGION=us-east-1
export ACCOUNT_ID=$(aws sts get-caller-identity --query Account --output text)
export EMAIL=you@example.com
EOF
source ~/lab.env && echo "$ACCOUNT_ID"
```

Replace `you@example.com` with your own address before running it.

### Step 5: Budget alert before anything else

Do **Task 1** now, before launching any resource. It sets a monthly cost budget that ignores credits, so it warns you while credits are silently being spent.

### Step 6: Cost map

| Resource in labs | Cost note |
|---|---|
| EC2 t3.micro, 8-30 GB EBS | Free-tier eligible; stop or terminate after labs |
| Public IPv4 address | Small hourly charge; credits cover it |
| ALB (Task 10) | Hourly plus LCU; delete within 2 hours |
| RDS db.t4g.micro (Task 20) | Free-tier eligible; delete same day |
| KMS customer key (Task 18) | About 1 USD/month, prorated; schedule deletion |
| Route 53 health check (Task 13) | Small monthly fee, prorated; delete after |
| AWS Config (Task 19) | Per item recorded; pennies if scoped |
| CloudWatch, Lambda, SNS, CloudFront | Always-free allowances cover the labs |
| NAT gateway | Not used: hourly cost is the classic surprise |

### Step 7: Core teardown script

Tasks 2-8 and 13-14 share one instance (`lab-web`), its security group, its IAM role and an SNS topic. Each task has its own cleanup; this script removes the shared core when you finish a study session.

```bash
cat > ~/teardown-core.sh <<'EOF'
#!/bin/bash
source ~/lab.env
aws ec2 terminate-instances --instance-ids "$IID"
aws ec2 wait instance-terminated --instance-ids "$IID"
aws ec2 delete-security-group --group-id "$SG"
aws iam remove-role-from-instance-profile \
  --instance-profile-name lab-ec2-profile --role-name lab-ec2-role
aws iam delete-instance-profile --instance-profile-name lab-ec2-profile
for p in AmazonSSMManagedInstanceCore CloudWatchAgentServerPolicy; do
  aws iam detach-role-policy --role-name lab-ec2-role \
    --policy-arn "arn:aws:iam::aws:policy/$p"
done
aws iam delete-role --role-name lab-ec2-role
aws sns delete-topic --topic-arn "$TOPIC"
for g in /lab/nginx/access /lab/pm2/error /lab/pm2/out; do
  aws logs delete-log-group --log-group-name "$g" 2>/dev/null
done
aws ssm delete-parameter --name AmazonCloudWatch-lab-web 2>/dev/null
echo "core removed"
EOF
chmod +x ~/teardown-core.sh
```

Once a week: Billing and Cost Management, Bills, and Cost Explorer (group by service). Also check EC2 in every Region you touched for stray instances, volumes, snapshots and Elastic IPs.

## Hands-on tasks

Each task lists Task, Solution, Verify and Cleanup. Run `source ~/lab.env` at the start of every session. Commands assume bash in CloudShell or WSL2.

### Task 1: Budget alerts that ignore credits

**Task:** Create a monthly cost budget of 5 USD for the account that emails you at 80% of actual spend and at 100% of forecast spend. The budget must measure gross usage, not usage after credits.

**Solution:**

```bash
source ~/lab.env
cat > budget.json <<'EOF'
{"BudgetName":"lab-monthly-5usd",
 "BudgetLimit":{"Amount":"5","Unit":"USD"},
 "TimeUnit":"MONTHLY","BudgetType":"COST",
 "CostTypes":{"IncludeCredit":false,"IncludeRefund":false}}
EOF
cat > notif.json <<EOF
[{"Notification":{"NotificationType":"ACTUAL","ComparisonOperator":"GREATER_THAN",
   "Threshold":80,"ThresholdType":"PERCENTAGE"},
  "Subscribers":[{"SubscriptionType":"EMAIL","Address":"$EMAIL"}]},
 {"Notification":{"NotificationType":"FORECASTED","ComparisonOperator":"GREATER_THAN",
   "Threshold":100,"ThresholdType":"PERCENTAGE"},
  "Subscribers":[{"SubscriptionType":"EMAIL","Address":"$EMAIL"}]}]
EOF
aws budgets create-budget --account-id "$ACCOUNT_ID" \
  --budget file://budget.json --notifications-with-subscribers file://notif.json
```

Why `IncludeCredit:false`: the Budgets API includes credits by default, so a normal budget shows about 0 USD while your credits drain. Optionally also add the console's "Zero spend budget" template (Billing, Budgets, Create budget, Use a template).

**Verify:**

```bash
aws budgets describe-budgets --account-id "$ACCOUNT_ID" \
  --query 'Budgets[].[BudgetName,BudgetLimit.Amount,CostTypes.IncludeCredit]'
aws budgets describe-notifications-for-budget --account-id "$ACCOUNT_ID" \
  --budget-name lab-monthly-5usd
```

**Cleanup:** Keep this budget for the whole study period. When you close the lab account:

```bash
aws budgets delete-budget --account-id "$ACCOUNT_ID" --budget-name lab-monthly-5usd
```

### Task 2: IAM role for EC2, password policy and policy simulation

**Task:** Create an instance role that allows Systems Manager and the CloudWatch agent and nothing else. Set an account password policy (min 14 chars, all character classes, reuse prevention 5). Prove with the policy simulator that the role can register with SSM but cannot delete S3 buckets. Confirm root MFA is on.

**Solution:**

```bash
source ~/lab.env
cat > ec2-trust.json <<'EOF'
{"Version":"2012-10-17","Statement":[{"Effect":"Allow",
 "Principal":{"Service":"ec2.amazonaws.com"},"Action":"sts:AssumeRole"}]}
EOF
aws iam create-role --role-name lab-ec2-role \
  --assume-role-policy-document file://ec2-trust.json
for p in AmazonSSMManagedInstanceCore CloudWatchAgentServerPolicy; do
  aws iam attach-role-policy --role-name lab-ec2-role \
    --policy-arn "arn:aws:iam::aws:policy/$p"
done
aws iam create-instance-profile --instance-profile-name lab-ec2-profile
aws iam add-role-to-instance-profile --instance-profile-name lab-ec2-profile \
  --role-name lab-ec2-role
aws iam update-account-password-policy --minimum-password-length 14 \
  --require-symbols --require-numbers --require-uppercase-characters \
  --require-lowercase-characters --password-reuse-prevention 5
```

**Verify:**

```bash
aws iam simulate-principal-policy \
  --policy-source-arn "arn:aws:iam::$ACCOUNT_ID:role/lab-ec2-role" \
  --action-names ssm:UpdateInstanceInformation s3:DeleteBucket \
  --query 'EvaluationResults[].[EvalActionName,EvalDecision]' --output table
# expect: allowed / implicitDeny
aws iam get-account-password-policy
aws iam get-account-summary --query 'SummaryMap.AccountMFAEnabled'   # expect 1
```

**Cleanup:** Keep the role for Tasks 3-8 (removed by `~/teardown-core.sh`). Remove the password policy when you finish the course:

```bash
aws iam delete-account-password-policy
```

### Task 3: EC2 web server with Nginx and PM2 via user data

**Task:** Launch a t3.micro Amazon Linux 2023 instance in the default VPC with IMDSv2 required, the lab instance profile, no SSH port open, and tags `Name=lab-web`, `backup=daily`. User data must install Nginx and Node.js, run a small app under PM2 on 127.0.0.1:3000 (with a `/health` route), make PM2 start at boot, and proxy port 80 to it.

**Solution:**

```bash
source ~/lab.env
cat > ~/app.sh <<'EOF'
#!/bin/bash
set -euxo pipefail
dnf install -y nginx nodejs npm
npm install -g pm2
mkdir -p /opt/app
cat > /opt/app/server.js <<'JS'
const http = require('http');
const os = require('os');
http.createServer((req, res) => {
  if (req.url === '/health') { res.end('ok\n'); return; }
  res.end(`hello from ${os.hostname()}\n`);
}).listen(3000, '127.0.0.1');
JS
export HOME=/root
pm2 start /opt/app/server.js --name app
pm2 startup systemd -u root --hp /root
pm2 save
cat > /etc/nginx/conf.d/app.conf <<'NG'
server {
    listen 80;
    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
NG
nginx -t
systemctl enable --now nginx
EOF

VPC=$(aws ec2 describe-vpcs --filters Name=is-default,Values=true \
  --query 'Vpcs[0].VpcId' --output text)
SG=$(aws ec2 create-security-group --group-name lab-web-sg \
  --description "lab web" --vpc-id "$VPC" --query GroupId --output text)
aws ec2 authorize-security-group-ingress --group-id "$SG" \
  --protocol tcp --port 80 --cidr 0.0.0.0/0
AMI=$(aws ssm get-parameter \
  --name /aws/service/ami-amazon-linux-latest/al2023-ami-kernel-default-x86_64 \
  --query Parameter.Value --output text)
IID=$(aws ec2 run-instances --image-id "$AMI" --instance-type t3.micro \
  --subnet-id "$(aws ec2 describe-subnets --filters Name=vpc-id,Values=$VPC \
     Name=availability-zone,Values=us-east-1a --query 'Subnets[0].SubnetId' \
     --output text)" \
  --security-group-ids "$SG" --iam-instance-profile Name=lab-ec2-profile \
  --metadata-options HttpTokens=required,HttpEndpoint=enabled \
  --user-data file://$HOME/app.sh \
  --tag-specifications \
  'ResourceType=instance,Tags=[{Key=Name,Value=lab-web},{Key=backup,Value=daily}]' \
  --query 'Instances[0].InstanceId' --output text)
aws ec2 wait instance-status-ok --instance-ids "$IID"
echo "export VPC=$VPC SG=$SG IID=$IID AMI=$AMI" >> ~/lab.env
```

The Nginx server block is placed in `conf.d`, which Amazon Linux's `nginx.conf` includes before its own default server, so it answers port 80 first.

**Verify:**

```bash
source ~/lab.env
PUBIP=$(aws ec2 describe-instances --instance-ids "$IID" \
  --query 'Reservations[0].Instances[0].PublicIpAddress' --output text)
echo "export PUBIP=$PUBIP" >> ~/lab.env
curl -s "http://$PUBIP/"          # hello from ip-172-...
curl -s "http://$PUBIP/health"    # ok
aws ec2 describe-instances --instance-ids "$IID" \
  --query 'Reservations[0].Instances[0].MetadataOptions.HttpTokens'  # required
```

**Cleanup:** Keep `lab-web` for Tasks 4-8, 13, 14. At the end of a session either stop it (`aws ec2 stop-instances --instance-ids "$IID"`; the public IP changes on start, so rerun the PUBIP lines) or run `~/teardown-core.sh`.

### Task 4: CloudWatch agent for memory, disk, Nginx and PM2 logs

**Task:** Using Systems Manager (no SSH), install the CloudWatch agent on `lab-web`. Store its configuration in Parameter Store. Collect `mem_used_percent` and root disk `used_percent`, ship the Nginx access log and PM2 logs to log groups with 7-day retention, then create a metric filter that counts HTTP 5xx responses.

**Solution:**

```bash
source ~/lab.env
cat > cwagent.json <<'EOF'
{
 "agent": {"metrics_collection_interval": 60, "run_as_user": "root"},
 "metrics": {
  "append_dimensions": {"InstanceId": "${aws:InstanceId}"},
  "metrics_collected": {
   "mem": {"measurement": ["mem_used_percent"]},
   "disk": {"measurement": ["used_percent"], "resources": ["/"]}
  }
 },
 "logs": {"logs_collected": {"files": {"collect_list": [
  {"file_path": "/var/log/nginx/access.log", "log_group_name": "/lab/nginx/access",
   "log_stream_name": "{instance_id}", "retention_in_days": 7},
  {"file_path": "/root/.pm2/logs/app-error.log", "log_group_name": "/lab/pm2/error",
   "log_stream_name": "{instance_id}", "retention_in_days": 7},
  {"file_path": "/root/.pm2/logs/app-out.log", "log_group_name": "/lab/pm2/out",
   "log_stream_name": "{instance_id}", "retention_in_days": 7}
 ]}}}
}
EOF
aws ssm put-parameter --name AmazonCloudWatch-lab-web --type String \
  --value file://cwagent.json --overwrite
cat > cmd.json <<'EOF'
{"commands":[
 "dnf install -y amazon-cloudwatch-agent",
 "CTL=/opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl",
 "$CTL -a fetch-config -m ec2 -s -c ssm:AmazonCloudWatch-lab-web",
 "$CTL -a status"
]}
EOF
CID=$(aws ssm send-command --instance-ids "$IID" \
  --document-name AWS-RunShellScript --parameters file://cmd.json \
  --query Command.CommandId --output text)
aws ssm wait command-executed --command-id "$CID" --instance-id "$IID"

aws logs put-metric-filter --log-group-name /lab/nginx/access \
  --filter-name nginx-5xx \
  --filter-pattern '[ip, ident, user, ts, request, status=5*, bytes, ref, ua, xff]' \
  --metric-transformations \
  metricName=Nginx5xx,metricNamespace=Lab/Web,metricValue=1,defaultValue=0
```

The parameter name starts with `AmazonCloudWatch-` because the managed `CloudWatchAgentServerPolicy` only allows reading parameters with that prefix. The filter pattern matches the 10 space-delimited fields of the default Nginx "main" log format; quoted and bracketed values count as one field each.

**Verify:**

```bash
aws ssm get-command-invocation --command-id "$CID" --instance-id "$IID" \
  --query '[Status,StandardOutputContent]' --output text
aws cloudwatch list-metrics --namespace CWAgent --metric-name mem_used_percent \
  --query 'Metrics[].Dimensions'
aws logs test-metric-filter \
  --filter-pattern '[ip, ident, user, ts, request, status=5*, bytes, ref, ua, xff]' \
  --log-event-messages \
  '1.2.3.4 - - [28/Sep/2026:10:00:00 +0000] "GET / HTTP/1.1" 502 157 "-" "curl" "-"'
for i in $(seq 5); do curl -s -o /dev/null "http://$PUBIP/"; done
sleep 60
aws logs tail /lab/nginx/access --since 10m | tail -3
```

**Cleanup:** Keep the agent and log groups for Tasks 5 and 8. The core teardown deletes the log groups and parameter. To remove only the filter:

```bash
aws logs delete-metric-filter --log-group-name /lab/nginx/access --filter-name nginx-5xx
```

### Task 5: Alarms, SNS, automatic recovery and a composite alarm

**Task:** Create an SNS topic that emails you. Create alarms for: CPU above 70% for 10 minutes, memory above 80% (from the agent), and a system status check failure that triggers EC2 recovery. Create a composite alarm that only notifies when CPU and memory are both in ALARM. Test the notification path without stressing the box.

**Solution:**

```bash
source ~/lab.env
TOPIC=$(aws sns create-topic --name lab-alerts --query TopicArn --output text)
aws sns subscribe --topic-arn "$TOPIC" --protocol email \
  --notification-endpoint "$EMAIL"      # confirm the email you receive
echo "export TOPIC=$TOPIC" >> ~/lab.env

aws cloudwatch put-metric-alarm --alarm-name lab-web-cpu-high \
  --namespace AWS/EC2 --metric-name CPUUtilization \
  --dimensions Name=InstanceId,Value="$IID" --statistic Average \
  --period 300 --evaluation-periods 2 --threshold 70 \
  --comparison-operator GreaterThanThreshold

aws cloudwatch put-metric-alarm --alarm-name lab-web-mem-high \
  --namespace CWAgent --metric-name mem_used_percent \
  --dimensions Name=InstanceId,Value="$IID" --statistic Average \
  --period 60 --evaluation-periods 5 --threshold 80 \
  --comparison-operator GreaterThanThreshold

aws cloudwatch put-metric-alarm --alarm-name lab-web-sys-check \
  --namespace AWS/EC2 --metric-name StatusCheckFailed_System \
  --dimensions Name=InstanceId,Value="$IID" --statistic Maximum \
  --period 60 --evaluation-periods 2 --threshold 0 \
  --comparison-operator GreaterThanThreshold \
  --alarm-actions "arn:aws:automate:$AWS_REGION:ec2:recover" "$TOPIC"

aws cloudwatch put-composite-alarm --alarm-name lab-web-degraded \
  --alarm-rule 'ALARM("lab-web-cpu-high") AND ALARM("lab-web-mem-high")' \
  --alarm-actions "$TOPIC"
```

The CPU and memory alarms have no actions on purpose: the composite alarm is the only one that pages you, which is the standard noise-reduction pattern.

**Verify:**

```bash
aws cloudwatch set-alarm-state --alarm-name lab-web-sys-check \
  --state-value ALARM --state-reason "notification test"
# the email arrives; the recover action is not run by a manual state change
aws cloudwatch describe-alarms --alarm-name-prefix lab-web \
  --query 'MetricAlarms[].[AlarmName,StateValue]' --output table
aws cloudwatch describe-alarms --alarm-types CompositeAlarm \
  --query 'CompositeAlarms[].[AlarmName,StateValue,AlarmRule]'
```

The alarm returns to OK at the next evaluation.

**Cleanup:**

```bash
aws cloudwatch delete-alarms --alarm-names lab-web-degraded
aws cloudwatch delete-alarms --alarm-names lab-web-cpu-high lab-web-mem-high \
  lab-web-sys-check
```

Keep the SNS topic for Tasks 8 and 13 (core teardown deletes it). Delete the composite alarm first, because a metric alarm referenced by a composite alarm cannot be deleted.

### Task 6: Session Manager, Run Command and Parameter Store

**Task:** Open a shell on `lab-web` with no port 22 and no key pair. Use Run Command, targeting by tag, to check Nginx and PM2 status. Store a database URL as a SecureString parameter and have the app read it at start through PM2.

**Solution:**

```bash
source ~/lab.env
aws ssm describe-instance-information \
  --query 'InstanceInformationList[].[InstanceId,PingStatus,PlatformName]'
aws ssm start-session --target "$IID"
# inside the session:
#   sudo -i
#   pm2 ls; systemctl status nginx --no-pager; tail -20 /var/log/cloud-init-output.log
#   exit; exit

cat > status.json <<'EOF'
{"commands":["systemctl is-active nginx","export HOME=/root","pm2 jlist | head -c 300"]}
EOF
CID=$(aws ssm send-command --targets Key=tag:Name,Values=lab-web \
  --document-name AWS-RunShellScript --parameters file://status.json \
  --query Command.CommandId --output text)

aws ssm put-parameter --name /lab/app/DB_URL --type SecureString \
  --value "mysql://app:not-a-real-pass@db.internal:3306/app"
cat > env.json <<'EOF'
{"commands":[
 "export HOME=/root",
 "P=/lab/app/DB_URL",
 "Q='--with-decryption --query Parameter.Value --output text'",
 "export DB_URL=$(aws ssm get-parameter --name $P $Q)",
 "pm2 restart app --update-env",
 "pm2 env 0 | grep -c DB_URL"
]}
EOF
CID2=$(aws ssm send-command --instance-ids "$IID" \
  --document-name AWS-RunShellScript --parameters file://env.json \
  --query Command.CommandId --output text)
```

The instance can decrypt because `AmazonSSMManagedInstanceCore` allows `ssm:GetParameter` and the AWS managed `aws/ssm` key is usable by principals in the account through SSM. With a customer managed key you would also need `kms:Decrypt` on that key.

**Verify:**

```bash
aws ssm list-command-invocations --command-id "$CID" --details \
  --query 'CommandInvocations[].CommandPlugins[].Output' --output text
aws ssm get-command-invocation --command-id "$CID2" --instance-id "$IID" \
  --query '[Status,StandardOutputContent]' --output text   # Success, 1
aws ec2 describe-security-groups --group-ids "$SG" \
  --query 'SecurityGroups[0].IpPermissions[].FromPort'     # only 80
```

**Cleanup:**

```bash
aws ssm delete-parameter --name /lab/app/DB_URL
```

### Task 7: Patch Manager, a maintenance window and an Automation runbook

**Task:** Scan `lab-web` for missing patches. Create a weekly maintenance window (Sunday 03:00 UTC, 2 hours) that installs patches on instances tagged `Name=lab-web`. Write a custom Automation runbook that restarts the PM2 app and checks `/health`, then run it and the AWS-managed `AWS-RestartEC2Instance` runbook.

**Solution:**

```bash
source ~/lab.env
aws ssm send-command --document-name AWS-RunPatchBaseline \
  --targets Key=tag:Name,Values=lab-web --parameters Operation=Scan

MW=$(aws ssm create-maintenance-window --name lab-patching \
  --schedule "cron(0 3 ? * SUN *)" --duration 2 --cutoff 1 \
  --no-allow-unassociated-targets --query WindowId --output text)
MWT=$(aws ssm register-target-with-maintenance-window --window-id "$MW" \
  --resource-type INSTANCE --targets Key=tag:Name,Values=lab-web \
  --query WindowTargetId --output text)
aws ssm register-task-with-maintenance-window --window-id "$MW" \
  --task-arn AWS-RunPatchBaseline --task-type RUN_COMMAND \
  --targets Key=WindowTargetIds,Values="$MWT" \
  --max-concurrency 1 --max-errors 1 \
  --task-invocation-parameters \
  '{"RunCommand":{"Parameters":{"Operation":["Install"]}}}'
echo "export MW=$MW" >> ~/lab.env

cat > restart-app.yaml <<'EOF'
schemaVersion: '0.3'
description: Restart the PM2 app and check health
parameters:
  InstanceId:
    type: String
mainSteps:
  - name: restartApp
    action: aws:runCommand
    inputs:
      DocumentName: AWS-RunShellScript
      InstanceIds:
        - '{{ InstanceId }}'
      Parameters:
        commands:
          - export HOME=/root
          - pm2 restart app
          - sleep 3
          - curl -fsS http://127.0.0.1/health
EOF
aws ssm create-document --name Lab-RestartPm2App --document-type Automation \
  --document-format YAML --content file://restart-app.yaml
EX=$(aws ssm start-automation-execution --document-name Lab-RestartPm2App \
  --parameters InstanceId="$IID" --query AutomationExecutionId --output text)
```

**Verify:**

```bash
aws ssm describe-instance-patch-states --instance-ids "$IID" \
  --query 'InstancePatchStates[0].[MissingCount,InstalledCount,Operation]'
aws ssm describe-maintenance-window-tasks --window-id "$MW" \
  --query 'Tasks[].[TaskArn,Type]'
sleep 30
aws ssm get-automation-execution --automation-execution-id "$EX" \
  --query 'AutomationExecution.AutomationExecutionStatus'     # Success
EX2=$(aws ssm start-automation-execution --document-name AWS-RestartEC2Instance \
  --parameters InstanceId="$IID" --query AutomationExecutionId --output text)
aws ssm get-automation-execution --automation-execution-id "$EX2" \
  --query 'AutomationExecution.StepExecutions[].[StepName,StepStatus]'
```

After the reboot, `curl http://$PUBIP/` should work again without intervention; that proves `pm2 startup` did its job.

**Cleanup:**

```bash
aws ssm delete-maintenance-window --window-id "$MW"
aws ssm delete-document --name Lab-RestartPm2App
```

### Task 8: Self-healing with CloudWatch, EventBridge and Run Command

**Task:** When the Nginx 5xx count reaches 5 in one minute, alarm to SNS and, through an EventBridge rule, automatically run `pm2 restart app` on the tagged instance. Prove it by stopping the app and generating 502s.

**Solution:**

```bash
source ~/lab.env
aws cloudwatch put-metric-alarm --alarm-name lab-web-5xx \
  --namespace Lab/Web --metric-name Nginx5xx --statistic Sum \
  --period 60 --evaluation-periods 1 --threshold 5 \
  --comparison-operator GreaterThanOrEqualToThreshold \
  --treat-missing-data notBreaching --alarm-actions "$TOPIC"

cat > events-trust.json <<'EOF'
{"Version":"2012-10-17","Statement":[{"Effect":"Allow",
 "Principal":{"Service":"events.amazonaws.com"},"Action":"sts:AssumeRole"}]}
EOF
cat > events-ssm.json <<EOF
{"Version":"2012-10-17","Statement":[{"Effect":"Allow","Action":"ssm:SendCommand",
 "Resource":["arn:aws:ssm:$AWS_REGION::document/AWS-RunShellScript",
             "arn:aws:ec2:$AWS_REGION:$ACCOUNT_ID:instance/*"]}]}
EOF
aws iam create-role --role-name lab-events-ssm \
  --assume-role-policy-document file://events-trust.json
aws iam put-role-policy --role-name lab-events-ssm --policy-name send-command \
  --policy-document file://events-ssm.json

cat > pattern.json <<'EOF'
{"source":["aws.cloudwatch"],
 "detail-type":["CloudWatch Alarm State Change"],
 "detail":{"alarmName":["lab-web-5xx"],"state":{"value":["ALARM"]}}}
EOF
aws events put-rule --name lab-restart-on-5xx --event-pattern file://pattern.json
cat > targets.json <<EOF
[{"Id":"restart-app",
  "Arn":"arn:aws:ssm:$AWS_REGION::document/AWS-RunShellScript",
  "RoleArn":"arn:aws:iam::$ACCOUNT_ID:role/lab-events-ssm",
  "Input":"{\"commands\":[\"export HOME=/root\",\"pm2 restart app\"]}",
  "RunCommandParameters":{"RunCommandTargets":[
    {"Key":"tag:Name","Values":["lab-web"]}]}}]
EOF
aws events put-targets --rule lab-restart-on-5xx --targets file://targets.json
```

**Verify:**

```bash
aws ssm send-command --instance-ids "$IID" --document-name AWS-RunShellScript \
  --parameters 'commands=["export HOME=/root","pm2 stop app"]'
sleep 5
for i in $(seq 20); do curl -s -o /dev/null -w "%{http_code}\n" "http://$PUBIP/"; done
# wait 2-4 minutes for log delivery, metric and alarm evaluation
aws cloudwatch describe-alarms --alarm-names lab-web-5xx \
  --query 'MetricAlarms[0].StateValue'
aws ssm list-commands --max-results 3 \
  --query 'Commands[].[RequestedDateTime,DocumentName,Status]' --output table
curl -s "http://$PUBIP/"     # hello again, restarted by the rule
```

**Cleanup:**

```bash
aws events remove-targets --rule lab-restart-on-5xx --ids restart-app
aws events delete-rule --name lab-restart-on-5xx
aws iam delete-role-policy --role-name lab-events-ssm --policy-name send-command
aws iam delete-role --role-name lab-events-ssm
aws cloudwatch delete-alarms --alarm-names lab-web-5xx
```

### Task 9: EBS volume: attach, mount, grow online, snapshot

**Task:** Add a 1 GiB gp3 data volume to `lab-web`, format it XFS, mount it persistently at `/data`, then grow it to 2 GiB without downtime and snapshot it.

**Solution:**

```bash
source ~/lab.env
AZ=$(aws ec2 describe-instances --instance-ids "$IID" \
  --query 'Reservations[0].Instances[0].Placement.AvailabilityZone' --output text)
VOL=$(aws ec2 create-volume --availability-zone "$AZ" --size 1 --volume-type gp3 \
  --tag-specifications 'ResourceType=volume,Tags=[{Key=Name,Value=lab-data}]' \
  --query VolumeId --output text)
aws ec2 wait volume-available --volume-ids "$VOL"
aws ec2 attach-volume --volume-id "$VOL" --instance-id "$IID" --device /dev/sdf
echo "export AZ=$AZ VOL=$VOL" >> ~/lab.env
aws ssm start-session --target "$IID"
```

Inside the session (Nitro instances expose EBS as NVMe; match the serial to the volume ID):

```bash
sudo -i
lsblk -o NAME,SIZE,SERIAL          # e.g. nvme1n1  1G  vol0abc...
mkfs.xfs /dev/nvme1n1
mkdir -p /data
UUID=$(blkid -s UUID -o value /dev/nvme1n1)
echo "UUID=$UUID /data xfs defaults,nofail 0 2" >> /etc/fstab
mount -a && df -h /data
```

Back in CloudShell, grow it, then grow the filesystem in the session:

```bash
aws ec2 modify-volume --volume-id "$VOL" --size 2
aws ec2 describe-volumes-modifications --volume-ids "$VOL" \
  --query 'VolumesModifications[0].ModificationState'   # optimizing or completed
# in the session:  xfs_growfs /data && df -h /data
SNAP=$(aws ec2 create-snapshot --volume-id "$VOL" --description lab-data \
  --query SnapshotId --output text)
aws ec2 wait snapshot-completed --snapshot-ids "$SNAP"
echo "export SNAP=$SNAP" >> ~/lab.env
```

`nofail` keeps the instance bootable if the volume is missing. After a modification, the same volume cannot be modified again for 6 hours.

**Verify:**

```bash
aws ec2 describe-volumes --volume-ids "$VOL" \
  --query 'Volumes[0].[Size,VolumeType,Iops,Throughput,State]'   # 2 gp3 3000 125
aws ec2 describe-snapshots --snapshot-ids "$SNAP" --query 'Snapshots[0].State'
# in the session: df -h /data shows about 2.0G
```

**Cleanup:** In the session run `umount /data` and delete the `/data` line from `/etc/fstab` (`sed -i '\#/data xfs#d' /etc/fstab`). Then:

```bash
aws ec2 detach-volume --volume-id "$VOL"
aws ec2 wait volume-available --volume-ids "$VOL"
aws ec2 delete-volume --volume-id "$VOL"
aws ec2 delete-snapshot --snapshot-id "$SNAP"
```

### Task 10: Golden AMI, launch template, ALB and Auto Scaling

**Task:** Bake an AMI from `lab-web` (PM2 and Nginx already configured). Put 2 instances from a launch template behind an Application Load Balancer across two AZs, using ELB health checks on `/health`, a 120-second grace period and a target-tracking policy at 50% CPU. Prove self-healing by killing an instance.

**Solution:**

```bash
source ~/lab.env
GOLD=$(aws ec2 create-image --instance-id "$IID" --name "lab-web-$(date +%Y%m%d%H%M)" \
  --query ImageId --output text)
aws ec2 wait image-available --image-ids "$GOLD"
cat > lt.json <<EOF
{"ImageId":"$GOLD","InstanceType":"t3.micro",
 "IamInstanceProfile":{"Name":"lab-ec2-profile"},
 "SecurityGroupIds":["$SG"],
 "MetadataOptions":{"HttpTokens":"required"},
 "TagSpecifications":[{"ResourceType":"instance",
   "Tags":[{"Key":"Name","Value":"lab-asg"}]}]}
EOF
aws ec2 create-launch-template --launch-template-name lab-web-lt \
  --launch-template-data file://lt.json
SUBNETS=$(aws ec2 describe-subnets --filters Name=vpc-id,Values="$VPC" \
  Name=availability-zone,Values=us-east-1a,us-east-1b \
  --query 'Subnets[].SubnetId' --output text)
ALB_ARN=$(aws elbv2 create-load-balancer --name lab-alb --subnets $SUBNETS \
  --security-groups "$SG" --query 'LoadBalancers[0].LoadBalancerArn' --output text)
TG_ARN=$(aws elbv2 create-target-group --name lab-tg --protocol HTTP --port 80 \
  --vpc-id "$VPC" --health-check-path /health --health-check-interval-seconds 10 \
  --healthy-threshold-count 2 --query 'TargetGroups[0].TargetGroupArn' --output text)
aws elbv2 create-listener --load-balancer-arn "$ALB_ARN" --protocol HTTP --port 80 \
  --default-actions Type=forward,TargetGroupArn="$TG_ARN"
aws autoscaling create-auto-scaling-group --auto-scaling-group-name lab-asg \
  --launch-template 'LaunchTemplateName=lab-web-lt,Version=$Latest' \
  --min-size 1 --max-size 3 --desired-capacity 2 \
  --vpc-zone-identifier "$(echo $SUBNETS | tr ' ' ',')" \
  --target-group-arns "$TG_ARN" --health-check-type ELB \
  --health-check-grace-period 120
cat > tt.json <<'EOF'
{"PredefinedMetricSpecification":{"PredefinedMetricType":"ASGAverageCPUUtilization"},
 "TargetValue":50}
EOF
aws autoscaling put-scaling-policy --auto-scaling-group-name lab-asg \
  --policy-name cpu50 --policy-type TargetTrackingScaling \
  --target-tracking-configuration file://tt.json
echo "export GOLD=$GOLD ALB_ARN=$ALB_ARN TG_ARN=$TG_ARN" >> ~/lab.env
```

For the lab the ALB and instances share `lab-web-sg`. In production give the ALB its own security group and allow port 80 on the instances only from that group.

**Verify:**

```bash
DNS=$(aws elbv2 describe-load-balancers --load-balancer-arns "$ALB_ARN" \
  --query 'LoadBalancers[0].DNSName' --output text)
aws elbv2 describe-target-health --target-group-arn "$TG_ARN" \
  --query 'TargetHealthDescriptions[].[Target.Id,TargetHealth.State]'
for i in $(seq 6); do curl -s "http://$DNS/"; done   # two different hostnames
VICTIM=$(aws autoscaling describe-auto-scaling-groups \
  --auto-scaling-group-names lab-asg \
  --query 'AutoScalingGroups[0].Instances[0].InstanceId' --output text)
aws ec2 terminate-instances --instance-ids "$VICTIM"
sleep 120
aws autoscaling describe-scaling-activities --auto-scaling-group-name lab-asg \
  --max-items 3 --query 'Activities[].[StatusCode,Description]'
```

**Cleanup:** Run it within 2 hours; the ALB bills hourly.

```bash
source ~/lab.env
aws autoscaling delete-auto-scaling-group --auto-scaling-group-name lab-asg \
  --force-delete
aws elbv2 delete-load-balancer --load-balancer-arn "$ALB_ARN"
aws elbv2 wait load-balancers-deleted --load-balancer-arns "$ALB_ARN"
aws ec2 wait instance-terminated --filters Name=tag:Name,Values=lab-asg
aws elbv2 delete-target-group --target-group-arn "$TG_ARN"
aws ec2 delete-launch-template --launch-template-name lab-web-lt
SNAPS=$(aws ec2 describe-images --image-ids "$GOLD" \
  --query 'Images[0].BlockDeviceMappings[].Ebs.SnapshotId' --output text)
aws ec2 deregister-image --image-id "$GOLD"
for s in $SNAPS; do aws ec2 delete-snapshot --snapshot-id "$s"; done
```

### Task 11: S3 versioning, lifecycle and encryption for log archives

**Task:** Create a private bucket for rotated Nginx and PM2 logs. Enable versioning, confirm Block Public Access and default encryption, and add a lifecycle rule for `logs/`: Standard-IA at 30 days, Glacier Instant Retrieval at 90, delete at 365, expire noncurrent versions after 30 days, abort incomplete multipart uploads after 7 days. Recover an accidentally deleted object.

**Solution:**

```bash
source ~/lab.env
B="lab-logs-$ACCOUNT_ID"
aws s3api create-bucket --bucket "$B"        # us-east-1 needs no location config
BPA=BlockPublicAcls=true,IgnorePublicAcls=true
BPA=$BPA,BlockPublicPolicy=true,RestrictPublicBuckets=true
aws s3api put-public-access-block --bucket "$B" \
  --public-access-block-configuration "$BPA"
aws s3api put-bucket-versioning --bucket "$B" \
  --versioning-configuration Status=Enabled
cat > lifecycle.json <<'EOF'
{"Rules":[{"ID":"logs-tiering","Status":"Enabled","Filter":{"Prefix":"logs/"},
  "Transitions":[{"Days":30,"StorageClass":"STANDARD_IA"},
                 {"Days":90,"StorageClass":"GLACIER_IR"}],
  "Expiration":{"Days":365},
  "NoncurrentVersionExpiration":{"NoncurrentDays":30},
  "AbortIncompleteMultipartUpload":{"DaysAfterInitiation":7}}]}
EOF
aws s3api put-bucket-lifecycle-configuration --bucket "$B" \
  --lifecycle-configuration file://lifecycle.json
echo "export B=$B" >> ~/lab.env

echo "GET / 200" > access-2026-09-28.log
aws s3 cp access-2026-09-28.log "s3://$B/logs/web/access-2026-09-28.log"
echo "GET / 502" >> access-2026-09-28.log
aws s3 cp access-2026-09-28.log "s3://$B/logs/web/access-2026-09-28.log"
aws s3 rm "s3://$B/logs/web/access-2026-09-28.log"      # "accident"
```

On a real server, a daily cron or a `postrotate` hook in logrotate would push the rotated file with `aws s3 cp`, using an instance role limited to `s3:PutObject` on `arn:aws:s3:::BUCKET/logs/*`.

**Verify and recover:**

```bash
aws s3api get-bucket-encryption --bucket "$B" \
  --query 'ServerSideEncryptionConfiguration.Rules[0].ApplyServerSideEncryptionByDefault'
aws s3api get-bucket-lifecycle-configuration --bucket "$B" --query 'Rules[0].ID'
aws s3api list-object-versions --bucket "$B" --prefix logs/web/ \
  --query '{v:Versions[].VersionId,d:DeleteMarkers[].VersionId}'
DM=$(aws s3api list-object-versions --bucket "$B" --prefix logs/web/ \
  --query 'DeleteMarkers[0].VersionId' --output text)
aws s3api delete-object --bucket "$B" --key logs/web/access-2026-09-28.log \
  --version-id "$DM"                                      # removes the marker
aws s3 cp "s3://$B/logs/web/access-2026-09-28.log" -     # object is back
```

**Cleanup:** A versioned bucket must have every version and delete marker removed first (or use Empty in the console).

```bash
aws s3api list-object-versions --bucket "$B" --output json \
  --query '{Objects: Versions[].{Key:Key,VersionId:VersionId}}' > v.json
aws s3api delete-objects --bucket "$B" --delete file://v.json
aws s3api list-object-versions --bucket "$B" --output json \
  --query '{Objects: DeleteMarkers[].{Key:Key,VersionId:VersionId}}' > m.json
aws s3api delete-objects --bucket "$B" --delete file://m.json 2>/dev/null
aws s3api delete-bucket --bucket "$B"
```

### Task 12: Event-driven processing: S3 upload triggers Lambda

**Task:** When an object is created under `uploads/` in a bucket, invoke a Python Lambda function that logs the bucket, key and size as JSON.

**Solution:**

```bash
source ~/lab.env
EB="lab-events-$ACCOUNT_ID"
aws s3api create-bucket --bucket "$EB"
cat > lambda-trust.json <<'EOF'
{"Version":"2012-10-17","Statement":[{"Effect":"Allow",
 "Principal":{"Service":"lambda.amazonaws.com"},"Action":"sts:AssumeRole"}]}
EOF
aws iam create-role --role-name lab-lambda-s3 \
  --assume-role-policy-document file://lambda-trust.json
aws iam attach-role-policy --role-name lab-lambda-s3 --policy-arn \
  arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole
cat > app.py <<'EOF'
import json
import urllib.parse

def handler(event, context):
    for r in event["Records"]:
        key = urllib.parse.unquote_plus(r["s3"]["object"]["key"])
        print(json.dumps({"bucket": r["s3"]["bucket"]["name"],
                          "key": key, "size": r["s3"]["object"].get("size", 0)}))
    return {"ok": True}
EOF
zip -q fn.zip app.py
sleep 10     # let the new role propagate
FN_ARN=$(aws lambda create-function --function-name lab-s3-events \
  --runtime python3.13 --handler app.handler --zip-file fileb://fn.zip \
  --role "arn:aws:iam::$ACCOUNT_ID:role/lab-lambda-s3" \
  --query FunctionArn --output text)
aws lambda wait function-active-v2 --function-name lab-s3-events
aws lambda add-permission --function-name lab-s3-events --statement-id s3invoke \
  --action lambda:InvokeFunction --principal s3.amazonaws.com \
  --source-arn "arn:aws:s3:::$EB" --source-account "$ACCOUNT_ID"
cat > notif-s3.json <<EOF
{"LambdaFunctionConfigurations":[{"LambdaFunctionArn":"$FN_ARN",
  "Events":["s3:ObjectCreated:*"],
  "Filter":{"Key":{"FilterRules":[{"Name":"prefix","Value":"uploads/"}]}}}]}
EOF
aws s3api put-bucket-notification-configuration --bucket "$EB" \
  --notification-configuration file://notif-s3.json
echo "export EB=$EB" >> ~/lab.env
```

**Verify:**

```bash
echo hi > test.txt
aws s3 cp test.txt "s3://$EB/uploads/test.txt"
aws s3 cp test.txt "s3://$EB/other/test.txt"      # must NOT trigger
sleep 15
aws logs tail /aws/lambda/lab-s3-events --since 5m | grep '"key"'
```

**Cleanup:**

```bash
aws s3 rm "s3://$EB" --recursive
aws s3api delete-bucket --bucket "$EB"
aws lambda delete-function --function-name lab-s3-events
aws logs delete-log-group --log-group-name /aws/lambda/lab-s3-events
aws iam detach-role-policy --role-name lab-lambda-s3 --policy-arn \
  arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole
aws iam delete-role --role-name lab-lambda-s3
```

### Task 13: Route 53 health check with a CloudWatch alarm

**Task:** Create an HTTP health check for `http://PUBLIC_IP/health` every 30 seconds with a failure threshold of 3. Alarm to SNS when it reports unhealthy. Break Nginx and watch it fail. Optionally, if you own a domain, wire failover routing.

**Solution:**

```bash
source ~/lab.env
HCC="IPAddress=$PUBIP,Port=80,Type=HTTP,ResourcePath=/health"
HCC="$HCC,RequestInterval=30,FailureThreshold=3"
HC=$(aws route53 create-health-check --caller-reference "lab-$(date +%s)" \
  --health-check-config "$HCC" \
  --query HealthCheck.Id --output text)
aws route53 change-tags-for-resource --resource-type healthcheck \
  --resource-id "$HC" --add-tags Key=Name,Value=lab-web
aws cloudwatch put-metric-alarm --alarm-name lab-web-r53 \
  --namespace AWS/Route53 --metric-name HealthCheckStatus \
  --dimensions Name=HealthCheckId,Value="$HC" --statistic Minimum \
  --period 60 --evaluation-periods 1 --threshold 1 \
  --comparison-operator LessThanThreshold --alarm-actions "$TOPIC"
echo "export HC=$HC" >> ~/lab.env
```

Route 53 health-check metrics are only published in us-east-1, so the alarm and its SNS topic must be there. The health checkers come from public Route 53 IP ranges; the security group must allow them (here port 80 is open to all).

Optional failover (needs a hosted zone you own; about 0.50 USD/month): create a PRIMARY record pointing to the instance with `HealthCheckId` set, and a SECONDARY record pointing to, for example, a static "maintenance" S3 website or another instance.

```json
{"Changes":[{"Action":"UPSERT","ResourceRecordSet":{
  "Name":"app.example.com","Type":"A","SetIdentifier":"primary",
  "Failover":"PRIMARY","TTL":60,"HealthCheckId":"HC_ID",
  "ResourceRecords":[{"Value":"PUBLIC_IP"}]}}]}
```

**Verify:**

```bash
aws route53 get-health-check-status --health-check-id "$HC" \
  --query 'HealthCheckObservations[].StatusReport.Status' | head -5
aws ssm send-command --instance-ids "$IID" --document-name AWS-RunShellScript \
  --parameters 'commands=["systemctl stop nginx"]'
sleep 180
aws cloudwatch describe-alarms --alarm-names lab-web-r53 \
  --query 'MetricAlarms[0].StateValue'          # ALARM, email received
aws ssm send-command --instance-ids "$IID" --document-name AWS-RunShellScript \
  --parameters 'commands=["systemctl start nginx"]'
```

**Cleanup:**

```bash
aws cloudwatch delete-alarms --alarm-names lab-web-r53
aws route53 delete-health-check --health-check-id "$HC"
```

### Task 14: AWS Backup plan and a tested restore

**Task:** Create a backup vault and a daily plan (05:00 UTC, 7-day retention) that selects resources tagged `backup=daily`. Run an on-demand backup of the `lab-web` root volume and restore it to a new volume.

**Solution:**

```bash
source ~/lab.env
cat > backup-trust.json <<'EOF'
{"Version":"2012-10-17","Statement":[{"Effect":"Allow",
 "Principal":{"Service":"backup.amazonaws.com"},"Action":"sts:AssumeRole"}]}
EOF
aws iam create-role --role-name lab-backup-role \
  --assume-role-policy-document file://backup-trust.json
for p in AWSBackupServiceRolePolicyForBackup AWSBackupServiceRolePolicyForRestores; do
  aws iam attach-role-policy --role-name lab-backup-role \
    --policy-arn "arn:aws:iam::aws:policy/service-role/$p"
done
BROLE="arn:aws:iam::$ACCOUNT_ID:role/lab-backup-role"
aws backup create-backup-vault --backup-vault-name lab-vault
cat > plan.json <<'EOF'
{"BackupPlanName":"lab-daily",
 "Rules":[{"RuleName":"daily-7d","TargetBackupVaultName":"lab-vault",
   "ScheduleExpression":"cron(0 5 ? * * *)","StartWindowMinutes":60,
   "Lifecycle":{"DeleteAfterDays":7}}]}
EOF
PLAN=$(aws backup create-backup-plan --backup-plan file://plan.json \
  --query BackupPlanId --output text)
cat > selection.json <<EOF
{"SelectionName":"tag-backup-daily","IamRoleArn":"$BROLE",
 "ListOfTags":[{"ConditionType":"STRINGEQUALS","ConditionKey":"backup",
   "ConditionValue":"daily"}]}
EOF
aws backup create-backup-selection --backup-plan-id "$PLAN" \
  --backup-selection file://selection.json
ROOTVOL=$(aws ec2 describe-instances --instance-ids "$IID" --query \
  'Reservations[0].Instances[0].BlockDeviceMappings[0].Ebs.VolumeId' --output text)
JOB=$(aws backup start-backup-job --backup-vault-name lab-vault \
  --resource-arn "arn:aws:ec2:$AWS_REGION:$ACCOUNT_ID:volume/$ROOTVOL" \
  --iam-role-arn "$BROLE" --lifecycle DeleteAfterDays=7 \
  --query BackupJobId --output text)
echo "export BROLE=$BROLE PLAN=$PLAN JOB=$JOB" >> ~/lab.env
```

Wait until the job is COMPLETED (a few minutes), then restore:

```bash
aws backup describe-backup-job --backup-job-id "$JOB" --query State
RP=$(aws backup describe-backup-job --backup-job-id "$JOB" \
  --query RecoveryPointArn --output text)
aws backup get-recovery-point-restore-metadata --backup-vault-name lab-vault \
  --recovery-point-arn "$RP" --query RestoreMetadata > meta.json
cat meta.json
# if there is no availabilityZone key, add "availabilityZone":"us-east-1a"
RJ=$(aws backup start-restore-job --recovery-point-arn "$RP" \
  --iam-role-arn "$BROLE" --metadata file://meta.json \
  --query RestoreJobId --output text)
echo "export RP=$RP RJ=$RJ" >> ~/lab.env
```

**Verify:**

```bash
aws backup list-protected-resources --query 'Results[].ResourceArn'
aws backup describe-restore-job --restore-job-id "$RJ" \
  --query '[Status,CreatedResourceArn]'          # COMPLETED, arn:...:volume/vol-...
aws backup list-backup-selections --backup-plan-id "$PLAN"
```

**Cleanup:**

```bash
NEWVOL=$(aws backup describe-restore-job --restore-job-id "$RJ" \
  --query CreatedResourceArn --output text | awk -F/ '{print $NF}')
aws ec2 delete-volume --volume-id "$NEWVOL"
SEL=$(aws backup list-backup-selections --backup-plan-id "$PLAN" \
  --query 'BackupSelectionsList[0].SelectionId' --output text)
aws backup delete-backup-selection --backup-plan-id "$PLAN" --selection-id "$SEL"
aws backup delete-backup-plan --backup-plan-id "$PLAN"
for rp in $(aws backup list-recovery-points-by-backup-vault \
    --backup-vault-name lab-vault \
    --query 'RecoveryPoints[].RecoveryPointArn' --output text); do
  aws backup delete-recovery-point --backup-vault-name lab-vault \
    --recovery-point-arn "$rp"
done
sleep 30
aws backup delete-backup-vault --backup-vault-name lab-vault
for p in AWSBackupServiceRolePolicyForBackup AWSBackupServiceRolePolicyForRestores; do
  aws iam detach-role-policy --role-name lab-backup-role \
    --policy-arn "arn:aws:iam::aws:policy/service-role/$p"
done
aws iam delete-role --role-name lab-backup-role
```

### Task 15: CloudFormation stack, change set and drift detection

**Task:** Deploy a stack with a security group and an EC2 instance whose AMI comes from the public SSM parameter. Preview a change of instance type with a change set, execute it, then create drift by hand and detect it.

**Solution:**

```bash
source ~/lab.env
cat > web.yaml <<'EOF'
AWSTemplateFormatVersion: '2010-09-09'
Description: Lab web server
Parameters:
  InstanceType:
    Type: String
    Default: t3.micro
    AllowedValues: [t3.micro, t3.small]
  LatestAmi:
    Type: AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>
    Default: /aws/service/ami-amazon-linux-latest/al2023-ami-kernel-default-x86_64
Resources:
  WebSG:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: cfn lab web
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: 80
          ToPort: 80
          CidrIp: 0.0.0.0/0
  Web:
    Type: AWS::EC2::Instance
    Properties:
      ImageId: !Ref LatestAmi
      InstanceType: !Ref InstanceType
      SecurityGroupIds: [!GetAtt WebSG.GroupId]
      IamInstanceProfile: lab-ec2-profile
      UserData: !Base64 |
        #!/bin/bash
        dnf install -y nginx
        systemctl enable --now nginx
      Tags:
        - Key: Name
          Value: lab-cfn-web
Outputs:
  PublicIp:
    Value: !GetAtt Web.PublicIp
  SecurityGroupId:
    Value: !GetAtt WebSG.GroupId
EOF
aws cloudformation validate-template --template-body file://web.yaml
aws cloudformation deploy --stack-name lab-cfn --template-file web.yaml
aws cloudformation create-change-set --stack-name lab-cfn --change-set-name to-small \
  --use-previous-template --parameters ParameterKey=InstanceType,ParameterValue=t3.small \
  ParameterKey=LatestAmi,UsePreviousValue=true
aws cloudformation wait change-set-create-complete --stack-name lab-cfn \
  --change-set-name to-small
aws cloudformation describe-change-set --stack-name lab-cfn --change-set-name to-small \
  --query 'Changes[].ResourceChange.[LogicalResourceId,Action,Replacement]'
aws cloudformation execute-change-set --stack-name lab-cfn --change-set-name to-small
aws cloudformation wait stack-update-complete --stack-name lab-cfn
CSG=$(aws cloudformation describe-stacks --stack-name lab-cfn \
  --query "Stacks[0].Outputs[?OutputKey=='SecurityGroupId'].OutputValue" --output text)
aws ec2 authorize-security-group-ingress --group-id "$CSG" \
  --protocol tcp --port 22 --cidr 0.0.0.0/0          # manual change = drift
DID=$(aws cloudformation detect-stack-drift --stack-name lab-cfn \
  --query StackDriftDetectionId --output text)
```

The change set shows `Modify` with `Replacement: False` for the instance: changing the instance type on an EBS-backed instance is an update with some interruption (stop and start), not a replacement.

**Verify:**

```bash
aws cloudformation describe-stack-drift-detection-status \
  --stack-drift-detection-id "$DID" --query '[DetectionStatus,StackDriftStatus]'
aws cloudformation describe-stack-resource-drifts --stack-name lab-cfn \
  --query 'StackResourceDrifts[].[LogicalResourceId,StackResourceDriftStatus]'
# WebSG MODIFIED, Web IN_SYNC
CIP=$(aws cloudformation describe-stacks --stack-name lab-cfn \
  --query "Stacks[0].Outputs[?OutputKey=='PublicIp'].OutputValue" --output text)
curl -s "http://$CIP/" | head -3
```

**Cleanup:**

```bash
aws cloudformation delete-stack --stack-name lab-cfn
aws cloudformation wait stack-delete-complete --stack-name lab-cfn
```

### Task 16: Build a VPC, add an S3 gateway endpoint, troubleshoot with flow logs

**Task:** Build `10.20.0.0/16` with two public subnets in different AZs, an internet gateway, a route table and an S3 gateway endpoint (no NAT gateway). Launch the Nginx/PM2 instance there, enable VPC flow logs to CloudWatch Logs, then block your own IP with a network ACL and find the REJECT records.

**Solution:**

```bash
source ~/lab.env
V=$(aws ec2 create-vpc --cidr-block 10.20.0.0/16 --tag-specifications \
  'ResourceType=vpc,Tags=[{Key=Name,Value=lab-vpc}]' --query Vpc.VpcId --output text)
aws ec2 modify-vpc-attribute --vpc-id "$V" --enable-dns-hostnames Value=true
SUBA=$(aws ec2 create-subnet --vpc-id "$V" --cidr-block 10.20.1.0/24 \
  --availability-zone us-east-1a --query Subnet.SubnetId --output text)
SUBB=$(aws ec2 create-subnet --vpc-id "$V" --cidr-block 10.20.2.0/24 \
  --availability-zone us-east-1b --query Subnet.SubnetId --output text)
IGW=$(aws ec2 create-internet-gateway \
  --query InternetGateway.InternetGatewayId --output text)
aws ec2 attach-internet-gateway --internet-gateway-id "$IGW" --vpc-id "$V"
RT=$(aws ec2 create-route-table --vpc-id "$V" --query RouteTable.RouteTableId \
  --output text)
aws ec2 create-route --route-table-id "$RT" --destination-cidr-block 0.0.0.0/0 \
  --gateway-id "$IGW"
aws ec2 associate-route-table --route-table-id "$RT" --subnet-id "$SUBA"
aws ec2 associate-route-table --route-table-id "$RT" --subnet-id "$SUBB"
aws ec2 modify-subnet-attribute --subnet-id "$SUBA" --map-public-ip-on-launch
S3EP=$(aws ec2 create-vpc-endpoint --vpc-id "$V" --vpc-endpoint-type Gateway \
  --service-name "com.amazonaws.$AWS_REGION.s3" --route-table-ids "$RT" \
  --query VpcEndpoint.VpcEndpointId --output text)
VSG=$(aws ec2 create-security-group --group-name lab-vpc-web --description "vpc web" \
  --vpc-id "$V" --query GroupId --output text)
aws ec2 authorize-security-group-ingress --group-id "$VSG" --protocol tcp --port 80 \
  --cidr 0.0.0.0/0
VIID=$(aws ec2 run-instances --image-id "$AMI" --instance-type t3.micro \
  --subnet-id "$SUBA" --security-group-ids "$VSG" \
  --iam-instance-profile Name=lab-ec2-profile \
  --metadata-options HttpTokens=required --user-data file://$HOME/app.sh \
  --query 'Instances[0].InstanceId' --output text)
cat > fl-trust.json <<'EOF'
{"Version":"2012-10-17","Statement":[{"Effect":"Allow",
 "Principal":{"Service":"vpc-flow-logs.amazonaws.com"},"Action":"sts:AssumeRole"}]}
EOF
cat > fl-policy.json <<'EOF'
{"Version":"2012-10-17","Statement":[{"Effect":"Allow","Resource":"*",
 "Action":["logs:CreateLogGroup","logs:CreateLogStream","logs:PutLogEvents",
           "logs:DescribeLogGroups","logs:DescribeLogStreams"]}]}
EOF
aws iam create-role --role-name lab-flowlogs \
  --assume-role-policy-document file://fl-trust.json
aws iam put-role-policy --role-name lab-flowlogs --policy-name write-logs \
  --policy-document file://fl-policy.json
sleep 10
FL=$(aws ec2 create-flow-logs --resource-type VPC --resource-ids "$V" \
  --traffic-type ALL --log-destination-type cloud-watch-logs \
  --log-group-name /lab/vpc/flow --max-aggregation-interval 60 \
  --deliver-logs-permission-arn "arn:aws:iam::$ACCOUNT_ID:role/lab-flowlogs" \
  --query 'FlowLogIds[0]' --output text)
cat >> ~/lab.env <<EOF
export V=$V SUBA=$SUBA SUBB=$SUBB IGW=$IGW RT=$RT S3EP=$S3EP VSG=$VSG
export VIID=$VIID FL=$FL
EOF
aws ec2 wait instance-status-ok --instance-ids "$VIID"
VIP=$(aws ec2 describe-instances --instance-ids "$VIID" \
  --query 'Reservations[0].Instances[0].PublicIpAddress' --output text)
curl -s "http://$VIP/"                        # works

MYIP=$(curl -s https://checkip.amazonaws.com)
NACL=$(aws ec2 create-network-acl --vpc-id "$V" --query NetworkAcl.NetworkAclId \
  --output text)
aws ec2 create-network-acl-entry --network-acl-id "$NACL" --ingress --rule-number 90 \
  --protocol tcp --port-range From=80,To=80 --cidr-block "$MYIP/32" --rule-action deny
aws ec2 create-network-acl-entry --network-acl-id "$NACL" --ingress --rule-number 100 \
  --protocol -1 --cidr-block 0.0.0.0/0 --rule-action allow
aws ec2 create-network-acl-entry --network-acl-id "$NACL" --egress --rule-number 100 \
  --protocol -1 --cidr-block 0.0.0.0/0 --rule-action allow
ASSOC=$(aws ec2 describe-network-acls \
  --filters Name=association.subnet-id,Values="$SUBA" \
  --query "NetworkAcls[0].Associations[?SubnetId=='$SUBA'].NetworkAclAssociationId" \
  --output text)
aws ec2 replace-network-acl-association --association-id "$ASSOC" --network-acl-id "$NACL"
echo "export NACL=$NACL VIP=$VIP" >> ~/lab.env
```

**Verify:**

```bash
curl -s -m 5 "http://$VIP/" || echo "blocked by NACL"
sleep 120
QID=$(aws logs start-query --log-group-name /lab/vpc/flow \
  --start-time $(date -d '-15 min' +%s) --end-time $(date +%s) \
  --query-string 'fields @timestamp, srcAddr, dstPort, action
    | filter action = "REJECT" and dstPort = 80 | limit 10' \
  --query queryId --output text)
sleep 10
aws logs get-query-results --query-id "$QID" --query 'results[][].value' | head -20
aws ec2 describe-route-tables --route-table-ids "$RT" \
  --query 'RouteTables[0].Routes[].[DestinationCidrBlock,DestinationPrefixListId,
    GatewayId]'
```

You should see your IP with `REJECT` on port 80, and a route to the S3 prefix list (`pl-...`) via the `vpce-...` endpoint.

**Cleanup:**

```bash
source ~/lab.env
aws ec2 terminate-instances --instance-ids "$VIID"
aws ec2 wait instance-terminated --instance-ids "$VIID"
aws ec2 delete-flow-logs --flow-log-ids "$FL"
aws logs delete-log-group --log-group-name /lab/vpc/flow
aws ec2 delete-security-group --group-id "$VSG"
aws ec2 delete-vpc-endpoints --vpc-endpoint-ids "$S3EP"
aws ec2 delete-subnet --subnet-id "$SUBA"
aws ec2 delete-subnet --subnet-id "$SUBB"
aws ec2 delete-network-acl --network-acl-id "$NACL"
aws ec2 delete-route-table --route-table-id "$RT"
aws ec2 detach-internet-gateway --internet-gateway-id "$IGW" --vpc-id "$V"
aws ec2 delete-internet-gateway --internet-gateway-id "$IGW"
aws ec2 delete-vpc --vpc-id "$V"
aws iam delete-role-policy --role-name lab-flowlogs --policy-name write-logs
aws iam delete-role --role-name lab-flowlogs
```

### Task 17: CloudFront with a private S3 origin, caching and invalidation

**Task:** Serve `index.html` from a private S3 bucket through CloudFront using Origin Access Control, HTTPS redirect and the managed CachingOptimized policy. Show a cache hit, deploy a new version, and fix the stale content with an invalidation.

**Solution:**

```bash
source ~/lab.env
SB="lab-site-$ACCOUNT_ID"
aws s3api create-bucket --bucket "$SB"
echo "<h1>v1</h1>" > index.html
aws s3 cp index.html "s3://$SB/index.html" --content-type text/html
OACC=Name=lab-oac,SigningProtocol=sigv4,SigningBehavior=always
OACC=$OACC,OriginAccessControlOriginType=s3
OAC=$(aws cloudfront create-origin-access-control \
  --origin-access-control-config "$OACC" \
  --query OriginAccessControl.Id --output text)
cat > dist.json <<EOF
{"CallerReference":"lab-$(date +%s)","Comment":"lab","Enabled":true,
 "DefaultRootObject":"index.html",
 "Origins":{"Quantity":1,"Items":[{"Id":"s3site",
   "DomainName":"$SB.s3.$AWS_REGION.amazonaws.com",
   "S3OriginConfig":{"OriginAccessIdentity":""},"OriginAccessControlId":"$OAC"}]},
 "DefaultCacheBehavior":{"TargetOriginId":"s3site",
   "ViewerProtocolPolicy":"redirect-to-https",
   "CachePolicyId":"658327ea-f89d-4fab-a63d-7e88639e58f6"}}
EOF
DIST=$(aws cloudfront create-distribution --distribution-config file://dist.json \
  --query Distribution.Id --output text)
cat > site-policy.json <<EOF
{"Version":"2012-10-17","Statement":[{"Sid":"CloudFrontOnly","Effect":"Allow",
 "Principal":{"Service":"cloudfront.amazonaws.com"},"Action":"s3:GetObject",
 "Resource":"arn:aws:s3:::$SB/*",
 "Condition":{"StringEquals":
   {"AWS:SourceArn":"arn:aws:cloudfront::$ACCOUNT_ID:distribution/$DIST"}}}]}
EOF
aws s3api put-bucket-policy --bucket "$SB" --policy file://site-policy.json
aws cloudfront wait distribution-deployed --id "$DIST"
echo "export SB=$SB OAC=$OAC DIST=$DIST" >> ~/lab.env
```

**Verify:**

```bash
CF=$(aws cloudfront get-distribution --id "$DIST" \
  --query Distribution.DomainName --output text)
curl -sI "https://$CF/" | grep -i x-cache      # Miss from cloudfront
curl -sI "https://$CF/" | grep -i x-cache      # Hit from cloudfront
curl -s -o /dev/null -w "%{http_code}\n" \
  "https://$SB.s3.amazonaws.com/index.html"     # 403: bucket not public
echo "<h1>v2</h1>" > index.html
aws s3 cp index.html "s3://$SB/index.html" --content-type text/html
curl -s "https://$CF/"                           # still v1 (cached)
INV=$(aws cloudfront create-invalidation --distribution-id "$DIST" \
  --paths "/index.html" "/" --query Invalidation.Id --output text)
aws cloudfront wait invalidation-completed --distribution-id "$DIST" --id "$INV"
curl -s "https://$CF/"                           # v2
```

**Cleanup:** A distribution must be disabled and fully deployed before it can be deleted.

```bash
aws cloudfront get-distribution-config --id "$DIST" > dc.json
ETAG=$(jq -r .ETag dc.json)
jq '.DistributionConfig.Enabled=false | .DistributionConfig' dc.json > dc2.json
aws cloudfront update-distribution --id "$DIST" --if-match "$ETAG" \
  --distribution-config file://dc2.json
aws cloudfront wait distribution-deployed --id "$DIST"
ETAG=$(aws cloudfront get-distribution --id "$DIST" --query ETag --output text)
aws cloudfront delete-distribution --id "$DIST" --if-match "$ETAG"
OETAG=$(aws cloudfront get-origin-access-control --id "$OAC" --query ETag --output text)
aws cloudfront delete-origin-access-control --id "$OAC" --if-match "$OETAG"
aws s3 rm "s3://$SB" --recursive && aws s3api delete-bucket --bucket "$SB"
```

### Task 18: KMS customer managed key for EBS, with rotation

**Task:** Create a customer managed KMS key with alias `alias/lab-ebs` and annual rotation. Create an EBS volume encrypted with it, encrypt and decrypt a small file, and read the key policy to see who can use the key.

**Solution:**

```bash
source ~/lab.env
KEY=$(aws kms create-key --description "lab ebs key" --query KeyMetadata.KeyId \
  --output text)
aws kms create-alias --alias-name alias/lab-ebs --target-key-id "$KEY"
aws kms enable-key-rotation --key-id "$KEY"
EVOL=$(aws ec2 create-volume --availability-zone us-east-1a --size 1 \
  --volume-type gp3 --encrypted --kms-key-id alias/lab-ebs \
  --query VolumeId --output text)
echo -n "hello-kms" > plain.txt
aws kms encrypt --key-id alias/lab-ebs --plaintext fileb://plain.txt \
  --query CiphertextBlob --output text | base64 -d > secret.bin
echo "export KEY=$KEY EVOL=$EVOL" >> ~/lab.env
```

**Verify:**

```bash
aws ec2 describe-volumes --volume-ids "$EVOL" --query 'Volumes[0].[Encrypted,KmsKeyId]'
aws kms get-key-rotation-status --key-id "$KEY"             # KeyRotationEnabled: true
aws kms decrypt --ciphertext-blob fileb://secret.bin --query Plaintext \
  --output text | base64 -d; echo                           # hello-kms
aws kms get-key-policy --key-id "$KEY" --policy-name default --output text | head -20
```

The default key policy trusts the account root, which delegates access control to IAM policies. Anyone launching an instance from an AMI encrypted with this key needs `kms:Decrypt`, `kms:CreateGrant` and related permissions on it.

**Cleanup:**

```bash
aws ec2 wait volume-available --volume-ids "$EVOL"
aws ec2 delete-volume --volume-id "$EVOL"
aws kms delete-alias --alias-name alias/lab-ebs
aws kms schedule-key-deletion --key-id "$KEY" --pending-window-in-days 7
```

### Task 19: CloudTrail, IAM Access Analyzer and an AWS Config rule

**Task:** Find who opened port 22 in Task 15 using CloudTrail event history. Create an account-level Access Analyzer and trigger a finding with a role trusted by an external account. Record only S3 buckets in AWS Config, add the managed rule that checks bucket versioning, and read the compliance result.

**Solution:**

```bash
source ~/lab.env
aws cloudtrail lookup-events --max-results 5 \
  --lookup-attributes \
  AttributeKey=EventName,AttributeValue=AuthorizeSecurityGroupIngress \
  --query 'Events[].[EventTime,Username,EventName]' --output table

aws accessanalyzer create-analyzer --analyzer-name lab-analyzer --type ACCOUNT
cat > ext-trust.json <<'EOF'
{"Version":"2012-10-17","Statement":[{"Effect":"Allow",
 "Principal":{"AWS":"arn:aws:iam::111122223333:root"},"Action":"sts:AssumeRole"}]}
EOF
aws iam create-role --role-name lab-external-trust \
  --assume-role-policy-document file://ext-trust.json

CB="lab-config-$ACCOUNT_ID"
aws s3api create-bucket --bucket "$CB"
cat > cfg-bucket.json <<EOF
{"Version":"2012-10-17","Statement":[
 {"Sid":"AclCheck","Effect":"Allow","Principal":{"Service":"config.amazonaws.com"},
  "Action":["s3:GetBucketAcl","s3:ListBucket"],"Resource":"arn:aws:s3:::$CB",
  "Condition":{"StringEquals":{"AWS:SourceAccount":"$ACCOUNT_ID"}}},
 {"Sid":"Write","Effect":"Allow","Principal":{"Service":"config.amazonaws.com"},
  "Action":"s3:PutObject","Resource":"arn:aws:s3:::$CB/AWSLogs/$ACCOUNT_ID/Config/*",
  "Condition":{"StringEquals":{"s3:x-amz-acl":"bucket-owner-full-control",
   "AWS:SourceAccount":"$ACCOUNT_ID"}}}]}
EOF
aws s3api put-bucket-policy --bucket "$CB" --policy file://cfg-bucket.json
aws iam create-service-linked-role --aws-service-name config.amazonaws.com 2>/dev/null
SLR="arn:aws:iam::$ACCOUNT_ID:role/aws-service-role/config.amazonaws.com"
SLR="$SLR/AWSServiceRoleForConfig"
aws configservice put-configuration-recorder --configuration-recorder \
  "name=default,roleARN=$SLR" --recording-group \
  "allSupported=false,includeGlobalResourceTypes=false,resourceTypes=AWS::S3::Bucket"
aws configservice put-delivery-channel --delivery-channel "name=default,s3BucketName=$CB"
aws configservice start-configuration-recorder --configuration-recorder-name default
cat > rule.json <<'EOF'
{"ConfigRuleName":"s3-versioning-enabled",
 "Source":{"Owner":"AWS","SourceIdentifier":"S3_BUCKET_VERSIONING_ENABLED"},
 "Scope":{"ComplianceResourceTypes":["AWS::S3::Bucket"]}}
EOF
aws configservice put-config-rule --config-rule file://rule.json
echo "export CB=$CB" >> ~/lab.env
```

**Verify:**

```bash
aws accessanalyzer list-findings --analyzer-arn "$(aws accessanalyzer get-analyzer \
  --analyzer-name lab-analyzer --query analyzer.arn --output text)" \
  --query 'findings[].[resourceType,resource,status]'
aws configservice describe-configuration-recorder-status \
  --query 'ConfigurationRecordersStatus[0].[recording,lastStatus]'
sleep 120
aws configservice get-compliance-details-by-config-rule \
  --config-rule-name s3-versioning-enabled \
  --query 'EvaluationResults[].[
    EvaluationResultIdentifier.EvaluationResultQualifier.ResourceId,ComplianceType]'
```

The config bucket shows NON_COMPLIANT (no versioning). In the console, Config can attach the `AWS-ConfigureS3BucketVersioning` SSM runbook as an automatic remediation. Trusted Advisor's free core security checks are in the console under Trusted Advisor; read them once.

**Cleanup:**

```bash
aws configservice delete-config-rule --config-rule-name s3-versioning-enabled
aws configservice stop-configuration-recorder --configuration-recorder-name default
aws configservice delete-delivery-channel --delivery-channel-name default
aws configservice delete-configuration-recorder --configuration-recorder-name default
aws s3 rm "s3://$CB" --recursive && aws s3api delete-bucket --bucket "$CB"
aws iam delete-role --role-name lab-external-trust
aws accessanalyzer delete-analyzer --analyzer-name lab-analyzer
```

### Task 20: RDS backups and point-in-time restore

**Task:** Create a single-AZ MySQL `db.t4g.micro` instance, not publicly accessible, with 1-day automated backups and the master password managed in Secrets Manager. Take a manual snapshot, then restore the database to the latest restorable time as a new instance.

**Solution:**

```bash
source ~/lab.env
aws rds create-db-instance --db-instance-identifier lab-db --engine mysql \
  --db-instance-class db.t4g.micro --allocated-storage 20 --storage-type gp3 \
  --master-username admin --manage-master-user-password \
  --backup-retention-period 1 --no-multi-az --no-publicly-accessible \
  --no-deletion-protection
aws rds wait db-instance-available --db-instance-identifier lab-db   # 10-15 min
aws rds create-db-snapshot --db-instance-identifier lab-db \
  --db-snapshot-identifier lab-db-manual-1
aws rds wait db-snapshot-available --db-snapshot-identifier lab-db-manual-1
aws rds restore-db-instance-to-point-in-time \
  --source-db-instance-identifier lab-db --target-db-instance-identifier lab-db-pitr \
  --use-latest-restorable-time --db-instance-class db.t4g.micro --no-multi-az \
  --no-publicly-accessible
aws rds wait db-instance-available --db-instance-identifier lab-db-pitr
```

A restore always creates a new instance with a new endpoint; the application's connection string (or a Route 53 CNAME in front of it) must be switched.

**Verify:**

```bash
aws rds describe-db-instances --db-instance-identifier lab-db \
  --query 'DBInstances[0].[DBInstanceStatus,LatestRestorableTime,
    MasterUserSecret.SecretArn]'
aws rds describe-db-instances --db-instance-identifier lab-db-pitr \
  --query 'DBInstances[0].[DBInstanceStatus,Endpoint.Address]'
aws cloudwatch get-metric-statistics --namespace AWS/RDS --metric-name FreeStorageSpace \
  --dimensions Name=DBInstanceIdentifier,Value=lab-db --statistics Minimum \
  --start-time "$(date -u -d '-30 min' +%FT%TZ)" --end-time "$(date -u +%FT%TZ)" \
  --period 300
```

**Cleanup:** Same day.

```bash
for db in lab-db-pitr lab-db; do
  aws rds delete-db-instance --db-instance-identifier "$db" \
    --skip-final-snapshot --delete-automated-backups
done
aws rds delete-db-snapshot --db-snapshot-identifier lab-db-manual-1
aws rds wait db-instance-deleted --db-instance-identifier lab-db
```

Finally, when you are done for the day: `~/teardown-core.sh`, then check Cost Explorer.

## Practice questions

All questions are original. Where it says "Choose TWO", exactly two options are correct.

1. A Node.js service on EC2 is slow. CPUUtilization is 20%, but you suspect memory pressure. The AWS/EC2 namespace has no memory metric. What is the most operationally efficient fix? A) Enable detailed monitoring. B) Install the CloudWatch agent and collect `mem_used_percent`. C) Write a cron job that calls `put-metric-data` with `free -m` output. D) Enable VPC flow logs.

2. You must alarm when Nginx returns more than 20 HTTP 5xx responses in 5 minutes. Access logs already flow to CloudWatch Logs. What should you create? A) A CloudWatch Logs Insights saved query. B) A metric filter on the log group, then an alarm on the new metric. C) A subscription filter to Lambda that sends email. D) An EventBridge rule on the log group.

3. An alarm on a custom error-count metric keeps showing INSUFFICIENT_DATA overnight because the metric is only published when errors occur. The team wants it to show OK. What change is best? A) Increase the evaluation periods. B) Set treat missing data to notBreaching (or give the metric filter a default value of 0). C) Switch the statistic to Maximum. D) Use a composite alarm.

4. On-call is paged every time CPU spikes during nightly builds, which is harmless unless latency also rises. How do you page only when both happen? A) Raise the CPU threshold to 95%. B) Create a composite alarm with `ALARM(cpu) AND ALARM(latency)` and move notifications to it. C) Use anomaly detection on CPU. D) Disable the CPU alarm at night with a Lambda function.

5. An EBS-backed EC2 instance must recover automatically from underlying host hardware failure while keeping its instance ID, private IP and Elastic IP. What do you configure? A) An Auto Scaling group of size 1. B) A CloudWatch alarm on `StatusCheckFailed_System` with the EC2 recover action. C) A CloudWatch alarm on `StatusCheckFailed_Instance` with the reboot action. D) A Route 53 health check.

6. You need to run `pm2 restart app` on 40 instances tagged `Role=api`, with no SSH, and keep the output for audit. What should you use? A) EC2 Instance Connect. B) Systems Manager Run Command targeting the tag, with output sent to S3 or CloudWatch Logs. C) A user data script. D) CloudFormation cfn-hup.

7. Security wants port 22 closed on all servers, with an interactive shell still available and sessions logged. Which TWO are required for Systems Manager Session Manager? (Choose TWO.) A) An instance profile with `AmazonSSMManagedInstanceCore`. B) An inbound security group rule on port 443. C) A running SSM Agent that can reach the Systems Manager endpoints. D) A key pair. E) An Elastic IP.

8. Instances in private subnets with no NAT gateway and no internet access never appear in Fleet Manager. The instance profile is correct. What fixes it? A) Add an S3 gateway endpoint only. B) Create interface VPC endpoints for `ssm`, `ssmmessages` and `ec2messages` with private DNS enabled. C) Attach an Elastic IP to each instance. D) Open inbound port 443 from 0.0.0.0/0.

9. Behind an ALB, some Auto Scaling instances return HTTP 500 for every request because the app process died, but Auto Scaling never replaces them. What change is needed? A) Increase desired capacity. B) Set the Auto Scaling group health check type to ELB. C) Enable cross-zone load balancing. D) Enable deletion protection on the ALB.

10. New Auto Scaling instances are terminated as unhealthy before `npm install` and PM2 start finish in user data (about 4 minutes), creating a replace loop. What is the simplest fix? A) Change the health check path to `/`. B) Increase the health check grace period beyond the boot time, or bake dependencies into the AMI. C) Switch to a Network Load Balancer. D) Use a larger instance type.

11. Traffic to an API ramps up and down unpredictably and you want average CPU across the group to stay near 50% with the least configuration. Which scaling policy? A) Simple scaling with two alarms. B) Step scaling. C) Target tracking on `ASGAverageCPUUtilization` = 50. D) Scheduled actions.

12. A reporting app has a guaranteed load spike every weekday at 09:00 and instances take 5 minutes to become healthy. How do you avoid slow responses at 09:00? A) Target tracking only. B) A scheduled action that raises minimum capacity at 08:45 (predictive scaling is another valid option). C) Increase the ALB idle timeout. D) Enable detailed monitoring.

13. ALB access logs show `elb_status_code` 504 with `target_status_code` "-" for long report requests that take 90 seconds. What is the likely cause and fix? A) Targets are unhealthy; fix the health check. B) The request exceeded the ALB idle timeout (60 seconds by default); raise it or make the job asynchronous. C) The security group blocks the ALB. D) The target group uses the wrong port.

14. After a deploy, the ALB returns HTTP 503 for every request. What is the most likely cause? A) The listener certificate expired. B) The target group has no registered or healthy targets. C) The ALB is out of capacity. D) WAF blocked the requests.

15. A Route 53 failover setup never fails over, even though the primary server is down. What is the most likely misconfiguration? A) The TTL is 60 seconds. B) The primary record has no health check associated (or, for an alias, Evaluate Target Health is off). C) The secondary record has a health check. D) The hosted zone is public.

16. A Route 53 health check against an EC2 web server always reports unhealthy, but the site loads fine from your laptop. What should you check first? A) The instance's IAM role. B) Whether the security group and NACL allow the Route 53 health checker IP ranges on the health-check port. C) Whether the EC2 instance has detailed monitoring. D) Whether the hosted zone has DNSSEC.

17. You want to send 10% of users to a new application version by DNS and increase gradually. Which routing policy? A) Latency. B) Failover. C) Weighted. D) Geolocation.

18. A versioned S3 bucket that stores daily log uploads keeps growing even though an expiration rule deletes objects after 90 days. Which TWO lifecycle actions fix it? (Choose TWO.) A) NoncurrentVersionExpiration. B) Transition to S3 One Zone-IA. C) AbortIncompleteMultipartUpload. D) Enable Requester Pays. E) Enable Transfer Acceleration.

19. A developer deleted `config/prod.json` from a versioned bucket. How do you restore it with the least effort? A) Restore from AWS Backup. B) Delete the delete marker for that key. C) Copy the object from CloudTrail. D) Re-enable versioning.

20. Users in Asia upload 2 GB video files to a bucket in us-east-1 and uploads are slow and sometimes fail. Which TWO changes help most? (Choose TWO.) A) Multipart upload. B) S3 Transfer Acceleration. C) S3 Object Lock. D) Glacier Instant Retrieval. E) Cross-Region Replication to us-west-2.

21. A bad migration corrupted an RDS MySQL table at 14:32. Automated backups are enabled with 7-day retention. The business needs data as of 14:30. What do you do? A) Restore the latest automated snapshot in place. B) Point-in-time restore to 14:30 into a new DB instance, then repoint the application. C) Promote a read replica. D) Reboot with failover.

22. What does RDS Multi-AZ (one standby) primarily provide compared with a read replica? A) Read scaling. B) Automatic failover to a synchronous standby in another AZ. C) Cross-Region disaster recovery. D) Lower storage cost.

23. Compliance requires daily backups of all EC2 instances and EBS volumes tagged `backup=daily`, kept 35 days, with a copy in a second Region. What is the least operational effort? A) A Lambda function on a cron schedule calling `create-snapshot`. B) An AWS Backup plan with a tag-based selection, a 35-day lifecycle and a cross-Region copy action. C) Data Lifecycle Manager plus manual copies. D) S3 replication.

24. A gp2 volume on a database host hits its IOPS ceiling during peaks. You want more IOPS without buying a bigger disk and without downtime. What do you do? A) Detach and restore from snapshot as io2. B) Use Elastic Volumes to modify it to gp3 and set IOPS independently of size. C) Add an instance store. D) Enable EBS encryption.

25. After increasing an EBS root volume from 8 GiB to 20 GiB, `df -h /` still shows 8 GiB on the XFS root. Which commands complete the change? A) `mkfs.xfs` then reboot. B) `growpart /dev/nvme0n1 1` then `xfs_growfs /`. C) `resize2fs /dev/nvme0n1`. D) Nothing; wait for the volume to finish optimizing.

26. A CloudFormation stack contains the production RDS instance. The team wants to delete the stack later without losing the data. What should be in the template? A) A stack policy. B) `DeletionPolicy: Snapshot` (or `Retain`) on the DB resource. C) Termination protection on the EC2 instances. D) An Outputs section.

27. A stack is in `UPDATE_ROLLBACK_FAILED` because a resource was changed outside CloudFormation. What is the supported way forward? A) Delete the stack immediately. B) Fix the underlying issue, or run `continue-update-rollback` and skip the problem resources. C) Edit the template in S3. D) Create a change set.

28. You must deploy the same baseline IAM roles and Config rules to 12 accounts in 3 Regions and keep new accounts in sync automatically. What should you use? A) Nested stacks. B) CloudFormation StackSets with service-managed permissions through AWS Organizations. C) Copy the template manually. D) AWS RAM.

29. After deploying a new `app.js` to S3 behind CloudFront, users still receive the old file for hours. Which approach prevents this in future deploys with the least ongoing cost? A) Invalidate `/*` on every deploy. B) Use versioned (hashed) file names so each deploy changes the URL. C) Set the TTL to 0 for all content. D) Disable CloudFront.

30. A bucket serves a site through CloudFront, but people also read objects directly with S3 URLs. How do you force all access through CloudFront? A) Enable S3 static website hosting. B) Use Origin Access Control and a bucket policy that allows only the distribution's ARN, with Block Public Access on. C) Add a WAF rule to S3. D) Use presigned URLs.

31. Flow logs show inbound HTTP accepted, but response packets to clients are rejected at the subnet. The subnet uses a custom network ACL that allows inbound 80 and outbound 80 only. What is wrong? A) The security group is missing an outbound rule. B) NACLs are stateless; outbound ephemeral ports (1024-65535) must be allowed. C) The route table needs a NAT gateway. D) Flow logs are misconfigured.

32. You need to block one abusive IP address from reaching every instance in a subnet immediately. Which control can do it? A) A security group deny rule. B) A network ACL deny rule with a lower rule number than the allow rules. C) An IAM policy. D) A route to a blackhole.

33. Instances in a private subnet must download packages from the internet but must not be reachable from it. The private route table currently has only the local route. What do you add? A) An internet gateway route in the private route table. B) A NAT gateway in a public subnet and a `0.0.0.0/0` route to it from the private route table. C) An egress-only internet gateway for IPv4. D) A VPC peering connection.

34. Yesterday someone deleted a security group rule and the app went down. How do you find out who, with no prior setup? A) VPC flow logs. B) CloudTrail event history (the last 90 days of management events are available by default). C) AWS Config rules. D) CloudWatch metrics.

35. The organization must prevent anyone, including account admins, from creating resources outside `eu-west-1` and `us-east-1` in member accounts. What do you use? A) IAM permission boundaries in each account. B) A service control policy that denies actions when `aws:RequestedRegion` is not one of the two (with exceptions for global services). C) AWS Config rule only. D) A billing alarm.

36. You must continuously detect S3 buckets without versioning and fix them automatically. What is the best approach? A) A weekly Trusted Advisor report. B) The AWS Config managed rule for S3 versioning with an automatic remediation using an SSM Automation runbook. C) GuardDuty. D) Macie.

37. An application's database password must rotate automatically every 30 days with no code change beyond fetching the secret. Where should it be stored? A) Parameter Store String parameter. B) AWS Secrets Manager with rotation enabled. C) An environment variable in the PM2 ecosystem file. D) S3 with SSE-KMS.

38. A team shares an AMI whose snapshots are encrypted with a customer managed KMS key. Another account can see the AMI but launches fail. What is missing? A) The AMI must be made public. B) The key policy must grant the other account use of the key (for example `kms:Decrypt` and `kms:CreateGrant`), and that account's IAM must allow it. C) The instance type is wrong. D) EBS encryption by default must be off.

39. You request a public ACM certificate for a CloudFront distribution, but it does not appear in the distribution's certificate list. Why? A) ACM certificates cannot be used with CloudFront. B) The certificate must be requested in us-east-1 (N. Virginia) for CloudFront. C) DNS validation is not supported. D) The certificate needs to be imported.

40. An EventBridge rule matches the right events (its metrics show matched events) but its Lambda target is never invoked. What is the most likely cause? A) The event bus is full. B) The Lambda function lacks a resource-based policy allowing `events.amazonaws.com` to invoke it (or it is failing and invocations appear as FailedInvocations). C) EventBridge cannot target Lambda. D) The rule needs a schedule expression.

### Answers

1. B. Memory and disk usage are OS-level metrics; only the CloudWatch agent (or a custom publisher) collects them. Detailed monitoring just increases frequency of the same hypervisor metrics.
2. B. Metric filters turn matching log lines into a metric; alarms work on metrics, not on log queries.
3. B. Sparse metrics need a missing-data policy (notBreaching) or a filter default value of 0, so absence of errors reads as OK.
4. B. Composite alarms combine alarm states with AND/OR/NOT and are the standard way to cut noise.
5. B. The EC2 recover action for system status check failures migrates the instance to healthy hardware and keeps its ID, IPs and EBS volumes.
6. B. Run Command targets by tag, needs no SSH, and records output in S3 or CloudWatch Logs with CloudTrail auditing the call.
7. A and C. Session Manager needs the agent, the instance profile and outbound HTTPS to the endpoints; no inbound ports or key pairs.
8. B. Without internet access, the SSM Agent reaches Systems Manager through interface endpoints for ssm, ssmmessages and ec2messages.
9. B. With EC2 health checks only, Auto Scaling sees a running VM as healthy; the ELB health check type makes it act on failed target health.
10. B. The grace period stops health-check terminations during boot; baking the app into the AMI also shortens boot time.
11. C. Target tracking creates and manages the alarms and scales to hold the metric at the target value.
12. B. Known, recurring spikes are handled by scheduled actions (or predictive scaling) so capacity is warm before the load arrives.
13. B. An ALB 504 with no target status code means the target did not respond before the idle timeout; raise it or move long work to a queue.
14. B. An ALB returns 503 when the target group has no registered targets, or all targets are unhealthy and fail-open does not apply.
15. B. Failover depends on the primary record's health: a health check on non-alias records, or Evaluate Target Health on alias records.
16. B. Route 53 health checkers come from published AWS IP ranges; SGs or NACLs that only allow your IP make the check fail.
17. C. Weighted routing splits DNS responses by relative weights, which is the DNS canary pattern.
18. A and C. Expiration only adds delete markers in a versioned bucket; old versions need NoncurrentVersionExpiration, and failed multipart parts need AbortIncompleteMultipartUpload.
19. B. Deleting in a versioned bucket adds a delete marker; removing the marker makes the previous version current again.
20. A and B. Multipart uploads parallelize and retry parts; Transfer Acceleration routes uploads over the AWS edge network.
21. B. Point-in-time restore always creates a new instance at any second in the retention window; you then switch the endpoint.
22. B. Multi-AZ standby is for availability with automatic failover; read replicas are for read scaling (and can be promoted manually).
23. B. AWS Backup centralizes schedules, retention, tag-based selection and cross-Region copies without custom code.
24. B. Elastic Volumes changes type and performance online; gp3 decouples IOPS and throughput from size.
25. B. The partition must be grown first (`growpart`), then the filesystem (`xfs_growfs` for XFS; `resize2fs` is for ext4).
26. B. DeletionPolicy controls what happens to a resource when the stack or resource is deleted; Snapshot or Retain keeps the data.
27. B. `continue-update-rollback`, optionally with resources to skip, is the documented recovery from UPDATE_ROLLBACK_FAILED.
28. B. StackSets with service-managed permissions deploy across accounts and Regions and can auto-deploy to new accounts in an OU.
29. B. Versioned object names make each deploy a cache miss by design; invalidations work but cost money beyond the free allowance and are slower.
30. B. OAC signs origin requests; the bucket policy allows only that distribution, and Block Public Access removes direct access.
31. B. NACLs are stateless, so return traffic to client ephemeral ports needs an explicit outbound allow.
32. B. Only NACLs support explicit deny; rules are evaluated in number order, so the deny needs a lower number than the allow.
33. B. Private subnets reach the internet outbound through a NAT gateway in a public subnet; egress-only IGWs are for IPv6 only.
34. B. CloudTrail event history keeps 90 days of management events in every account at no charge, including who called RevokeSecurityGroupIngress.
35. B. SCPs set the maximum permissions for member accounts, including admins; `aws:RequestedRegion` restricts Regions.
36. B. Config evaluates continuously and can trigger an SSM Automation runbook to remediate non-compliant resources.
37. B. Secrets Manager provides managed rotation; Parameter Store SecureString has no built-in rotation.
38. B. Encrypted AMI sharing requires sharing the KMS key through its key policy plus IAM permissions in the target account.
39. B. CloudFront only uses ACM certificates from us-east-1, whatever Region the origin is in.
40. B. For Lambda targets, EventBridge needs a resource-based permission on the function; check FailedInvocations to confirm.

## Exam-day tips

Delivery rules (from the AWS certification policy pages):

- Book through your AWS Certification account (Pearson VUE). You can reschedule or cancel up to 24 hours before the appointment, and reschedule at most twice. Inside 24 hours or no-show, the fee is lost.
- If English is not your first language, request the ESL accommodation (30 extra minutes) once in your AWS Certification account before you register. It then applies to every future exam. Do this before booking.
- ID: online proctoring needs one valid, unexpired government-issued primary ID with photo and signature, in Roman characters. Test centers need two IDs (two primary, or one primary and one secondary). The first and last name must match your certification account exactly.
- Test center: arrive 15-30 minutes early.
- Online: you can launch the exam up to 30 minutes early; more than 15 minutes late and you forfeit the fee. Run the Pearson OnVUE system test on the same computer and network beforehand, clear the desk and room, and use a single monitor.
- Online: you may not leave the camera view or stand up for any reason, including restroom breaks. Plan for 130 minutes (160 with ESL) plus check-in.
- No reference material: no notes, docs, phone or console. This is a pure recall and judgment exam.

Time management:

- 65 questions in 130 minutes is 2 minutes each. First pass: answer everything, flag anything over 90 seconds. Second pass: flagged items only.
- Never leave a blank. There is no penalty for guessing, and 15 unknown questions are unscored anyway.
- Multiple-response questions state how many to pick; read that number twice.

Common traps:

- "Most operationally efficient" or "least effort" means the managed service (AWS Backup, target tracking, Run Command, Config remediation) beats a custom Lambda or cron job.
- Security group vs NACL: SGs are stateful and allow-only; NACLs are stateless, ordered, and can deny.
- Detailed monitoring does not add memory or disk metrics; only the CloudWatch agent does.
- Region-bound facts: billing metrics, Route 53 health-check metrics and CloudFront ACM certificates are in us-east-1.
- Versioned buckets: expiration creates delete markers; you need noncurrent version rules to actually free space.
- Restores (RDS PITR, snapshots) create new resources with new endpoints or IDs.
- Auto Scaling ignores app failures unless the health check type is ELB.
- Parameter Store vs Secrets Manager: rotation points to Secrets Manager.
- NAT gateway (IPv4, in a public subnet) vs egress-only internet gateway (IPv6).
- Retake: if you fail, wait 14 days. After passing, you cannot retake the same exam version for 2 years.

## Readiness checklist

- [ ] I created the lab account myself, root has MFA, and daily work uses a non-root admin identity
- [ ] Task 1 budget exists with credits excluded, and I get the alert emails
- [ ] I can launch an IMDSv2-only instance with user data that runs Nginx and PM2 and survives reboot
- [ ] I can install and configure the CloudWatch agent from Parameter Store without SSH
- [ ] I can write a metric filter for Nginx 5xx and test it with `test-metric-filter`
- [ ] I can build metric, composite and recover alarms and explain missing-data handling
- [ ] I can use Session Manager, Run Command, Patch Manager, maintenance windows and Automation
- [ ] I built an EventBridge rule that remediates an alarm automatically
- [ ] I can grow an EBS volume online and extend the filesystem
- [ ] I can build a launch template, ALB, target group and Auto Scaling group from the CLI
- [ ] I can explain target tracking vs step vs scheduled vs predictive scaling
- [ ] I can write S3 lifecycle rules for versioned buckets and recover a deleted object
- [ ] I wired S3 event notifications to Lambda, including the invoke permission
- [ ] I can create Route 53 health checks, alarm on them, and describe every routing policy
- [ ] I ran an AWS Backup job and a successful restore, and know the DR tiers (backup-restore to active/active)
- [ ] I can deploy, change-set, drift-detect and delete a CloudFormation stack; I know StackSets, RAM and CDK basics
- [ ] I built a VPC with IGW, routes, NACLs and an S3 gateway endpoint and read flow logs with Logs Insights
- [ ] I can put CloudFront in front of private S3 with OAC and explain invalidation vs versioned names
- [ ] I can create a KMS key, use it for EBS, and explain key policies and cross-account sharing
- [ ] I can find an actor in CloudTrail and explain Access Analyzer, Config rules and conformance packs
- [ ] I can explain Organizations, SCPs, IAM Identity Center, GuardDuty, Security Hub, Inspector, Macie
- [ ] I restored RDS to a point in time and know Multi-AZ vs read replicas vs RDS Proxy
- [ ] I can describe in a sentence each of: Bedrock, Kiro, DevOps Agent, Security Agent, Health Dashboard
- [ ] I scored 80%+ on the official practice question set and reviewed every miss
- [ ] ESL accommodation requested (if wanted), ID names match my account, OnVUE system test passed
- [ ] All lab resources deleted and Cost Explorer shows nothing running

## Sources

- AWS Certified CloudOps Engineer - Associate exam page (name, SOA-C03, format, 65 questions, 130 minutes, 150 USD, delivery, languages, Korean and Chinese retirement after Nov 19, 2026, SysOps holders): https://aws.amazon.com/certification/certified-cloudops-engineer-associate/
- AWS Certified SysOps Administrator - Associate exam page (last exam date Sep 29, 2025; replacement): https://aws.amazon.com/certification/certified-sysops-admin-associate/
- SOA-C03 exam guide (question types, 50 scored and 15 unscored, 720 of 1,000, compensatory scoring, domain weights): https://docs.aws.amazon.com/aws-certification/latest/sysops-administrator-associate-03/sysops-administrator-associate-03.html
- SOA-C03 Domain 1: https://docs.aws.amazon.com/aws-certification/latest/sysops-administrator-associate-03/sysops-administrator-associate-03-domain1.html
- SOA-C03 Domain 2: https://docs.aws.amazon.com/aws-certification/latest/sysops-administrator-associate-03/sysops-administrator-associate-03-domain2.html
- SOA-C03 Domain 3: https://docs.aws.amazon.com/aws-certification/latest/sysops-administrator-associate-03/sysops-administrator-associate-03-domain3.html
- SOA-C03 Domain 4: https://docs.aws.amazon.com/aws-certification/latest/sysops-administrator-associate-03/sysops-administrator-associate-03-domain4.html
- SOA-C03 Domain 5: https://docs.aws.amazon.com/aws-certification/latest/sysops-administrator-associate-03/sysops-administrator-associate-03-domain5.html
- SOA-C02 vs SOA-C03 comparison (SOA-C02 until Sep 29, 2025; SOA-C03 from Sep 30, 2025): https://docs.aws.amazon.com/aws-certification/latest/sysops-administrator-associate-03/sysops-administrator-associate-03-comparison.html
- SOA-C03 revisions (v1.0 Sep 30, 2025; v1.1 June 1, 2026; added services): https://docs.aws.amazon.com/aws-certification/latest/sysops-administrator-associate-03/soa-03-revisions.html
- SOA-C03 in-scope services: https://docs.aws.amazon.com/aws-certification/latest/sysops-administrator-associate-03/soa-03-in-scope-services.html
- SOA-C02 exam guide v2.3 (exam labs removed as of March 28, 2023): https://d1.awsstatic.com/training-and-certification/docs-sysops-associate/AWS-Certified-SysOps-Administrator-Associate_Exam-Guide.pdf
- AWS Certification policies, before testing (reschedule, ESL accommodation): https://aws.amazon.com/certification/policies/before-testing/
- AWS Certification policies, during testing (ID, check-in, no breaks online): https://aws.amazon.com/certification/policies/during-testing/
- AWS Certification FAQs (14-day retake wait, 2-year retake rule after passing): https://aws.amazon.com/certification/faqs/
- AWS Free Tier (Free and Paid plans, up to 200 USD credits, 6 months): https://aws.amazon.com/free/
- AWS Free Tier FAQs (Free plan expiry and restrictions): https://aws.amazon.com/free/free-tier-faqs/
- EC2 Free Tier usage (eligible instance types for accounts after July 15, 2025): https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-free-tier-usage.html
- AWS Budgets CostTypes (IncludeCredit defaults to true): https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_budgets_CostTypes.html
- Unverified: which Skill Builder exam-prep items are free vs subscription; exact per-service Free plan restrictions; the dollar amount of each Explore AWS credit activity.
