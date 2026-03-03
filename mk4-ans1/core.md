# MK4 — ANS1 (Ansible Automation)

## INDEX
MK4-ANS1: Ansible automation (agentless over SSH). Целта е да можеш да пишеш минимални playbook-и, да ползваш modules вместо shell, да работиш с inventory/vars/become/handlers и да доказваш idempotency.
Изход: локален playbook, който прави реална конфигурационна промяна и на втори run не прави излишни промени.

## THEORY

### 1) Какво е Ansible (защо DevOps го ползва)
- Ansible е automation/orchestration tool.
- Agentless: не слагаш агент на target-а. Control node се свързва към target по SSH.
- Полза: repeatable конфигурация, по-малко „snowflakes“, по-бързи промени и по-добра проследимост.

### 2) Архитектура и термини
- Control node: машината, от която пускаш Ansible (в нашия проект: VM).
- Managed node: target machine (в лабораториите може да е localhost).
- Inventory: списък/групи на targets + vars.
- Module: „правилният“ начин (idempotent операции).
- Playbook: YAML, който съдържа plays.
- Play: hosts + настройки + tasks.
- Task: единична стъпка (обикновено module call).

### 3) Inventory (targets и групи)
- Inventory може да е файл (INI/YAML) или inline (`-i localhost,`).
- Groups: `[web]`, `[db]` и т.н.
- Vars могат да са на host/group/play ниво.
Ключ: ако inventory/hosts са грешни → нищо не се изпълнява където трябва.

### 4) Modules vs shell/command
- Modules са предпочитани: знаят как да проверят state и са по-idempotent.
- `shell`/`command` са last resort: трудно се прави идемпотентност, повече риск и „шум“.

### 5) Idempotency (най-важната концепция)
Idempotent task: пускаш го 100 пъти → първия път прави нужната промяна, следващите пъти е “ok/unchanged”.
Практически критерий: second run на playbook трябва да има минимален “changed”.

### 6) become (sudo/root)
- Много системни операции искат root (apt, /etc, services).
- `become: true` прави privilege escalation (sudo).
- Ако забравиш become → permission denied.

### 7) Variables (vars) и templating
- Vars са параметри: в playbook (`vars:`), inventory, или `-e` (extra vars).
- Jinja2 се ползва за template (напр. `{{ var }}`).
Минимум за модула: разбираш къде може да живее една променлива и как се референцира.

### 8) Handlers (notify → handler)
- Handler е task, който се изпълнява само ако е “notified” от друга задача.
- Типичен pattern: променяш config файл → notify → restart service.
- Това е директно свързано с idempotency (няма ненужни рестарти).

### 9) Gather facts
- По default Ansible събира facts (данни за OS/мрежа).
- За лаборатории често: `gather_facts: false` (по-бързо, по-малко шум).

### 10) Минимален troubleshooting standard
- Gate 1: `ansible-playbook --syntax-check playbook.yml`
- Verbose: `-v`, `-vvv`
- Най-чести проблеми: YAML indent, permissions/become, inventory/hosts, missing collection/module.

### KEY TAKEAWAYS (Study Test е по това)
1) Ansible е agentless и работи over SSH.
2) Playbook → play → tasks (tasks викат modules).
3) Inventory дефинира targets + групи + vars.
4) Modules > shell/command.
5) Idempotency: second run = минимален “changed”.
6) become: true за root операции.
7) Handlers: notify → run only on change.
8) gather_facts: false намалява шум и ускорява.
9) syntax-check е задължителен gate.
10) Най-чести fail-ове: SSH/inventory и permissions.

## INSTRUCTIONS
1) Прочети THEORY + KEY TAKEAWAYS.
2) U: Study Test (≥7/10) + Setup Task (Ansible install + localhost ping).
3) X: Commands Test (≥7/10) + Practical Task (playbook с become + handler + idempotency proof).
4) Validation + commit само при PASS.

## TO COMPLETE
PASS изисква:
- Study Test: PASS (≥ 7/10)
- Setup Task: PASS (ansible работи във VM)
- Commands Test: PASS (≥ 7/10)
- Practical Task: PASS (run1 changed + handler ran; run2 unchanged + handler not run)

## FINAL
```powershell
git add mk4-ans1
git commit -m "mk4-ans1: module complete"
git push   # само ако има remote
```
