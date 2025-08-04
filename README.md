# 🚀 Multi-Threaded Proxy Server with Cache

A multi-threaded HTTP proxy server implemented in **C** using **POSIX threads**, **semaphores**, and an **LRU cache**. It supports concurrent handling of multiple client requests with basic caching to reduce latency and server load.

---

## 🧠 Project Theory

### 🔁 Multi-threading
- Implemented using **POSIX threads (`pthread`)**.
- Used **semaphores** instead of condition variables.
- Why semaphores?
  - `pthread_join()` requires a specific thread ID to wait on.
  - `sem_wait()` and `sem_post()` are simpler and don’t need specific IDs.
  - Better abstraction for handling resource locking.

### 🔧 OS Components Used
- Threads (`pthread`)
- Semaphores (`sem_init`, `sem_wait`, `sem_post`)
- Locks (for concurrency control)
- Cache (implemented with **LRU algorithm**)

---

## 🎯 Project Goals & Motivation

- Understand how local requests are routed to a server.
- Learn how to manage multiple simultaneous client requests.
- Explore thread-level locking and synchronization.
- Implement a basic **HTTP cache** system similar to those used by browsers.

---

## 🌐 What the Proxy Server Does

- Speeds up network requests by caching responses.
- Reduces traffic to backend servers.
- Can be modified to:
  - Block certain websites.
  - Encrypt outgoing requests.
  - Mask client IP addresses.

---

## ⚠️ Limitations

- If a URL triggers multiple internal client requests (like images, scripts), cache stores each separately. During retrieval, only one chunk might be sent—causing incomplete site loading.
- Cache elements have a **fixed size** — large responses/websites may not be cached completely.

---

## 🛠️ Possible Extensions

- Use **multiprocessing** instead of multithreading for better CPU-bound performance.
- Add filters for **blocking or allowing specific websites**.
- Extend to handle more HTTP methods like **POST**, **PUT**, etc.

---

## ▶️ How to Run

```bash
$ git clone https://github.com/Lovepreet-Singh-LPSK/MultiThreadedProxyServerClient.git
$ cd MultiThreadedProxyServerClient
$ make all
$ ./proxy <port_number>
```
### DEMO

