# 📜 **Ansible Playbook: Create a Directory**  

```yaml
---
- name: Create a Directory in /tmp
  hosts: all
  become: yes  # Run with sudo privileges (if required)
  tasks:
    - name: Create /tmp/new_directory
      file:
        path: /tmp/new_directory
        state: directory
        mode: '0755'  # Sets directory permissions
```

---

## 📌 How to Run the Playbook  

1️⃣ **Save the YAML file:**  
Create a new file named `create_directory.yml` and copy the above code.  

2️⃣ **Run the playbook:**  

```bash
ansible-playbook -i inventory.ini create_directory.yml
```

(Replace `inventory.ini` with your actual Ansible inventory file.)  

3️⃣ **Verify the directory on the target machine:**  

```bash
ls -ld /tmp/new_directory
```

---

## 🔧 Additional Enhancements  

📌 **Ensure Directory Exists Before Creating**  

```yaml
    - name: Create Directory If Not Exists
      file:
        path: /tmp/new_directory
        state: directory
        mode: '0755'
        owner: ubuntu
        group: ubuntu
```

📌 **Create Multiple Directories**  

```yaml
    - name: Create Multiple Directories
      file:
        path: "{{ item }}"
        state: directory
        mode: '0755'
      loop:
        - /tmp/dir1
        - /tmp/dir2
        - /tmp/dir3
```

📌 **Remove the Directory (Optional)**  

```yaml
    - name: Remove the Directory
      file:
        path: /tmp/new_directory
        state: absent
```
