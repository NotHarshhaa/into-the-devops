# 📜 **Ansible Playbook: Update & Upgrade APT Packages**  

```yaml
---
- name: Update and Upgrade APT Packages
  hosts: all
  become: yes  # Run as sudo
  tasks:
    - name: Update APT Package List
      apt:
        update_cache: yes

    - name: Upgrade All Packages
      apt:
        upgrade: yes
```

---

## 📌 How to Run the Playbook  

1️⃣ **Create a playbook file:**  
Save the above YAML code as `update_upgrade.yml`.  

2️⃣ **Run the playbook:**  
Use the following command:  

```bash
ansible-playbook -i inventory.ini update_upgrade.yml
```

(Replace `inventory.ini` with your actual Ansible inventory file.)  

3️⃣ **Verify updates:**  
Check installed package versions using:  

```bash
apt list --upgradable
```

---

## 🔧 Additional Enhancements  

📌 **Add Auto Cleanup** (Remove unnecessary packages & dependencies)  

```yaml
    - name: Remove Unused Packages
      apt:
        autoremove: yes
```

📌 **Enable Unattended Upgrades** (Automate future updates)  

```yaml
    - name: Enable Unattended Upgrades
      apt:
        name: unattended-upgrades
        state: present
```
