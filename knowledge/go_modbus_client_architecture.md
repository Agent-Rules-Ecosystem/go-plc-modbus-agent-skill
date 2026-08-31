# Arquitectura de Cliente Modbus en Go

---

## 🏗️ Polling Worker Pattern con Goroutines

```go
package main

import (
	"context"
	"log"
	"time"

	"github.com/simonvetter/modbus"
)

type PLCWorker struct {
	client *modbus.ModbusClient
	ip     string
	port   uint16
}

func (w *PLCWorker) Start(ctx context.Context, interval time.Duration) {
	ticker := time.NewTicker(interval)
	defer ticker.Stop()

	for {
		select {
		case <-ctx.Done():
			log.Println("Deteniendo worker PLC...")
			return
		case <-ticker.C:
			w.pollRegisters()
		}
	}
}

func (w *PLCWorker) pollRegisters() {
	if w.client == nil {
		return
	}
	regs, err := w.client.ReadRegisters(0, 10, modbus.HOLDING_REGISTER)
	if err != nil {
		log.Printf("Error leyendo registros PLC: %v", err)
		return
	}
	log.Printf("Valores leídos: %v", regs)
}
```
