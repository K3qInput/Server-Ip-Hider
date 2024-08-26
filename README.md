
# Minecraft Server-IP-Hider using NeoProtect, ngrok, and GeyserMC

This repository provides the necessary instructions and configuration files to set up a Minecraft server with DDoS protection (NeoProtect), IP obfuscation (ngrok), and cross-play support (GeyserMC).

## Prerequisites

- **Minecraft server (Java Edition)**
- **NeoProtect account**
- **ngrok account**
- **GeyserMC plugin**
- **Java installed on the server**

## Setup Guide

### 1. Install ngrok

- Download and install ngrok from [ngrok.com](https://ngrok.com/).
- Start ngrok to expose your Minecraft server:
  ```bash
  ngrok tcp 25565
  ```
- Note the public ngrok IP and port (e.g., `tcp://0.tcp.ngrok.io:12345`).

### 2. Set Up NeoProtect

- Sign up at [NeoProtect](https://neoprotect.net/) and register your server.
- In the NeoProtect dashboard, set the backend IP to the ngrok IP and port (e.g., `0.tcp.ngrok.io:12345`).
- NeoProtect will now route traffic through their DDoS protection network before forwarding it to your ngrok tunnel.

### 3. Install and Configure GeyserMC

- Download the GeyserMC plugin from [geysermc.org](https://geysermc.org/).
- Place the `Geyser-Spigot.jar` file in your server’s `plugins` folder.
- Configure `config.yml` in the `Geyser` folder:
  ```yaml
  remote:
    address: your_neoprotect_ip_or_domain
    port: 25565
  bedrock:
    address: 0.0.0.0
    port: 19132
  ```
- To allow Bedrock players to connect, run a separate ngrok tunnel for the Bedrock port:
  ```bash
  ngrok tcp 19132
  ```

### 4. Update NeoProtect for Bedrock Support

- In NeoProtect, add the Bedrock port (`19132`) to the IP forwarding settings to ensure Bedrock players are routed correctly.

### 5. Start the Minecraft Server

- Start your Minecraft server as usual.
- Players can connect using the NeoProtect IP or domain for Java Edition, and Bedrock players can connect via the specified Bedrock port.

### 6. Testing the Setup

- Verify that both Java and Bedrock clients can connect to the server.
- Monitor NeoProtect and ngrok dashboards to ensure proper traffic routing and DDoS protection.

## Considerations

- **Dynamic IPs with ngrok:** If ngrok changes its IP, you will need to update the NeoProtect settings, which can cause downtime.
- **Alternative Options:** For more stability, consider using a static IP (e.g., from a VPS) instead of ngrok.

## Additional Information

- [GeyserMC Documentation](https://geysermc.org/docs/)
- [ngrok Documentation](https://ngrok.com/docs)
- [NeoProtect Documentation](https://neoprotect.net/docs/)

## License

This project is licensed under the MIT License.
```

