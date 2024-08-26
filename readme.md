# Minecraft Server Setup with NeoProtect, ngrok, and GeyserMC

This repository contains instructions and configuration files to set up a Minecraft server with DDoS protection (NeoProtect), IP obfuscation (ngrok), and cross-play support (GeyserMC).

## Prerequisites

- Minecraft server (Java Edition)
- NeoProtect account
- ngrok account
- GeyserMC plugin
- Java installed on the server

## Setup Guide

### 1. Install ngrok

- Download and install ngrok from [ngrok.com](https://ngrok.com/).
- Start ngrok to expose your Minecraft server:
  ```bash
  ngrok tcp 25565
Note the public ngrok IP and port (e.g., tcp://0.tcp.ngrok.io:12345).
