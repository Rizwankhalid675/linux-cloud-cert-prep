# Linux & Cloud Certification Prep

Self-study material for four Linux and cloud-ops credentials, built from the current official exam objectives. Hands-on labs, original practice questions, week-by-week plans and readiness checklists.

> Prepared with AI assistance (Claude) as a personal study resource. Every exam and badge is taken by the candidate, under each provider's rules. Practice questions are original; no exam material is reproduced. Verify prices, versions and dates on the official pages before booking.

## Contents

| Chapter | Credential | Format |
|---|---|---|
| 1 | Red Hat RHCSA (EX200) | Performance-based (note: official page now lists RHEL 10) |
| 2 | Linux Foundation LFCS | Performance-based, online proctored |
| 3 | AWS CloudOps Engineer – Associate (SOA-C03, formerly SysOps SOA-C02) | Multiple choice/response |
| 4 | Cisco NetAcad Linux Unhatched & Linux Essentials (+ optional LPI 010-160) | Course + final exam |

The full guide is compiled to [`linux-cert-prep-guide.pdf`](linux-cert-prep-guide.pdf) (97 pages).

## How it's organized

Each chapter has: an exam-facts table, an objectives map, a study plan, low/no-cost lab setup, hands-on tasks (with solutions and verify commands), original practice questions with answers, exam-day tips, a readiness checklist and cited sources.

## Rebuild the PDF

```
pip install reportlab
python build_pdf.py
```

The builder reads the `0*.md` chapter files and writes `linux-cert-prep-guide.pdf`.

## Disclaimer

Study aid only, provided as-is. Not affiliated with or endorsed by Red Hat, the Linux Foundation, Amazon Web Services, Cisco or LPI. Confirm every exam detail against the official source.
