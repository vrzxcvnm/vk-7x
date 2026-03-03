# X — COMMANDS TEST (MK3-XCI)
PASS ≥ 7/10

Цел: да пускаш lint/validation командите без подсказване и да четеш резултата.
Работи във VM.

## Commands (тренирай)
```bash
yamllint --version
yamllint -f parsable file.yml
ansible-lint --version
ansible-lint playbook.yml
ansible-playbook --syntax-check playbook.yml
```

## TEST ITEMS (10 точки)
1) Каква е разликата lint vs validation?
2) Какво означава FAIL на yamllint?
3) Кога ansible-lint може да FAIL дори при валиден YAML?
4) Какво гарантира `--syntax-check` (и какво НЕ гарантира)?
5) Защо gate редът е важен (преди commit)?
6) Как идентифицираш файла/реда от lint output?
7) Какво е .yamllint config и защо е нужен?
8) Какво е най-честият YAML проблем (indent/tabs)?
9) Какво правиш ако lint-ът е “too strict” (policy adjustment)?
10) Как доказваш, че gate е PASS (показваш outputs)?

## PASS CRITERIA
Commands Test = PASS ако ≥ 7/10 са правилни + показваш реални outputs.
