# SJSU Ansible Web (Nginx on 8080)

This repository contains Ansible code for the SJSU assignment.  
It configures two VMs (VM1 and VM2) with Nginx web servers running on port **8080**.  
Each VM serves a simple web page that says:

- VM1 → **Hello World from SJSU-1**  
- VM2 → **Hello World from SJSU-2**

The playbook supports both **deploy** and **undeploy** operations.

---

## 📂 Project Structure

- **sjsu-ansible-web/**
  - **ansible.cfg** — Ansible configuration
  - **inventory.ini** — Inventory with VM IPs and variables
  - **site.yml** — Main playbook (deploy + undeploy)
  - **roles/**
    - **nginx_hello/**
      - **tasks/**
        - **main.yml** — Role tasks: install, configure, restart Nginx
      - **templates/**
        - **hello.conf.j2** — Nginx site config template (port 8080)
        - **index.html.j2** — Web page template (Hello World SJSU-X)



#Requirements

macOS / Linux host

Ansible installed

SSH access to VMs (Ubuntu 20.04+ / 22.04+ / 24.04+)

Security group or firewall rules allowing:

TCP 22 (SSH) from your host

TCP 8080 (HTTP) from your browser


## Usage
1) Edit `inventory.ini` with your VM IPs and SSH key path.
2) Test: `ansible all -m ping`
3) Deploy: `ansible-playbook site.yml --tags deploy`
4) Verify:
   - `curl http://<vm1-ip>:8080` → **Hello World from SJSU-1**
   - `curl http://<vm2-ip>:8080` → **Hello World from SJSU-2**
5) Un-deploy: `ansible-playbook site.yml --tags undeploy`

## 🛠 Requirements
- Ansible on macOS/Linux
- SSH access to the two VMs
- Firewall/Security Group: TCP 22 (SSH) and TCP 8080 (HTTP)
EOF

git add README.md
git commit -m "Add README with project details"
git push
