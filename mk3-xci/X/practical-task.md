# X — PRACTICAL TASK (MK3-XCI)

Цел: да симулираш локален CI gate върху мини-лаб: yamllint + ansible-lint + ansible syntax-check.
Работи във VM.

## Lab steps
```bash
mkdir -p ~/mk3-xci-lab && cd ~/mk3-xci-lab

# 1) yamllint config (policy)
cat > .yamllint <<'YML'
extends: default
rules:
  line-length: {max: 120}
  truthy: disable
YML

# 2) Create a broken YAML (expect FAIL)
printf "a: 1\n  b: 2\n" > bad.yml
yamllint -f parsable bad.yml || true

# 3) Fix YAML (expect PASS)
printf "a: 1\nb: 2\n" > good.yml
yamllint -f parsable good.yml

# 4) Create playbook + run syntax-check
cat > playbook.yml <<'YML'
- name: mk3 gate lab
  hosts: localhost
  gather_facts: false
  tasks:
    - name: create file
      ansible.builtin.copy:
        dest: /tmp/mk3_gate.txt
        content: "mk3 gate ok\n"
        mode: "0644"
YML
ansible-playbook --syntax-check playbook.yml

# 5) ansible-lint on playbook
ansible-lint playbook.yml
```

## PASS CRITERIA
- yamllint FAIL на bad.yml (доказваш, че gate хваща проблем)
- yamllint PASS на good.yml
- ansible-playbook --syntax-check PASS
- ansible-lint PASS (или ако има finding → fix и после PASS)
- можеш да покажеш outputs като evidence
