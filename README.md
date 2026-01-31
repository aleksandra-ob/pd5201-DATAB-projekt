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

### Zapytanie 4iii: Rodzaje testów wraz ze średnią liczbą wariantów w nich wykrytych
**Zapytanie:**
```sql
Select test_type,
AVG(variant_count) AS avg_variants
From (
Select tests.test_id, tests.test_type, 
Count(results.result_id) as variant_count
From tests
Inner join results on results.test_id = tests.test_id
GROUP BY tests.test_id, tests.test_type) sub
Group by test_type;
```
| test_type | avg_variants |
|---|---|
| SNP Array |       3.0000 |
| NGS-panel |       3.6857 |
| WES       |       3.5294 |
| WGS       |       3.6071 |



