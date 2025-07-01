# Kubernetes Node.js App with MongoDB

This project deploys a **Node.js** application backed by a **MongoDB** database in a **Kubernetes cluster** using best practices like **ConfigMaps**, **Secrets**, **Services**, and **multi-stage Docker builds**.

---

## 🧰 Tech Stack

- **Node.js** (Express)
- **MongoDB**
- **Docker** (multi-stage builds)
- **Kubernetes** (KinD / Minikube)
- **ConfigMaps** & **Secrets**
- **ClusterIP** services
- **NGINX** (for load balancing, optional)
- **GitHub** (source versioning)

---

## 📦 Features

- RESTful API for user signup/authentication
- Secure config via Kubernetes Secrets
- Auto-scaling with Deployment replicas
- Health-checked MongoDB pod with persistent storage
- Environment variable injection from ConfigMaps
- Internal DNS-based service discovery

---

## 🚀 Project Structure


├── src/
│ ├── index.Router.js
│ └── utils/
├── Dockerfile
├── k8s/
│ ├── deployment.yaml
│ ├── service.yaml
│ ├── configmap.yaml
│ └── secret.yaml
└── README.md


Build and Push the Docker image
docker build -t yossefazozz/k8s_nodejs:v2.0 .
docker push yossefazozz/k8s_nodejs:v2.0

Apply Kubernetes configs
kubectl apply -f k8s/

🔐 Environment Variables

Test URL
curl -X POST http://<NodeIP>:<NodePort>/auth/signup \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "youssef",
    "lastName": "azozz",
    "userName": "azozzprof",
    "email": "test@example.com",
    "password": "password123",
    "cPassword": "password123",
    "age": 23,
    "phone": "01113879559",
    "role": "normal"
  }'
