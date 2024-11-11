# 🎬 Streaming Platform - Scaled-Down Microservices Project (Netflix-style)

**Project Description**  
This project is a streaming platform designed with a microservices architecture, allowing users to view and subscribe to live video events and on-demand content. Inspired by popular streaming platforms, this system leverages multiple backend technologies to deliver a modular and scalable experience.

**Project Goal**  
The goal of this project is to serve as a learning platform for working with microservices and integrating modern technologies such as **Golang, Kafka, gRPC, NGINX, MongoDB, PostgreSQL, Elasticsearch, and Docker/Kubernetes**.

## 🚀 Main Features

- **Real-Time Video Ingestion**: Processes and distributes live streaming video.
- **Event Management**: Allows the creation, scheduling, and viewing of video events.
- **Subscription System**: Manages user subscriptions to channels and events.
- **Real-Time Notifications**: Notifies users about upcoming events, updates, and recommendations.
- **Content Search**: Enables users to search for events and content by keywords.
- **Audience Analytics**: Tracks viewer count, viewing duration, and generates real-time usage statistics.

## 🏗️ General Architecture

The platform consists of several independent microservices that communicate with each other via **Kafka** for asynchronous events and **gRPC** for direct communication. Each microservice is deployed independently for scalability and efficiency.

### Key Microservices

1. **Video Ingest Service**
   - Provides ingestion and distribution of live video.
   - Managed with **NGINX** and streaming protocols like RTMP.

2. **Events Service**
   - Manages the creation, updating, and querying of video events.
   - Uses **MongoDB** to store event metadata.

3. **Subscriptions Service**
   - Manages user subscriptions to channels and events.
   - Stores data in **PostgreSQL** for relational queries.

4. **Notifications Service**
   - Sends notifications to users in real-time.
   - Utilizes **Kafka** for asynchronous distribution of notification events.

5. **Search Service**
   - Provides search functionalities for events and content.
   - Stores data in **Elasticsearch** for fast searches and content filtering.

6. **Analytics Service**
   - Tracks usage metrics, viewing activity, and engagement.
   - Uses **Kafka** to receive real-time event data and stores metrics in **MongoDB**.

## 📚 Technologies Used

- **Programming Language**: Golang
- **Messaging and Events**: Kafka
- **Service Communication**: gRPC
- **Data Storage**:
  - **MongoDB**: Event metadata and temporary storage for viewing data.
  - **PostgreSQL**: Relational data for users and subscriptions.
  - **Elasticsearch**: Search engine for events and notifications.
- **Web Server and Load Balancer**: NGINX
- **Containerization and Orchestration**: Docker and Kubernetes

## 📂 Project Structure

Each microservice is housed in an individual repository to maintain modularity and version control. Additionally, there are two shared repositories for common definitions and libraries.

### Repository Structure

- **Microservices**:
  - `video-ingest-service`: Video Ingestion Service.
  - `events-service`: Event Management Service.
  - `subscriptions-service`: Subscriptions Service.
  - `notifications-service`: Notifications Service.
  - `search-service`: Search Service.
  - `analytics-service`: Real-Time Analytics Service.

- **Shared Repositories**:
  - `common-protos`: Contains `.proto` files for shared gRPC definitions.
  - `common-libs`: Shared libraries for authentication, logging, configuration, etc.

## ⚙️ Setup and Deployment

### 1. Clone the Repositories

```bash
git clone https://github.com/username/video-ingest-service.git
git clone https://github.com/username/events-service.git
git clone https://github.com/username/subscriptions-service.git
git clone https://github.com/username/notifications-service.git
git clone https://github.com/username/search-service.git
git clone https://github.com/username/analytics-service.git
git clone https://github.com/username/common-protos.git
git clone https://github.com/username/common-libs.git
```

### 2. Local Environment Configuration

Each microservice includes an `.env.example` file with the required environment variables. Duplicate the file, rename it to `.env`, and configure the variables according to your local setup.

### 3. Local Deployment with Docker Compose

Each microservice includes a `docker-compose.yml` file to start the service and its local dependencies (e.g., Kafka, MongoDB, or PostgreSQL). To test a specific service:

```bash
cd events-service
docker-compose up
```

To deploy the entire platform, it’s recommended to create a central `docker-compose.yml` file pointing to the necessary services and dependencies.

### 4. Kubernetes Deployment

For Kubernetes deployment, you can use **Minikube** or **Kind** for local testing. **Helm Charts** are provided for each microservice in their respective repositories.

Basic steps for deployment in Kubernetes:

```bash
# Start Minikube or Kind
minikube start

# Deploy each microservice using Helm
helm install video-ingest ./video-ingest-service/chart
helm install events ./events-service/chart
...
```

## 🧪 Testing

Each microservice includes its own suite of unit and integration tests.

To run tests:

```bash
# Run unit tests in each service
go test ./...
```

## 📌 Roadmap and Future Features

- **Recommendation System**: Based on the user's viewing history.
- **Mobile Device API Integration**.
- **Scalability Optimization**: Improvements in orchestration and load balancing.
- **Advanced Authentication and Authorization**.

## 🎓 Learning Objective

This project will help me understand microservices architecture, using messaging, and orchestration tools in distributed environments, and how to integrate storage and search services into a streaming system.

---

**Note**: This project is a scaled-down version and is not optimized for large-scale deployment. It is primarily designed for educational and experimental purposes.

---
