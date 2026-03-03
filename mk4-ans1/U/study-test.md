# U — STUDY TEST (MK4-ANS1) (A/B/C)
PASS ≥ 7/10

1) Ansible е:
A) agent-based tool, който изисква агент на всяка машина
B) agentless automation over SSH
C) container orchestrator

2) Правилният модел е:
A) playbook → plays → tasks
B) tasks → playbook → commits
C) branches → pods → services

3) Inventory е:
A) списък/структура на target hosts и групи
B) списък с Docker images
C) списък с Kubernetes namespaces

4) Най-добра практика е да използваш:
A) shell/command винаги
B) modules когато има
C) само bash scripts

5) Idempotency означава:
A) задачата всеки път прави промяна
B) можеш да пускаш многократно без излишни промени
C) работи само веднъж

6) `become: true` се ползва за:
A) промяна на git branch
B) privilege escalation (sudo/root операции)
C) смяна на IP адрес

7) Handler се изпълнява:
A) винаги
B) само при notify (когато има промяна)
C) само при reboot

8) `gather_facts: false`:
A) ускорява playbook-а за лаборатории
B) прави playbook-а да изпълнява tasks два пъти
C) изключва SSH

9) `ansible-playbook --syntax-check`:
A) изпълнява задачите
B) валидира синтаксис/структура без изпълнение
C) създава VM

10) Най-честите проблеми при Ansible са:
A) SSH access и permissions
B) липса на интернет винаги
C) Docker layers

## ANSWER KEY
1) B
2) A
3) A
4) B
5) B
6) B
7) B
8) A
9) B
10) A
