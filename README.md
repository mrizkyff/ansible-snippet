# Ansible Snippet

Struktur dasar Ansible untuk mengelola server remote. Repositori ini berisi playbook untuk melakukan update apt dan instalasi beberapa paket seperti htop, neofetch, dan Docker.

## Struktur Direktori

```
.
├── ansible.cfg           # Konfigurasi default Ansible
├── inventory.ini         # Daftar host yang akan dikelola
├── site.yml              # Playbook utama yang mengimpor semua playbook lainnya
└── playbooks/            # Direktori berisi playbook individual
    ├── apt_update.yml    # Playbook untuk update apt
    ├── install_htop.yml  # Playbook untuk instalasi htop
    ├── install_neofetch.yml # Playbook untuk instalasi neofetch
    └── install_docker.yml # Playbook untuk instalasi Docker
```

## Penggunaan

### Menjalankan Semua Playbook

```bash
ansible-playbook site.yml
```

### Menjalankan Playbook Tertentu

```bash
ansible-playbook playbooks/apt_update.yml
ansible-playbook playbooks/install_htop.yml
ansible-playbook playbooks/install_neofetch.yml
ansible-playbook playbooks/install_docker.yml
```

### Menjalankan Playbook dengan Tag

```bash
ansible-playbook playbooks/update_and_install.yml --tags update
ansible-playbook playbooks/update_and_install.yml --tags htop
ansible-playbook playbooks/update_and_install.yml --tags neofetch
ansible-playbook playbooks/update_and_install.yml --tags docker
```

## Konfigurasi Host

Edit file `inventory.ini` untuk menambahkan atau mengubah host yang akan dikelola. Contoh konfigurasi saat ini:

```ini
[webservers]
webserver1 ansible_host=192.168.1.101 ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa
webserver2 ansible_host=192.168.1.102 ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa

[dbservers]
dbserver1 ansible_host=192.168.1.103 ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa
```

## Catatan

- Pastikan SSH key sudah dikonfigurasi dengan benar untuk koneksi ke server remote
- Pastikan user yang digunakan memiliki hak sudo pada server remote