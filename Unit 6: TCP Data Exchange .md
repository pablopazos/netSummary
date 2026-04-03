
# 🔄 Unit 6: TCP Data Exchange

This unit focuses on how TCP ensures a **reliable data transfer service** over an unreliable network (IP) and how it manages different types of data flows and congestion.

---

### 1. Reliable Data Transfer Service
TCP's main goal is to ensure that:
1. **No corruption:** Data is received exactly as sent.
2. **No loss:** All segments reach the destination.
3. **Correct order:** Data is delivered to the application in the original sequence.

---

### 2. Interactive vs. Non-Interactive Traffic

#### ⌨️ Interactive Data Flow (Low Latency)
Used for applications like **Telnet** or **SSH** where small amounts of data (often 1 byte) are sent.
* **Delayed ACK:** TCP usually waits up to **200ms** before sending an ACK, hoping to "piggyback" the acknowledgment on an outgoing data segment to save bandwidth.
* **Nagle's Algorithm:** To avoid sending too many tiny packets (overhead), this algorithm collects small amounts of data and sends them only when a full-sized segment can be formed or when an ACK for the previous segment is received.

####  Non-Interactive Data Flow (Bulk Transfer)
Used for large transfers like **FTP** or **HTTP**. 
* Focuses on throughput rather than latency.
* Uses the **Sliding Window** mechanism to send multiple segments before needing an ACK.

---

### 3. TCP Congestion Control
Congestion occurs when there is too much data in the network for the routers to handle.

* **Indicators of Congestion:**
    1. **Retransmission Timeout (RTO):** Severe congestion (Fast Recovery).
    2. **Duplicate ACKs:** Moderate congestion; 3 duplicate ACKs trigger **Fast Retransmit**.
* **Key Algorithms:**
    * **Slow Start:** Increases the congestion window (cwnd) exponentially until a threshold is reached.
    * **Congestion Avoidance:** Increases the window linearly to probe for available bandwidth.

---

### 4. TCP Keepalive Timer
In a connection where no data is being exchanged, TCP remains silent. This can be a problem if one end crashes without closing the connection.

* **Function:** After **2 hours** of inactivity, the server sends a **keepalive probe** (a 1-byte segment).
* **Possible Responses:**
    1. **OK:** The connection remains active.
    2. **Crashed:** No response after several probes; the connection is closed.
    3. **Rebooted:** The peer responds with an **RST** (Reset).
    4. **Unreachable:** Network error (ICMP unreachable).

---

### 5. Retransmission Strategies
* **Stop & Wait:** Inefficient (waits for each ACK).
* **Pipelining (Go-Back-N / Selective Repeat):** Allows sending multiple packets without waiting for ACKs, significantly improving performance.
* **Fast Retransmit:** If 3 duplicate ACKs are received, TCP retransmits the missing segment immediately without waiting for the timer to expire.
