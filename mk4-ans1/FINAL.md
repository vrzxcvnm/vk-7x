# FINAL — MK4 ANS1

## RESULTS
- Study Test: 7 / 10 (PASS ≥ 7)
- Setup Task: PASS 
- Commands Test: PASS 
- Practical Task: PASS 

## EVIDENCE (paste outputs)
- `ansible --version`
- `ansible localhost -m ping -c local`
- Practical proof:
  - run1 output (changed + handler ran)
  - run2 output (unchanged + handler did NOT run)

## VALIDATION CHECKLIST
- [ ] tree mk4-ans1 /F структура е правилна
- [ ] setup е PASS (ansible работи)
- [ ] практическата задача е PASS
- [ ] git status на host е clean за модула преди commit

## COMMIT (само ако PASS)
```powershell
git add mk4-ans1
git commit -m "mk4-ans1: module complete"
git push   # само ако има remote
```
