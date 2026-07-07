# Lens

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

An open-source tool for flexibly visualizing events, tracking metrics, and tracing the entire lifecycle of your artifacts across multiple repositories by leveraging Actions in git. 

## Key Features

- **Immediate Feedback Loops**: Lens pushes real-time CI/CD metrics directly to a unified dashboard, ensuring that failing checks and deployment errors are caught and fixed faster without developers having to manually hunt through GitHub Actions logs.
- **Breaking Down Silos**: Lens aggregates data from across your entire polyrepo ecosystem into one centralized view. This ensures that everything from deployment frequency to test pass rates can be easily understood by everyone who has a stake, not just the DevOps engineers.
- **Frictionless Artifact Tracking**: By leveraging custom workflow tags via the Lens Action, you can seamlessly trace a single artifact (like an application version or a Docker image tag) as it flows across multiple repositories, without digging through individual git commit histories.
- **Secure OIDC Ingestion**: Lens securely verifies telemetry from GitHub Actions using native OIDC federation.
- **Agnostic Architecture**: Deploy anywhere. Use Docker Compose for a quick single-node setup, or deploy directly to Kubernetes and AWS ECS.

## Inspiration

DevOps often preaches providing immediate feedback by shifting checks left in the development cycle so mistakes are caught and fixed faster. Another goal is breaking down organizational silos so that everything can be understood by everyone who has a stake.

An issue I have consistently run into is a lack of that immediate feedback and dealing with siloed information when it comes to git repositories and their artifacts. This leaves me with a limited understanding of how repositories are grouped, unable to view the metrics I care about, or track an artifact, like an application version, across multiple repositories without significant friction.

![Lens Dashboard](hero.png)

## Ecosystem Overview

Lens uses a modular, polyrepo architecture. This repository serves as the official front door, while the actual application logic is broken down into the following core components:

- [**`lens-backend`**](https://github.com/nickdchristian/lens-backend) [![Release](https://img.shields.io/github/v/release/nickdchristian/lens-backend?label=version)](https://github.com/nickdchristian/lens-backend/releases) [![Build](https://img.shields.io/github/actions/workflow/status/nickdchristian/lens-backend/ci.yml?label=build)](https://github.com/nickdchristian/lens-backend/actions)<br>The core FastAPI backend that stores deployment data and handles OAuth2.
- [**`lens-frontend`**](https://github.com/nickdchristian/lens-frontend) [![Release](https://img.shields.io/github/v/release/nickdchristian/lens-frontend?label=version)](https://github.com/nickdchristian/lens-frontend/releases) [![Build](https://img.shields.io/github/actions/workflow/status/nickdchristian/lens-frontend/ci.yml?label=build)](https://github.com/nickdchristian/lens-frontend/actions)<br>The visual dashboard built with Vite and Lit.
- [**`lens-action`**](https://github.com/nickdchristian/lens-action) [![Release](https://img.shields.io/github/v/release/nickdchristian/lens-action?label=version)](https://github.com/nickdchristian/lens-action/releases)<br>The official GitHub Action that securely sends deployment events to the Lens backend.
- [**`lens-quickstart`**](https://github.com/nickdchristian/lens-quickstart)<br>The official deployment templates and configuration guides for self-hosting.


## Quick Start / Deployment

Ready to deploy Lens for your team? We've created a dedicated deployment repository that contains everything you need to get up and running securely in under 5 minutes.

👉 **[Go to the Lens Quickstart Repository](https://github.com/nickdchristian/lens-quickstart)**

The quickstart includes:
- A `setup.sh` script to auto-generate cryptographic secrets.
- A vendor-agnostic `docker-compose.yml` pulling our pre-built `ghcr.io` images.
- An `nginx.conf` template for reverse proxying and handling `X-Forwarded-Proto` HTTPS headers.
- Comprehensive guides for both single-node servers and cloud-native (AWS/Kubernetes) deployments.

## Contributing & Issues

Since Lens is split across multiple repositories, we use **this** repository as the central hub for all issue tracking. 

Whether you've found a bug in the web UI, the backend API, or the GitHub Action, please [open an issue here](https://github.com/nickdchristian/lens/issues/new)!
