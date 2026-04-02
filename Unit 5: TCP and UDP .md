#  Layer 4: Transport Layer (TCP & UDP)

The Transport Layer is responsible for **process-to-process** communication. It ensures that data from the upper layers reaches the correct application on the destination host using **port numbers**.

---

### 1. TCP (Transmission Control Protocol)
TCP is a **connection-oriented** and **reliable** protocol. It ensures that all data is delivered in the correct order and without errors.

* **Reliability:** Uses acknowledgments (ACK) and retransmissions.
* **Flow Control:** Prevents the sender from overwhelming the receiver (Sliding Window).
* **Error Detection:** Uses checksums to verify data integrity.

####  The Three-Way Handshake (Connection Establishment)
Before sending data, TCP establishes a logical connection:
1.  **SYN:** Client sends a synchronization segment to the server.
2.  **SYN-ACK:** Server acknowledges and sends its own synchronization request.
3.  **ACK:** Client acknowledges the server's request. Connection is now **established**.

####  Connection Termination
* Uses **FIN** segments to close a connection gracefully.
* Uses **RST** (Reset) if a connection needs to be closed abruptly due to an error or an unauthorized port.

---

### 2. UDP (User Datagram Protocol)
UDP is a **connectionless** and **unreliable** protocol (best-effort delivery). It does not guarantee that data will arrive.

* **Low Overhead:** No handshakes, no acknowledgments, no flow control.
* **Speed:** Much faster than TCP, ideal for real-time applications.
* **Usage:** Used when speed is more important than perfect accuracy.

---

### 3. Comparison Table: TCP vs. UDP

| Feature | TCP | UDP |
| :--- | :--- | :--- |
| **Connection** | Connection-oriented | Connectionless |
| **Reliability** | Guaranteed delivery | Best-effort (unreliable) |
| **Data Flow** | Byte stream (ordered) | Datagrams (unordered) |
| **Speed** | Slower (due to overhead) | Faster (minimum overhead) |
| **Applications** | HTTP/HTTPS, SSH, FTP, SMTP | DNS, DHCP, VoIP, Streaming |

---

### 4. Addressing: Port Numbers
Ports allow a single physical device to run multiple network services simultaneously.

* **Range:** 0 to 65535.
* **Well-known Ports (0 - 1023):** Reserved for standard services.
    * **21:** FTP (File Transfer)
    * **22:** SSH (Secure Shell)
    * **25:** SMTP (Email)
    * **53:** DNS (Domain Name System - uses both, mostly UDP)
    * **80 / 443:** HTTP / HTTPS (Web)
* **Registered Ports (1024 - 49151):** For specific user processes or applications.
* **Dynamic/Private Ports (49152 - 65535):** Temporary ports used by clients to initiate connections.

---

### 5. Segmentation and Multiplexing
* **Segmentation:** Breaking large application data into smaller pieces (segments) for transport.
* **Multiplexing:** Using different port numbers to handle multiple conversations over the same network interface.
