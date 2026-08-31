# Especificación del Protocolo Modbus TCP

> Referencia técnica de MBAP Header, códigos de función e interpretación de registros industriales.

---

## 📡 MBAP Header (Modbus Application Protocol Header)

A diferencia de Modbus RTU (RS-485), Modbus TCP envuelve las tramas en un cabezal de 7 bytes sobre TCP (Puerto 502):

| Campo | Tamaño | Descripción |
|---|---|---|
| **Transaction ID** | 2 Bytes | Identificador único de transacción |
| **Protocol ID** | 2 Bytes | Siempre `0x0000` para Modbus |
| **Length** | 2 Bytes | Número de bytes restantes en la trama |
| **Unit ID** | 1 Byte | Dirección de esclavo / Slave ID (1 a 247) |

---

## 🔢 Códigos de Función Canónicos

- `FC01` (Read Coils): Lectura de salidas discretas (Bits).
- `FC02` (Read Discrete Inputs): Lectura de entradas digitales (Bits).
- `FC03` (Read Holding Registers): Lectura de registros internos de 16-bit (Read/Write).
- `FC04` (Read Input Registers): Lectura de entradas analógicas de 16-bit (Read-Only).
- `FC05` (Write Single Coil): Escritura de un bit individual.
- `FC06` (Write Single Register): Escritura de un registro de 16-bit.
- `FC16` (Write Multiple Registers): Escritura en bloque de múltiples registros.
