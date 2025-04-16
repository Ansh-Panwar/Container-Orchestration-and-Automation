# Docker Bake - Multi-Platform Image Automation

## Repository: **Packer-Bakery-Foundation**

### Overview:
This repository streamlines the process of building Docker images across multiple platforms using **Docker Bake**. It supports concurrent builds and targets architectures such as **AMD64** and **ARM64**, making it well-suited for robust CI/CD pipelines.

---

## 🔧 What is Docker Bake?
Docker Bake enables you to define and run multiple build tasks in parallel from a single configuration file. Instead of chaining multiple `docker build` commands, you can define your logic in a file and run:

```sh
docker buildx bake
```

### **🌟 Key Advantages:**
- 🎯 **Cross-platform builds** (like Linux/AMD64 & Linux/ARM64)  
- ⚡ **Faster execution** with parallel processing  
- 📂 **Unified configuration** using HCL/YAML  
- 🔄 **Pipeline-ready** and integrates easily with CI/CD tools  

---

## 📌 How to Use

### **Step 1: Set Up `docker-bake.hcl`**
Create a file named `docker-bake.hcl` in the project root:

```hcl
group "default" {
  targets = ["python-bakery"]
}

target "python-bakery" {
  context    = "."
  dockerfile = "Dockerfile"
  platforms  = ["linux/amd64", "linux/arm64"]
  tags       = ["yourdockerhub/python-bakery:latest"]
}
```

### **Step 2: Create a `Dockerfile`**
Write a simple Dockerfile to install Python 3.9 on Ubuntu:

```dockerfile
FROM ubuntu:20.04

RUN apt-get update && apt-get install -y \
    python3.9 python3.9-venv python3.9-dev \
    && rm -rf /var/lib/apt/lists/*

CMD ["python3"]
```

### **Step 3: Build and Push**
Execute the following to build and push the image to Docker Hub:

```sh
docker buildx bake --push
```

✅ Automatically builds for both **amd64** and **arm64**  
✅ Uploads the images to your Docker repository  

---

## 🆚 Why Choose Docker Bake?

| Feature                 | `docker build` | `docker buildx bake` |
|------------------------|----------------|-----------------------|
| Multi-architecture      | ❌ Not native   | ✅ Built-in support   |
| Concurrent builds       | ❌ No           | ✅ Yes                |
| Config file (HCL/YAML) | ❌ Manual       | ✅ Structured config  |
| CI/CD integration       | ✅ Possible     | ✅ Easy               |

---

## 🧩 Final Thoughts
Docker Bake makes building cross-platform images easier, faster, and more maintainable—perfect for teams using automated pipelines and modern DevOps practices.

Need help setting this up in your CI/CD system? 🚀 Let’s make it happen!