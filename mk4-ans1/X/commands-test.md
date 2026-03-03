# X — COMMANDS TEST (MK4-ANS1)
PASS ≥ 7/10

Цел: да можеш да изпълняваш основните Ansible команди без подсказване и да обясниш резултата.
Работи във VM.

## Commands (тренирай)
```bash
ansible --version
ansible localhost -m ping -c local
ansible-playbook --syntax-check playbook.yml
ansible-playbook playbook.yml
ansible-playbook playbook.yml -v
```

## TEST ITEMS (10 точки)
1) Какво показва `ansible --version` (versions/paths)?
2) Защо `-c local` е полезно за localhost?
3) Какво валидира `--syntax-check`?
4) Разлика между module и shell/command?
5) Какво е inventory и защо е важно?
6) Какво е HEAD/branch? (връзка с workflow: не комитваш без PASS)
7) Какво е idempotency и как я доказваш?
8) Какво прави `become: true`?
9) Какво е handler и кога се изпълнява?
10) Как дебъгваш playbook run (verbosity)?

## PASS CRITERIA
Commands Test = PASS ако ≥ 7/10 са правилни + показваш реални outputs.
