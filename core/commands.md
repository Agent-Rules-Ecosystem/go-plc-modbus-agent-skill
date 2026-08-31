# Comandos de Dominio — go-plc-modbus-agent-skill

- `$goplc`: Bootstrap e inyección de la habilidad Modbus PLC en Go.
- `$goplc:audit`: Auditoría de conexión Ethernet, timeouts y registros mapeados del PLC. Registra hallazgos en `overview/work/skill/go-plc-modbus.md`.
- `$goplc:read [ip] [port] [reg]`: Genera snippet de lectura de registros (Holding / Input).
- `$goplc:worker`: Genera la estructura de un worker loop concurrente con goroutines.
