# Communication Protocols

## Characteristic

## UART

**Universal Asyncronous Receiver/Transmitter**

**Properties**

- Communicate data serially, asynchronously.
- The underlying physical layer may be a telegraph wire or serial port.
- May contains parity bit

**Usage** 

- Used for communicating to embeded chip because it's simple
- USB serial

**Consideration**

- Speed is limited by electrical characteristic and clock.
- Receiver need to do **super-sampling** (sampling higher than the clock rate)
to ensure that we don't skip bits.
- Start and stop bit is needed to signal async start and synchronize clock

### Transmision

- The wire is kept high. (due to historical reason, to check if telegraph line is damaged)
- To sent byte, signal LOW (start) for 1 time unit (determined by **buad rate**)
- Send all bit from LSB to MSB.
- Send a single HIGH bit (stop).

## SPI

- **Serial Peripheral Interface**
- Synchronous, Full-Deplex, Master/Slave

### Interface

- SCLK: Clock
- MOSI: Master Out - Slave In
- MISO: Master In - Slave Out
- nSS -CS: NOT Slave Select

### Topology

- Single master, Multiple slave
	- Share common SCLK, MOSI, MISO bus, Separate nSS connections
- Single master, Daisy chained slave
	- Share common SCLK, nSS. MOSI and MISO is daisy chained slaves
	as if that they are shift register.

### Transmission

- Slaves contains shift register buffering 8 most-recent bits.
- The bits are commited on SS rising edge
- The rest of the protocol are left undefined eg. when do word is received.

## I2C

- Protocol for bus. unlike point to point in SPI, UART
- Synchronous
- Half Duplex
- Multi Master/Slave

### Wiring

- SDA: Data 
- SCL: Clock

both are pulled-up using external resistor

### Transmission

1. SDA Low
2. Clock Low
3. Send data (eight bits) through SDA, receiver read on clock high
4. the receiver then ACK by sending LOW (if in slave to master direction, master don't ACK, then it mean master want to stop)

### Clock Stretching

Slave can pull the SCL low to prevent master from sending additional bits (because master need to make the clock high to send bits), when the master observe this, it means that slave is not ready.

### Arbitation

When multiple master attempt to send the message simultaneously (rarely happens because all master monitor the line for activity), master than see the SDA differ from what it want lose the arbitation. Note that from slave's perspective, the signal remains valid.

## CAN

[todo]

## Universal Serial Bus (USB)

### Characteristic

- Async
- Half-Duplex (Full-Duplex for 3 and C)
- Master/Slave

### Interface

- USB 1.X and 2.0
	- Vcc
	- D-
	- D+
	- GND
- USB 3.0
	- Previous
	- SSTX +/-
	- SSRX +/-

### Architecture

Tiered star Topology

- Host Controller
- Hub
- Peripheral

Single root expands like a tree. each node has a single upstream and multiple dwnstream.

#### Host
- Host enumerate peripherals
- Host learn VID (Vendor ID), and PID (Peripheral ID)
- Host assign addresses for all nodes

#### Peripheral

- Single/Compound device

#### Power management

- Host/Hub can electrically disconnect bad devices.

#### Communication

- USB return descriptor describing its capability
- Endpoint 0 is reserved for control transfer

#### Transfer Type

- Control Transfers: Config, Command
- Bulk Transfers: Bulk amount of data for non time-sensitive transfer
- Isochronous transfer: Streaming data eg. Webcam, Ethernet. allocated bandwidth
- Interrupt transfers: Poll devices

### Extension

#### USB-OTG

- Dual role devices
- Aggressive power management
