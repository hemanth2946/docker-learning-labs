# Docker Learning Labs

A hands-on repository for learning Docker step by step, from images and containers to Docker Compose, health checks, image registries, and a real-world sandbox optimization project.

The goal is to document practical experiments, commands, troubleshooting notes, and lessons learned—not just collect tutorials.

## Learning roadmap

- [ ] **01 — Images and containers:** pull images, run containers, inspect logs, and manage container lifecycle.
- [ ] **02 — Dockerfile:** containerize a small Node.js application and understand build layers and caching.
- [ ] **03 — Ports and networking:** publish ports and connect containers through a Docker network.
- [ ] **04 — Volumes:** persist data beyond a container's lifecycle.
- [ ] **05 — Environment variables:** configure applications without hardcoding secrets.
- [ ] **06 — Docker Compose:** run a multi-container application from one Compose file.
- [ ] **07 — Multi-stage builds:** reduce production image size.
- [ ] **08 — Image registry:** tag, publish, and pull images from a registry.
- [ ] **09 — Health checks:** report service readiness and coordinate dependencies.
- [ ] **10 — Capstone:** investigate and optimize startup for a multi-container Broken Crystals security lab.

## Repository structure

```text
docker-learning-labs/
├── README.md
├── LICENSE
├── .gitignore
├── 01-images-containers/
├── 02-dockerfile/
│   └── node-app/
├── 03-ports-networking/
├── 04-volumes/
├── 05-environment-variables/
├── 06-docker-compose/
├── 07-multistage-builds/
├── 08-image-registry/
├── 09-healthchecks/
└── projects/
    └── broken-crystals-optimization/
```

Create each folder as you start that topic. Keep examples small, reproducible, and accompanied by a short explanation of what you learned.

## Prerequisites

- Docker Desktop on Windows/macOS, or Docker Engine on Linux
- A terminal (PowerShell, Windows Terminal, Bash, or equivalent)
- Git
- Node.js for the Node.js application exercise

Verify Docker is available:

```bash
docker --version
docker info
docker run --rm hello-world
```

## First exercise: run Nginx

```bash
docker pull nginx:alpine
docker run -d --name my-nginx -p 8080:80 nginx:alpine
docker ps
```

Open [http://localhost:8080](http://localhost:8080) in your browser. Then inspect and clean up the container:

```bash
docker logs my-nginx
docker inspect my-nginx
docker stop my-nginx
docker rm my-nginx
```

## Example topics to document

For each lab, try to include:

1. **Goal** — what you are trying to understand.
2. **Commands** — the exact commands you ran.
3. **Explanation** — what each important command or option does.
4. **Result** — expected output or a screenshot.
5. **Troubleshooting** — errors you encountered and how you resolved them.
6. **Cleanup** — how to remove containers, networks, and volumes created by the lab.

## Capstone: Broken Crystals startup optimization

The capstone will explore a multi-container security lab. The intended investigation includes:

- Measure baseline startup time and record the environment.
- Identify time spent installing dependencies, downloading source, building images, pulling service images, fixed sleeps, and health checks.
- Evaluate a prebuilt application image to avoid building the app image on every sandbox startup.
- Use Docker Compose where appropriate to describe services and dependencies.
- Prefer health checks and readiness checks over arbitrary fixed delays.
- Measure results under both cold-cache and warm-cache conditions.

Do not assume a speedup before measuring it. Record the baseline, methodology, and results so others can reproduce the comparison.

**Important:** Broken Crystals is a separate upstream project. Review its license and terms before redistributing its source, modified code, or built images. This repository's license applies to your original work only; it does not override licenses for third-party projects or dependencies.

## Engineering practices

- Pin image versions or digests for reproducible examples where practical.
- Never commit `.env` files, passwords, API keys, tokens, or other secrets.
- Use `.env.example` with placeholder values when configuration documentation is needed.
- Avoid running containers as root when practical and appropriate.
- Keep images small, use `.dockerignore`, and take advantage of build caching.
- Document resource requirements and cleanup commands.
- Add automated checks as the project grows.

## Progress

Update the checklist above as each lab is completed. Add short notes about what you learned and link to any capstone results.

## License

This repository's original work is licensed under the MIT License. See [LICENSE](LICENSE). Third-party projects, assets, and dependencies remain under their own licenses.
