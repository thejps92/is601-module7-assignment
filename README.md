# QR Code Generator - Dockerized Application

A Python-based QR code generator that runs inside a Docker container. It takes a URL as input and outputs a timestamped QR code image.

## Features

- Generates QR codes from any valid URL
- Configurable fill and background colors via environment variables
- Runs as a non-root user inside the container for security
- Outputs QR codes with timestamped filenames

## Prerequisites

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Quick Start

### Using Docker Compose

```bash
docker compose up --build
```

This builds the image and generates a QR code. The output `.png` file will appear in the `qr_codes/` folder.

### Using Docker Run

```bash
docker build -t qr-code-generator-app .
docker run --rm -v "${PWD}/qr_codes:/app/qr_codes" qr-code-generator-app
```

### Custom URL

```bash
docker run --rm -v "${PWD}/qr_codes:/app/qr_codes" qr-code-generator-app --url https://www.njit.edu
```

## Environment Variables

| Variable | Description | Default |
|---|---|---|
| `QR_CODE_DIR` | Directory to save QR codes | `qr_codes` |
| `FILL_COLOR` | QR code fill color | `red` |
| `BACK_COLOR` | QR code background color | `white` |

## Project Structure

```
├── .github/workflows/  # GitHub Actions CI
├── qr_codes/           # Generated QR code output
├── compose.yaml        # Docker Compose configuration
├── Dockerfile          # Docker image definition
├── main.py             # Application entry point
└── requirements.txt    # Python dependencies
```