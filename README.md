# ssh-test

A simple Docker container with an SSH server for testing purposes.

## Features

- Ubuntu 22.04 based Docker container
- OpenSSH server configured with password authentication
- Pre-configured user: `plfanzen` with password: `plfanzy`
- Automated CI/CD with GitHub Actions

## Usage

### Building the Docker Image

```bash
docker build -t ssh-server .
```

### Running the Container

```bash
docker run -d -p 2222:22 --name ssh-test ssh-server
```

### Connecting via SSH

```bash
ssh -p 2222 plfanzen@localhost
```

When prompted, enter the password: `plfanzy`

Alternatively, using sshpass:

```bash
sshpass -p 'plfanzy' ssh -o StrictHostKeyChecking=no -p 2222 plfanzen@localhost
```

### Stopping the Container

```bash
docker stop ssh-test
docker rm ssh-test
```

## CI/CD

This project includes a GitHub Actions workflow that:
1. Builds the Docker image
2. Runs the container
3. Tests SSH connectivity
4. Reports results

The workflow runs automatically on pushes and pull requests to the main/master branch.