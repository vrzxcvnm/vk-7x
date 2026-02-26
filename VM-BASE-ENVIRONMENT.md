VM BASE ENVIRONMENT (CREATED IN MK1)

OS: Ubuntu (box: bento/ubuntu-24.04 or ubuntu/jammy64)

Provider: VirtualBox

Minimum: 2 CPU / 4096 MB RAM

Recommended: 4 CPU / 8192 MB RAM (ако host позволява)

MODULE FLOW (ORDER IS STRICT)

mk1-vcor — Virtual Core (Host prep + VM lifecycle)

mk2-scm — Git Version Control

mk3-xci — CI Automation (YAML lint + validation)

mk4-ans1 — Ansible Automation

mk5-doc — Docker

mk6-k8s — Kubernetes

mk7-iac — Terraform (IaC)

mk8-sc1 — DevSecOps (Trivy + Gitleaks)

REQUIRED TOOLS INSIDE VM (BY MODULE)

mk2-scm

git

mk3-xci

yamllint

ansible-lint

ansible (за syntax-check)

mk4-ans1

ansible

ssh

mk5-doc

docker

docker compose

mk6-k8s

kubectl

kind OR minikube

mk7-iac

terraform

mk8-sc1

trivy

gitleaks

PROGRESSION MODEL (NO SKIPS)

THEORY
→ U (Study Test + Setup Task)
→ X (Commands Test + Practical Task)
→ FINAL
→ Git Commit
→ Next Module

COMMIT RULE

Един модул = един commit

Не смесвай модули в един commit

Commit само при PASS (≥ 70%)

Commit template:

git add mkX-xxxx
git commit -m "mkX-xxxx: module complete"
git push