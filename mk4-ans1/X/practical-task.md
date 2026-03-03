# X — PRACTICAL TASK (MK4-ANS1)

Цел: да напишеш playbook за localhost, който:
- създава файл в /tmp (с become)
- използва handler (notify → handler)
- доказва idempotency (second run без промяна)

Работи във VM.

## Steps
```bash
mkdir -p ~/mk4-ans1-lab && cd ~/mk4-ans1-lab

# 1) inventory
cat > inventory.ini <<'INI'
[local]
localhost ansible_connection=local
INI

# 2) playbook (handler се задейства само ако файлът се промени)
cat > playbook.yml <<'YML'
- name: mk4 ans1 lab
  hosts: local
  gather_facts: false
  become: true
  tasks:
    - name: write config file
      ansible.builtin.copy:
        dest: /tmp/mk4_ans1.conf
        content: "mk4 ans1 config v1\\n"
        mode: "0644"
      notify: restart-demo

  handlers:
    - name: restart-demo
      ansible.builtin.debug:
        msg: "HANDLER RUN (only when copy changed)"
YML

# 3) gates
ansible-playbook --syntax-check -i inventory.ini playbook.yml

# 4) run 1
ansible-playbook -i inventory.ini playbook.yml

# 5) run 2 (трябва да е идемпотентно: copy task да е ok/unchanged, handler да НЕ се изпълни)
ansible-playbook -i inventory.ini playbook.yml
```

## PASS CRITERIA
- syntax-check PASS
- run 1: има промяна (changed) и handler се изпълнява
- run 2: без промяна (ok/unchanged) и handler не се изпълнява
- можеш да обясниш защо това демонстрира idempotency
