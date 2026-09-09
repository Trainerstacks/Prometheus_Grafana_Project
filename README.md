# 📊 Prometheus_Grafana_Project

A comprehensive monitoring solution combining Spring Boot application deployment with Prometheus and Grafana for real-time metrics visualization.

---

## 🎯 Project Overview

This project demonstrates:
- ✅ Spring Boot REST API application
- ✅ Docker containerization
- ✅ Prometheus metrics collection
- ✅ Grafana dashboards & visualization

---

## 📋 Prerequisites

- Java 17+
- Docker & Docker Compose
- kubectl (for Kubernetes)
- Prometheus server
- Grafana server
- Maven or Gradle
- Git

---

## 🚀 Quick Start

### 1. Clone Repository
```bash
git clone https://github.com/Trainerstacks/Prometheus_Grafana_Project.git
cd Prometheus_Grafana_Project
```

### 2. Build Application
```bash
# Using Maven
mvn clean package

# Or Gradle
./gradlew clean build
```

### 3. Run with Docker
```bash
# Build Docker image
docker build -t prometheus-app:latest .

# Run container
docker run -d -p 8080:8080 prometheus-app:latest
```

### 4. Start Monitoring Stack
```bash
# Prometheus
docker run -d --name=prometheus -p 9090:9090 -v $(pwd)/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus

# Grafana
docker run -d --name=grafana -p 3000:3000 grafana/grafana

# Node Exporter (system metrics)
docker run -d --name=node-exporter -p 9100:9100 prom/node-exporter
```

---

## 📊 Monitoring Endpoints

| Service | URL | Purpose |
|---------|-----|---------|
| **Application** | `http://localhost:8080` | Spring Boot app |
| **Prometheus** | `http://localhost:9090` | Metrics server |
| **Grafana** | `http://localhost:3000` | Dashboard UI |
| **Node Exporter** | `http://localhost:9100/metrics` | System metrics |

---

## ⚙️ Prometheus Configuration

### prometheus.yml
```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: prometheus
    static_configs:
      - targets:
          - localhost:9090

  - job_name: node-exporter
    static_configs:
      - targets:
          - localhost:9100

  - job_name: app-server
    static_configs:
      - targets:
          - localhost:8080/actuator/prometheus
```

---

## 🖥️ Grafana Setup

1. Access: `http://localhost:3000`
2. Default credentials: `admin` / `admin`
3. Add Prometheus data source:
   - URL: `http://prometheus:9090`
4. Import dashboards for visualization

---

## 🐛 Troubleshooting

**Prometheus not scraping metrics?**
- Check prometheus.yml syntax
- Verify targets are accessible
- Check firewall rules

**Grafana not connecting to Prometheus?**
- Verify data source URL
- Check network connectivity
- Use internal Docker network names

**Application not exposing metrics?**
- Add Spring Boot Actuator dependency
- Enable Prometheus endpoint in application.properties

---

## 📖 Documentation Links

- [Prometheus Docs](https://prometheus.io/docs/)
- [Grafana Docs](https://grafana.com/docs/)
- [Spring Boot Actuator](https://spring.io/guides/gs/actuator-service/)
- [Docker Docs](https://docs.docker.com/)

---

## 👥 Contributors

- **Trainerstacks** - Initial commit with Thymeleaf and Spring Security dependencies

---

## 📄 License

This project is licensed under the MIT License.

---

## 📞 Support

For issues or questions, please open a GitHub issue.

---

**Happy Monitoring! 🚀📊**

Save this as README.md in your repo root and customize the URLs/names to match your setup! ✅
