# Docker Proxy Add-on for Home Assistant

The **Docker Proxy** add-on provides a filtered proxy over your host's Docker socket, allowing you to restrict which API requests are accepted. This enhances security by limiting external tools to only the necessary Docker commands.

* **Version:** `latest`
* **Source:** [https://github.com/Adribreezy/breeznas-addons-homeassistant](https://github.com/Adribreezy/breeznas-addons-homeassistant)
* **Image:** `tecnativa/docker-socket-proxy`

## 🛡️ Key Features

* **Security Filtering:** Restrict access to specific Docker API endpoints using environment variables (e.g., `CONTAINERS: "1"`, `IMAGES: "1"`).
* **Network Exposure:** Exposes the filtered Docker socket over a TCP port (`2375`).
* **Low-Level Access:** Utilizes necessary host permissions to proxy the Docker socket.

## ⚠️ Important Configuration Notes (Permissions and Access)

This add-on requires high-level host access to function correctly as a proxy for the Docker socket.

* `init: false` is set to ensure the necessary privileges can be applied.
* **High-level permissions** are enabled for system integration:
    * `host_pid: true`
    * `docker_api: true`
    * `host_network: true`
    * Other supervisor APIs (`hassio_api`, `auth_api`) are also enabled.
* The proxy exposes the filtered Docker socket on port `2375/tcp`.

## ⚙️ Filter Configuration (Environment Variables)

The core functionality of this proxy is managed by environment variables. A value of `"1"` enables the endpoint, and `"0"` disables it.

| Variable | Value | Description (Enabled: "1") |
| :--- | :--- | :--- |
| `CONTAINERS` | **"1"** | Allows access to container operations. |
| `IMAGES` | **"1"** | Allows access to image operations. |
| `INFO` | **"1"** | Allows access to Docker system information. |
| `NETWORKS` | **"1"** | Allows access to network operations. |
| `SERVICES` | **"1"** | Allows access to service operations (e.g., in Swarm). |
| `TASKS` | **"1"** | Allows access to task information. |
| `VOLUMES` | **"1"** | Allows access to volume operations. |
| `AUTH` | **"0"** | Disables authentication endpoints. |
| `BUILD` | **"0"** | Disables build operations. |
| `POST` | **"1"** | Allows POST requests (required for some operations). |
| `LOG_LEVEL` | `"info"` | Sets the proxy logging level. |

> **Warning:** You should **carefully review and customize** these variables to limit access only to the endpoints required by your external application.

## 🛠️ Installation and Setup

### 1. Installation

1.  Navigate to the **Add-on Store** in your Home Assistant installation.
2.  Add the URL of this repository to your repositories list: `https://github.com/Adribreezy/breeznas-addons-homeassistant`
3.  Find **Docker Proxy** in the Add-on Store and click **Install**.

### 2. Network Configuration

The add-on exposes the filtered Docker socket on port `2375`.

| Port | Protocol | Description |
| :--- | :------- | :---------- |
| **2375** | TCP | Proxy Expose Port (Unencrypted) |

**Security Note:** Port 2375 is typically unencrypted. Ensure you only expose this port securely or within a trusted network.

### 3. Start the Add-on

1.  Review and adjust the **Environment** variables to match your security requirements.
2.  Start the add-on.
3.  The service will run in the background, listening on the configured port.

***

## 💻 Technical Details

| Property | Value |
| :--- | :--- |
| **Slug** | `docker-proxy` |
| **Architecture** | `amd64` |
| **Startup** | `services` |
| **Panel Title** | `docker Proxy` |
| **Panel Icon** | `mdi:atom` |

***

## 🔗 Repository

For more information and source code, visit the repository:
[https://github.com/Adribreezy/breeznas-addons-homeassistant](https://github.com/Adribreezy/breeznas-addons-homeassistant)