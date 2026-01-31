# pd5201-DATAB-projekt
database project

## Wyniki zapytań SQL

### Zapytanie 4ii: Rodzaje i ilość testów w których uczestniczyło powyżej 30 pacjentów
**Zapytanie:**
```sql
Select tests.test_type,
COUNT(DISTINCT patient_test.patient_id) AS num_patients
From tests
Inner join patient_test on patient_test.test_id = tests.test_id
GROUP BY tests.test_type
HAVING COUNT(DISTINCT patient_test.patient_id) > 30;
```
| test_type | num_patients |
|-----------|--------------| 
| NGS-panel |           38 | 
| SNP Array |           39 |
