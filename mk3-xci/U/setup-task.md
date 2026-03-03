# U — SETUP TASK (MK3-XCI) — VM (Ubuntu 24.04)

Цел: да инсталираш и валидираш lint/validation инструментите във VM: yamllint, ansible-lint, ansible.

## A) Влизане във VM (Host)
```powershell
cd .\vm
vagrant ssh
```

## B) Install / Verify (във VM) — recommended (apt)
```bash
sudo apt-get update
sudo apt-get install -y yamllint ansible ansible-lint

yamllint --version
ansible --version
ansible-lint --version
```

## C) Quick sanity checks
```bash
# 1) yamllint on inline YAML (should PASS)
printf "a: 1\nb: 2\n" > /tmp/ok.yml
yamllint /tmp/ok.yml

# 2) ansible syntax-check minimal playbook (should PASS)
cat > /tmp/p.yml <<'YML'
- name: mk3 sanity
  hosts: localhost
  gather_facts: false
  tasks:
    - name: ping
      ansible.builtin.ping:
YML
ansible-playbook --syntax-check /tmp/p.yml
```

## PASS CRITERIA
Setup Task = PASS ако:
- `yamllint --version` работи
- `ansible --version` работи
- `ansible-lint --version` работи
- yamllint PASS на ok.yml
- ansible-playbook --syntax-check PASS на /tmp/p.yml
