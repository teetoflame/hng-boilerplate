# Ansible Project for Server Configuration and Application Deployment

## Overview

This project uses Ansible to automate the configuration of servers and deployment of an application. The playbook provisions a PostgreSQL database, RabbitMQ messaging service, and an Express.js application, and sets up Nginx as a reverse proxy.

## Project Structure

ansible/
├── ansible.cfg
├── inventory.cfg
├── playbooks/
│   └── main.yaml


- **ansible.cfg**: Configuration file for Ansible.
- **inventory.cfg**: Inventory file specifying the hosts.
- **playbooks/main.yaml**: The main playbook that orchestrates the tasks.
- #roles/hng/tasks/main.yaml**: Role-specific tasks for the `hng` user.

## Prerequisites

- Ansible installed on your local machine.
- SSH access to the target servers.
- The SSH private key file (`~/.ssh/id_ed25519`) for accessing the servers.

## Setup

1. Clone the repository:
    ```bash
    git clone https://github.com/your-repo/ansible-project.git
    cd ansible-project
    ```

2. Ensure your `inventory.cfg` is correctly set up with your server details:
    ```ini
    [hng]
    ip-172-31-16-246 ansible_ssh_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_ed25519
    ```

3. Update the `ansible.cfg` file if necessary:
    ```ini
    [defaults]
    inventory = inventory.cfg
    remote_user = ubuntu
    private_key_file = ~/.ssh/id_ed25519
    host_key_checking = False
    retry_files_enabled = False
    ```

## Running the Playbook

To run the playbook and configure your servers, execute the following command:

```bash
ansible-playbook playbooks/main.yaml -b

## This command will perform the following tasks:

Create the hng user with sudo privileges.
Update the apt cache and install required packages.
Clone the specified Git repository.
Install and configure PostgreSQL.
Install and configure RabbitMQ.
Install application dependencies using Yarn.
Set up environment variables.
Start the application.
Install and configure Nginx to reverse proxy the application.

## Testing the Application
After running the playbook, you can test the application by accessing the server's public IP address in your browser. The application should be accessible via http://<server-public-ip>.

## Troubleshooting
Check the logs in /var/log/stage_5b/ for any errors related to the application.
Verify the status of the PostgreSQL, RabbitMQ, and Nginx services to ensure they are running correctly.
