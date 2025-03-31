# Ansible Web Server Provisioning on AWS

This project provisions 3 consistent web servers on AWS EC2 instances using Ansible automation. It configures Nginx, opens firewall ports, manages directories, templates configs, and ensures idempotency.

---

## 📦 Project Structure

```
aws-ansible/
├── Readme.md
├── ansible.cfg
├── group_vars
│   └── aws.yml
├── inventory.ini
├── nginx.conf.j2
├── playbook.yml
├── roles
│   └── webserver
│       ├── defaults
│       │   └── main.yml
│       ├── handlers
│       │   └── main.yml
│       ├── tasks
│       │   └── main.yml
│       └── templates
│           └── nginx.conf.j2
└── screenshots
    ├── instances
    │   ├── Screenshot 2025-03-31 124404.png
    │   ├── Screenshot 2025-03-31 124427.png
    │   ├── Screenshot 2025-03-31 125125.png
    │   └── Screenshot 2025-03-31 125155.png
    ├── playbook
    │   ├── Screenshot 2025-03-31 130215.png
    │   ├── Screenshot 2025-03-31 130449.png
    │   ├── Screenshot 2025-03-31 130513.png
    │   └── Screenshot 2025-03-31 130530.png
    └── verifications
        ├── Screenshot 2025-03-31 131222.png
        ├── Screenshot 2025-03-31 131400.png
        ├── Screenshot 2025-03-31 131441.png
        ├── Screenshot 2025-03-31 131502.png
        ├── Screenshot 2025-03-31 131613.png
        ├── Screenshot 2025-03-31 131621.png
        ├── Screenshot 2025-03-31 131627.png
        ├── Screenshot 2025-03-31 131730.png
        ├── Screenshot 2025-03-31 131735.png
        └── Screenshot 2025-03-31 131740.png

```

---

## 🧪 Validation Checklist

- ✅ `ansible -i inventory.ini aws -m ping` returns pong
- ✅ Nginx installed and running: `systemctl status nginx`
- ✅ Ports 80 & 443 open: `firewall-cmd --list-all`
- ✅ Directories exist with correct ownership/permissions
- ✅ `/etc/nginx/nginx.conf` correctly templated
- ✅ `curl http://<public-ip>` returns a response

---

## 📌 Run the Playbook

```bash
ansible-playbook -i inventory.ini site.yml
```

---

## ✅ Notes

- Ensure EC2 security group allows inbound traffic on ports 22, 80, 443.
- For Amazon Linux 2 on ansible master instance: 
install ansible via
```
sudo amazon-linux-extras enable ansible2
sudo yum install -y ansible
```
- For Amazon Linux 2 on webserver instances: 
enable Nginx via
```
sudo amazon-linux-extras enable nginx1
sudo yum clean metadata
sudo yum install -y nginx

```
