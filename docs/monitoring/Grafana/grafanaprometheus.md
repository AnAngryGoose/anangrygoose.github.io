# Grafana & Prometheus Monitoring 

---
```yaml
services:

### --- Prometheus: Metrics Database  --- ##
  prometheus:
    image: prom/prometheus:latest
    container_name: prometheus
    restart: unless-stopped
    command:
      - '--config.file=/etc/prometheus/prometheus.yml'
      - '--storage.tsdb.path=/prometheus'
      - '--storage.tsdb.retention.time=15d'
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
      - /mnt/appdata/grafana/prometheus_data:/prometheus
    ports:
      - 9090:9090

### --- Grafana: Visualization Dashboard --- ##
  grafana:
    image: grafana/grafana:latest
    container_name: grafana
    restart: unless-stopped
    volumes:
      - /mnt/appdata/grafana/grafana_data:/var/lib/grafana
    ports:
      - 3000:3000
    environment:
      - GF_SECURITY_ADMIN_USER=admin
      - GF_SECURITY_ADMIN_PASSWORD=admin  # Change this
      - GF_USERS_ALLOW_SIGN_UP=false

 ### --- Node Exporter -- Host System Metrics --- ##

  node-exporter:
    image: quay.io/prometheus/node-exporter:latest
    container_name: node-exporter
    restart: unless-stopped
    volumes:
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - '/:/host:ro,rslave'
      - /:/rootfs:ro
    command:
      - '--path.procfs=/host/proc'
      - '--path.sysfs=/host/sys'
      - '--path.rootfs=/host'
      - '--collector.filesystem.mount-points-exclude=^/(sys|proc|dev|host|etc)($$|/)'
    ports:
      - 9100:9100

### --- OPNsense Exporter: Firewall Metrics --- ##
  opnsense-exporter:
    image: ghcr.io/athennamind/opnsense-exporter:latest
    container_name: opnsense-exporter
    restart: always
    command:
      - --opnsense.protocol=https
      - --opnsense.address=192.168.0.1:4043 # address of opnsense UI 
      - --exporter.instance-label=opnsense-exporter
      - --web.listen-address=:9200 
      #- --exporter.disable-arp-table
      #- --exporter.disable-cron-table
      #- ....
    environment:
      OPNSENSE_EXPORTER_OPS_API_KEY: "OPNSENSEAPIKEY"
      OPNSENSE_EXPORTER_OPS_API_SECRET: "OPNSENSESECRET
    ports:
      - "9200:9200"
  ### --- cAdvisor: Container Metrics --- ##
  # Monitors Docker Container Stats
  cadvisor:
    image: gcr.io/cadvisor/cadvisor:latest
    container_name: cadvisor
    restart: unless-stopped
    privileged: true
    devices:
      - /dev/kmsg
    volumes:
      - /:/rootfs:ro
      - /var/run:/var/run:ro
      - /sys:/sys:ro
      - /var/lib/docker/:/var/lib/docker:ro
      - /dev/disk/:/dev/disk:ro
    ports:
      - 8080:8080
```