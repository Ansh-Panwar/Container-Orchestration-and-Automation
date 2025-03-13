# 🚀 Docker Volume Persistence 🐳

## 📌 Introduction

This guide explores how to use Docker bind mounts with a Linux container to ensure data persists even after a container is removed. Bind mounts allow a local directory on the host machine to be accessible within a container, making it a useful technique for managing persistent storage.

---

## 🔧 Steps & Observations

### 🏗 Step 1: Running a Container with a Bind Mount

You executed:

```sh
docker run -dit --name ubuntu_with_bind_mount -v /home/ansh/docker_data:/data ubuntu:latest sh
```

### 🔍 What Happened?

- Since `ubuntu:latest` was not found locally, Docker pulled it from the official repository.
- A new container named `ubuntu_with_bind_mount` was created.
- The `-v` flag mounted the local directory `/home/ansh/docker_data` to `/data` inside the container.
- The container started a shell (`sh`) in detached mode.

---

## 📄 Step 2: Creating a File Inside the Bind Mount

Inside the container, you created a file:

```sh
docker exec -it ubuntu_with_bind_mount sh -c "echo 'Hello, Ansh!' > /data/testfile.txt"
```

### 🔍 What Happened?

- The command executed a shell inside the running container.
- It created a file `testfile.txt` inside `/data` and wrote "Hello, Ansh!" into it.
- Since `/data` is a bind-mounted directory, the file was actually stored in `/home/ansh/docker_data` on the host machine.

---

## ✅ Step 3: Verifying the File Exists

To check the contents:

```sh
docker exec -it ubuntu_with_bind_mount sh -c "cat /data/testfile.txt"
```

### 📌 Output:

```plaintext
Hello, Ansh!
```

This confirms that the file was successfully created and is accessible inside the container. 🎉

---

## 🗑 Step 4: Removing the First Container

You removed the container:

```sh
docker rm -f ubuntu_with_bind_mount
```

### 🔍 What Happened?

- The container was forcefully stopped and removed.
- However, since `testfile.txt` was stored in the bind-mounted directory, it remained intact on the host system. 🏠

---

## 🔄 Step 5: Creating a New Container with the Same Bind Mount

You started a new container:

```sh
docker run -dit --name new_ubuntu -v /home/ansh/docker_data:/data ubuntu sh
```

### 🔍 What Happened?

- A new container named `new_ubuntu` was created.
- The same bind-mounted directory (`/home/ansh/docker_data`) was mounted to `/data` inside the container.

---

## 🔎 Step 6: Verifying File Persistence

Inside the new container, you checked if `testfile.txt` still exists:

```sh
docker exec -it new_ubuntu sh -c "cat /data/testfile.txt"
```

### 📌 Output:

```plaintext
Hello, Ansh!
```

This confirms that bind mounts allow data to persist across container lifecycles. 🔥

---

## 🎯 Conclusion

✅ Bind mounts provide a reliable way to persist data across multiple container instances.  
✅ Deleting a container does not remove data stored in the bind-mounted directory.  
✅ Any new container using the same mount point can access previously stored data.  
✅ Bind mounts facilitate file sharing between containers and persistent storage beyond a container’s lifecycle.  

---

## 🚀 Next Steps

- 🛠 Experiment with **named volumes** (`docker volume create`) for better volume management.
- 🐳 Try using bind mounts with different container images.
- 🔐 Explore file permission settings to control access between host and container.

🎯 This guide highlights the benefits of using bind mounts in Docker. Keep experimenting and happy coding! 🚀

