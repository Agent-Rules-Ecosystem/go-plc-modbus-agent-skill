# Script de Diagnóstico — Go Modbus TCP Health Checker

```markdown
```bash
# Diagnóstico rápido de puerto Modbus TCP PLC (Puerto 502 por defecto)
nc -zvw3 192.168.1.50 502
```

Si el puerto responde `open`, ejecutar la auditoría de registros con `$goplc:audit`.
```
