# Dozzle Agent for Home Assistant

**Dozzle Agent** is a Home Assistant Add-on providing a real-time log viewer for your containers, supporting Docker, Swarm, and K8s. This add-on runs the **Dozzle Agent** command to facilitate log viewing.

* **Version:** v8.14.5
* **Source:** [https://github.com/Adribreezy/breeznas-addons-homeassistant](https://github.com/Adribreezy/breeznas-addons-homeassistant)
* **Image:** `theadribreezy/dozzle-agent`

## 🚀 Features

* **Real-time log viewing** for your Home Assistant containers.
* Utilizes the lightweight and powerful **Dozzle** tool.
* Provides **low-level host access** to gather logs effectively.

## ⚠️ Important Configuration Notes

This add-on is configured to operate with extensive privileges to access Docker logs across the host.

* `init: false` is set to allow the use of the specific `cmd` and the necessary permissions.
* **`cmd: agent`**: Starts the Dozzle in agent mode.
* **High-level permissions** are enabled to ensure full access to the Docker environment:
    * `host_pid: true`
    * `docker_api: true`
    * `host_network: true`
    * The Docker socket is mounted: `/run/docker.sock:/var/run/docker.sock:ro`
    
    > **Note:** These permissions are required for the agent to access and stream logs from other containers on the host system.

## ⚙️ Installation and Configuration

### 1. Installation

1.  Navigate to the **Add-on Store** in your Home Assistant installation.
2.  Add the URL of this repository to your repositories list: `https://github.com/Adribreezy/breeznas-addons-homeassistant`
3.  Find **Dozzle Agent** in the Add-on Store and click **Install**.

### 2. Network Configuration

The add-on exposes the agent on port `7007`.

| Port | Protocol | Description |
| :--- | :------- | :---------- |
| **7007** | TCP | Agent Port |

You can configure the host port mapping for `7007/tcp` in the add-on configuration tab.

### 3. Start the Add-on

1.  Review the configuration (optional).
2.  Start the add-on.
3.  The add-on will be accessible via the **Dozzle-Agent** panel icon (`mdi:atom`) in the Home Assistant sidebar.

***

## 💻 Technical Details

| Property | Value |
| :--- | :--- |
| **Slug** | `dozzle` |
| **Startup** | `services` |
| **Panel Title** | `Dozzle-Agent` |
| **Panel Icon** | `mdi:atom` |

***

## 🔗 Repository

For more information and source code, visit the repository:
[https://github.com/Adribreezy/breeznas-addons-homeassistant](https://github.com/Adribreezy/breeznas-addons-homeassistant)