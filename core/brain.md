# Motor de Decisiones — go-plc-modbus-agent-skill

| Situación | Diagnóstico | Acción recomendada |
|---|---|---|
| Timeout de socket TCP | Enlace Ethernet caído o IP/Puerto erróneo | Implementar reconexión exponencial con `time.Sleep` |
| Valores `float32` corruptos | Byte order / Word swap no coincidente | Probar decodificación ABCD vs CDAB vs BADC |
| Error `Illegal Data Address` | Registro fuera del mapa permitido por el PLC | Verificar offset 0-based vs 1-based (ej: Holding Reg 40001 -> Offset 0) |
| Bloqueo de Goroutines | Falta de `context.WithTimeout` | Envolver llamadas en I/O con timeouts explícitos |
