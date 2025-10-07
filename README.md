# CI/CD with Jenkins — Flask & Express

## Overview
This repo is deployed via Jenkins pipeline to EC2 using pm2. The Jenkinsfiles are in repo root.

## Requirements
- Ubuntu EC2 instance
- Jenkins running at http://<EC2_PUBLIC_IP>:8080
- SSH deploy key added to GitHub

## How Jenkins deploys
1. Webhook triggers Jenkins on push.
2. Jenkins checks out repo, installs dependencies (Python venv / npm ci), runs tests (optional).
3. Jenkins rsyncs workspace to /home/deployer/<app>.
4. Jenkins runs pm2 restart or pm2 start to apply new code.

## How to reproduce
- Add deployer and jenkins sudoers entry (see scripts in this repo)
- Configure Jenkins credentials (SSH key)
- Add webhook: http://<EC2_PUBLIC_IP>:8080/github-webhook/

## Evidence included
- Jenkins Console Output screenshot
- curl outputs for both apps
- pm2 list, systemctl jenkins outputs
