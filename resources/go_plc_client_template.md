# Plantilla de Código — Cliente PLC Modbus TCP en Go

```go
// Package plc proporciona abstracción de comunicación con PLC Ethernet vía Modbus TCP
package plc

import (
	"encoding/binary"
	"fmt"
	"math"
	"time"

	"github.com/simonvetter/modbus"
)

type PLCClient struct {
	client *modbus.ModbusClient
}

func NewPLCClient(host string, port uint16) (*PLCClient, error) {
	c, err := modbus.NewClient(&modbus.ClientConfiguration{
		URL:     fmt.Sprintf("tcp://%s:%d", host, port),
		Timeout: 2 * time.Second,
	})
	if err != nil {
		return nil, err
	}
	return &PLCClient{client: c}, nil
}

func (p *PLCClient) ReadFloat32(addr uint16) (float32, error) {
	regs, err := p.client.ReadRegisters(addr, 2, modbus.HOLDING_REGISTER)
	if err != nil {
		return 0, err
	}
	bytes := []byte{
		byte(regs[0] >> 8), byte(regs[0]),
		byte(regs[1] >> 8), byte(regs[1]),
	}
	bits := binary.BigEndian.Uint32(bytes)
	return math.Float32frombits(bits), nil
}
```
