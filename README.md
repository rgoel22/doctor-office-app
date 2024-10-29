# Docker development setup

## Prerequisites

- Pull this repository `git clone https://github.com/reubenthomas107/doctor-office-app.git`

## Steps to Build and Start the Services

### 1. Build the services without using the cache:
```bash
docker-compose build --no-cache
```

### 2. Start the services in detached mode:

```bash
docker-compose up -d
```

### 3. Navigate to the application in your browser:

Open [http://localhost:3001/](http://localhost:3001/)