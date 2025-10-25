# Breeznas Home Assistant Add-ons

Welcome to the repository for Adrian's Home Assistant Add-ons (BreezNAS). This repository hosts a collection of specialized add-ons designed to enhance the functionality, monitoring, and security of your Home Assistant installation.

## Add-ons Included

This repository currently features the following add-ons:

### 1. Dozzle Agent

**Real-time log viewer for your containers.**

The **Dozzle Agent** is a lightweight add-on that provides a web-based interface for viewing logs from your Docker containers in real-time. It's an essential tool for debugging and monitoring container health within your Home Assistant environment.

| Detail | Value |
| :--- | :--- |
| **Description** | Realtime log viewer for containers. Supports Docker, Swarm and K8s. |
| **Version** | `v8.14.5` |
| **Panel Access** | Yes (`Dozzle-Agent`) |
| **Exposed Port** | `7007/tcp` |

➡️ **[See the Dozzle Agent README for detailed information and configuration.](#)** (doozle/README.MD)

### 2. Docker Proxy

**A secured and filtered proxy for your Docker socket.**

The **Docker Proxy** add-on enhances the security of your Home Assistant host by allowing you to restrict which Docker API requests are accepted. It exposes a filtered version of the host Docker socket over a network port, making it safer to use with external monitoring or management tools.

| Detail | Value |
| :--- | :--- |
| **Description** | Proxy over your Docker socket to restrict which requests it accepts. |
| **Version** | `latest` |
| **Key Feature** | Endpoint filtering via Environment Variables (e.g., `CONTAINERS: "1"`, `IMAGES: "1"`) |
| **Exposed Port** | `2375/tcp` |

🛡️ **[See the Docker Proxy README for detailed security and filter configuration.](#)** (docker-proxy/README.MD)

***

## 🛠️ How to Add This Repository to Home Assistant

1.  In your Home Assistant interface, navigate to **Settings** -> **Add-ons**.
2.  Click the **Add-on Store** button (bottom right).
3.  Click the **three dots** in the top right corner and select **Repositories**.
4.  Add the following URL:

    ```
    [https://gitea.breeznas.com/Adrian/ha-addons-breeznas]
    ```

5.  Click **Add**. The add-ons listed above should now appear in your Add-on Store.

## 🔗 Repository Source

For source code, issues, and contributions, please visit:
[https://gitea.breeznas.com/Adrian/ha-addons-breeznas](https://gitea.breeznas.com/Adrian/ha-addons-breeznas)