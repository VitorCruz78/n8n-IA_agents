# n8n-IA_agents
centralizar estudos de n8n e agentes de IA

# Step 1: Install Docker and Docker Compose
    sudo apt update
    sudo apt install docker.io docker-compose-plugin -y
    sudo systemctl enable --now docker

# Step 2: Create docker-compose.yml
    services:
      n8n:
        image: n8nio/n8n:latest
        container_name: n8n
        restart: always
        ports:
          - "5678:5678"
        environment:
          - N8N_BASIC_AUTH_ACTIVE=true
          - N8N_BASIC_AUTH_USER=user
          - N8N_BASIC_AUTH_PASSWORD=password
          - N8N_HOST=localhost
          - N8N_PORT=5678
          - N8N_PROTOCOL=http
          - NODE_ENV=production
        volumes:
          - ~/.n8n:/home/node/.n8n
    
# Step 3: Prepare Volume Directory
    mkdir -p ~/.n8n
    chmod -R 755 ~/.n8n

# Step 4: Start n8n
    docker compose up -d

# Step 5: Access n8n
    http://localhost:5678

# Logs
    docker logs n8n
