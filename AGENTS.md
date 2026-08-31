---
name: go-plc-modbus-agent-skill
description: Specialized skill for industrial PLC Ethernet Modbus TCP communication in Go.
---

# 🦫🔌 Go PLC Modbus Skill Directive

## Bootstrap de la Habilidad

1. `.skill/go-plc-modbus-agent-skill/core/commands.md` ← Comandos de dominio
2. `.skill/go-plc-modbus-agent-skill/core/brain.md` ← Matriz de diagnóstico y reconexión PLC
3. `.skill/go-plc-modbus-agent-skill/SKILL.md` ← Directivas técnicas y endianness
4. `.skill/go-plc-modbus-agent-skill/knowledge/modbus_tcp_protocol.md` ← Referencia del protocolo

## Reglas Canónicas de la Skill

1. **Nunca bloquear el loop principal**: Todo acceso a I/O industrial Ethernet debe correr en una Goroutine dedicada con `context.Context` y timeout explícito.
2. **Reconexión Automática**: El cliente Modbus debe implementar reconexión transparente tras fallos de Socket TCP sin tirar el proceso.
3. **Conversión Estricta de Byte Order**: Mapear explícitamente el orden de palabra/byte (BigEndian / LittleEndian / ABCD / CDAB) según la especificación del PLC.
4. **Persistencia Activa**: Los resultados del diagnóstico `$goplc:audit` deben registrarse obligatoriamente en `overview/work/skill/go-plc-modbus.md`.
