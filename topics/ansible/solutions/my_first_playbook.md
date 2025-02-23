# 📜 **Ansible Playbook: Install `zlib` and Create a File**  

```yaml
---
- name: Install zlib and Create a File
  hosts: all
  become: yes  # Run with sudo privileges
  tasks:
    - name: Install zlib package
      package:
        name: zlib1g
        state: present

    - name: Create /tmp/some_file
      file:
        path: /tmp/some_file
        state: touch
```

---

## 📌 How to Run the Playbook  

1️⃣ **Save the YAML file:**  
Create a new file named `my_first_playbook.yml` and copy the above code.  

2️⃣ **Run the playbook on a remote host:**  

```bash
ansible-playbook -i inventory.ini my_first_playbook.yml
```

(Replace `inventory.ini` with your actual inventory file.)  

3️⃣ **Verify the results on the remote host:**  

```bash
dpkg -l | grep zlib  # Check if zlib is installed
ls -l /tmp/some_file  # Check if the file is created
```
