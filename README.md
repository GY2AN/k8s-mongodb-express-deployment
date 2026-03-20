# 🚀 Kubernetes MongoDB + Mongo Express Deployment

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/46bfed1e-1677-42a5-84a1-8cb778718e06" />


This project demonstrates a production-style Kubernetes setup for deploying a MongoDB database with a Mongo Express web UI.

It showcases key Kubernetes concepts such as Deployments, Services, ConfigMaps, Secrets, and inter-service communication.

---

## 📌 Tech Stack

* Kubernetes (Minikube)
* Docker
* MongoDB
* Mongo Express
* YAML (K8s manifests)

---

## 🧠 Key Concepts Demonstrated

* ✅ Pod-to-Service communication using DNS
* ✅ Secure credential management using Secrets
* ✅ Environment configuration using ConfigMaps
* ✅ Multi-container architecture (DB + UI)
* ✅ Debugging Kubernetes networking issues
* ✅ Using connection URLs for reliable service integration

---

## 📂 Project Structure

```
manifests/
├── mongo.yaml              # MongoDB Deployment + Service
├── mongo-express.yaml      # Mongo Express Deployment + Service
├── mongo-configmap.yaml    # Database service config
├── mongo-secret.yaml       # Credentials (Base64 encoded)
```

---

## ⚙️ Setup Instructions

### 1️⃣ Start Minikube

```bash
minikube start
```

---

### 2️⃣ Apply Kubernetes Manifests

```bash
kubectl apply -f manifests/
```

---

### 3️⃣ Verify Resources

```bash
kubectl get pods
kubectl get svc
```

---

### 4️⃣ Access Mongo Express UI

```bash
minikube service mongo-express-service
```

---

### 🔐 Login Credentials

```
Username: admin
Password: pass
```

---

## 🔍 Architecture Overview

* MongoDB runs as a Deployment with a ClusterIP Service
* Mongo Express connects using internal DNS (`mongodb-service`)
* Credentials are injected via Kubernetes Secrets
* ConfigMap provides service discovery configuration

---

## 🧪 Troubleshooting

### ❌ Mongo Express cannot connect to MongoDB

* Ensure service name matches ConfigMap
* Verify endpoints:

```bash
kubectl describe svc mongodb-service
```

---

### ❌ Environment variables not updating

```bash
kubectl rollout restart deployment mongo-express
```

---

## 📈 Future Improvements

* Add Persistent Volume (data persistence)
* Use Ingress instead of NodePort
* Implement authentication best practices
* Helm chart packaging
* CI/CD pipeline integration

---

## 💡 Key Learning

This project highlights a real-world issue where:

* Environment variables were correctly set
* But application fallback behavior caused connection failures

The fix involved switching to:

```
ME_CONFIG_MONGODB_URL
```

---

## 🤝 Author

Gyan Prakash
Frontend Developer → Transitioning into DevOps & Cloud 🚀

---

## ⭐ If you found this useful

Give it a ⭐ on GitHub!
