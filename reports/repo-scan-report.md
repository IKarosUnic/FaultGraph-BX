## Reporte de Escaneo de Repositorio - FaultGraph-BX

- **Ruta objetivo:** `C:\GIT HUB\box\target_app`
- **Archivos evaluados:** 2
- **Archivos con problemas:** 1 / 2
- **Total de problemas detectados:** 4
- **Tiempo de analisis:** 364 ms

### Resumen por Severidad
| Severidad | Conteo |
| :--- | :---: |
| CRITICAL | 0 |
| HIGH     | 4 |
| MEDIUM   | 0 |
| LOW      | 0 |

### Detalle por Archivo
- [WARN] **`PaymentService.bx`**: 4 problema(s) encontrado(s):
  - **[Linea 60 | HIGH] UNPROTECTED_CONFIG_DEREF**: Acceso anidado a struct sin comprobacion de existencia ni valor por defecto (CWE-476).
    - *Evidencia:* `var surcharge = arguments.amount * variables.config.fallback.surchargePct;`
    - *Remediacion:* Validar con structKeyExists() o utilizar operador de navegacion segura con fallback.
  - **[Linea 60 | HIGH] UNVALIDATED_NUMERIC_CAST**: Operacion aritmetica directa sin validacion isNumeric() ni limpieza de caracteres (CWE-20).
    - *Evidencia:* `var surcharge = arguments.amount * variables.config.fallback.surchargePct;`
    - *Remediacion:* Normalizar montos y porcentajes verificando isNumeric() antes de calcular.
  - **[Linea 61 | HIGH] UNVALIDATED_NUMERIC_CAST**: Operacion aritmetica directa sin validacion isNumeric() ni limpieza de caracteres (CWE-20).
    - *Evidencia:* `var total     = arguments.amount + surcharge;`
    - *Remediacion:* Normalizar montos y porcentajes verificando isNumeric() antes de calcular.
  - **[Linea 62 | HIGH] UNPROTECTED_CONFIG_DEREF**: Acceso anidado a struct sin comprobacion de existencia ni valor por defecto (CWE-476).
    - *Evidencia:* `var queueName = variables.config.fallback.queueName;`
    - *Remediacion:* Validar con structKeyExists() o utilizar operador de navegacion segura con fallback.
- [OK] **`PaymentServicePatched.bx`**: Sin problemas detectados.