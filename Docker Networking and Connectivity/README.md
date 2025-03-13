# 🚀 Docker Networking & Connectivity

## 📌 Objective

The goal of this exercise is to explore and demonstrate network isolation in Docker containers. We will examine how containers within the same custom bridge network can communicate, while those on different networks remain isolated. Understanding this is crucial for securing microservices and containerized applications.

---

## 🌐 Introduction to Docker Networking

Docker networking is fundamental for containerized applications, allowing containers to communicate while ensuring security and isolation. Docker provides several networking options:

### 🔹 Types of Docker Networks:

1. **Bridge Network (Default)** – Allows communication between containers using internal IPs unless restricted.
2. **Custom Bridge Network** – Offers better control and supports name-based resolution.
3. **Host Network** – Attaches containers directly to the host’s network stack.
4. **Overlay Network** – Enables communication across multiple hosts (Docker Swarm).
5. **Macvlan Network** – Assigns a MAC address to each container, making them appear as separate devices.
6. **None Network** – Completely disables networking.

For this demonstration, we focus on the **custom bridge network**, which improves control and network isolation.

---

## ⚡ Why Use a Custom Bridge Network?

A custom bridge network offers several advantages:

✅ **Improved Security** – Containers on different networks are isolated by default.
✅ **Better Performance** – Direct communication without host networking stack overhead.
✅ **DNS-Based Resolution** – Containers communicate via names instead of IPs.
✅ **Greater Control** – Define specific subnets, IP ranges, and gateways.

To demonstrate, we create a **custom bridge network** called **ansh-bridge** and connect multiple containers.

---

## 🔧 Step 1: Creating a Custom Bridge Network

```sh
docker network create --driver bridge --subnet 172.20.0.0/16 --ip-range 172.20.240.0/20 ansh-bridge
```

### 🔍 Explanation:

- `--driver bridge` → Uses the default bridge network mode.
- `--subnet 172.20.0.0/16` → Defines the network’s IP range.
- `--ip-range 172.20.240.0/20` → Allocates IPs dynamically.

---

## 🚀 Step 2: Running Containers in the Custom Network

### Running Redis Container (**ansh-database**)

```sh
docker run -itd --net=ansh-bridge --name=ansh-database redis
```

### Running BusyBox Container (**ansh-server-A**)

```sh
docker run -itd --net=ansh-bridge --name=ansh-server-A busybox
```

### 📌 Check Container IPs

```sh
docker network inspect ansh-bridge
```

#### Expected Output:

```plaintext
 ansh-database: 172.20.240.1
 ansh-server-A: 172.20.240.2
```

---

## 🔄 Step 3: Testing Communication Between Containers

### Ping from **ansh-database** to **ansh-server-A**

```sh
docker exec -it ansh-database ping 172.20.240.2
```

### Ping from **ansh-server-A** to **ansh-database**

```sh
docker exec -it ansh-server-A ping 172.20.240.1
```

✅ **Expected Outcome:** Both containers should successfully ping each other.

---

## 🚧 Step 4: Demonstrating Network Isolation with a Third Container

We add another container (**ansh-server-B**) on the **default bridge network**.

```sh
docker run -itd --name=ansh-server-B busybox
```

### 📌 Get IP of **ansh-server-B**

```sh
docker inspect -format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' ansh-server-B
```

*(Example IP: `172.17.0.2`)*

---

## ❌ Step 5: Testing Communication Between Different Networks

### Ping from **ansh-database** to **ansh-server-B**:

```sh
docker exec -it ansh-database ping 172.17.0.2
```

🚨 **Expected Outcome:** The ping should fail, as they are on different networks.

---

## 🔍 Step 6: Confirming Network Isolation

### Inspect Networks

```sh
docker network inspect ansh-bridge
docker network inspect bridge
```

✅ **ansh-bridge** should contain **ansh-database** & **ansh-server-A**.  
✅ **bridge** should contain **ansh-server-B**.

---

## 🏆 Conclusion

- Containers in the **same** network can communicate.
- Containers in **different** networks are **isolated by default**.
- Docker’s networking model ensures security and separation unless explicitly connected.

🚀 **Now you have mastered Docker Bridge Networking!** 🎯

