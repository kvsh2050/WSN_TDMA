# Wireless Sensor Network – Coordinator Node

This project implements a **central coordinator** in a wireless sensor network using the **nRF24L01+ transceiver** and **RF24Network** protocol. The coordinator communicates with 3 sensor nodes in a time-slotted manner, sending timestamped data packets and verifying acknowledgment (ACK) responses.

---

## Coordinator Node

![Coordinator screen](https://github.com/user-attachments/assets/d03092f7-ae4e-4cf6-b25d-fa78e4619d21)  
![Terminal output](https://github.com/user-attachments/assets/006f5a0d-9bb6-4556-809a-0f7a56659d9d)

The coordinator handles:
- Packet construction using a `payload_t` struct
- Communication with three nodes: Node 1, Node 2, and Node 3
- ACK detection for reliability
- Timing between transmissions to avoid radio collisions

---

## Implementation Details

![Implementation setup](https://github.com/user-attachments/assets/3844d466-7d21-435e-a950-f8582a2d172c)

- **Microcontroller**: Arduino-compatible board
- **Wireless module**: nRF24L01+
- **Protocol**: RF24Network over SPI
- **Addressing**: Octal (Coordinator = 00, Nodes = 01, 02, 03)
- **Transmission cycle**: Every 60 seconds (with 15s and 30s delays between nodes)

### Payload Structure

```cpp
struct payload_t {
  unsigned long ms;       // Time since device start
  unsigned long counter;  // Packet number
};
````

---

## Sensor Nodes

Each node receives a message from the coordinator, responds with an ACK, and may optionally send data back.

![Nodes photo](https://github.com/user-attachments/assets/78194b24-3ce8-4eb1-a2af-212b1c42f971)
![Node test bench](https://github.com/user-attachments/assets/33762e5a-b977-460e-8b43-50b9f62c6028)
![Hardware connections](https://github.com/user-attachments/assets/7057d9cc-c079-4b23-9def-77068e8033ba)

---

## Summary

This setup demonstrates a lightweight and scalable **wireless sensor network**, with one central coordinator polling three nodes in sequence. It’s ideal for IoT applications, environmental monitoring, or remote data collection with acknowledgment tracking.

> For the full code and node implementation, refer this repository.


