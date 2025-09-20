ansible-role-docker
=========

Ansible-роль для установки Docker в Ubuntu

Role Variables
--------------

docker_conflict_packages - список пакетов, которые нужно удалить перед установкой Docker.

```yaml
docker_conflict_packages:
  - docker.io
  - docker-doc
  - docker-compose
  - docker-compose-v2
  - podman-docker
  - containerd
  - runc
```

docker_required_packages - список пакетов, которые нужно установить перед установкой Docker.

```yaml
docker_required_packages:
  - ca-certificates
  - curl
  - gnupg
```

docker_gpg_key_url - ссылка на gpg-ключ Docker.

```yaml
docker_gpg_key_url: "https://download.docker.com/linux/{{ ansible_distribution | lower }}/gpg"
```

docker_repo - ссылка на apt-репозиторий Docker.

```yaml
docker_repo: "deb [arch=amd64] https://download.docker.com/linux/{{ ansible_distribution | lower }} {{ ansible_distribution_release }} stable"
```

docker_packages - пакеты, которые нужно установить из репозитория Docker.

```yaml
docker_packages:
  - docker-ce
  - docker-ce-cli
  - containerd.io
  - docker-buildx-plugin
  - docker-compose-plugin
```

docker_services - сервисы, которые нужно запустить после установки Docker.

```yaml
docker_services:
  - containerd
  - docker
```


Example Playbook
----------------

```yaml
---
- hosts: servers
  become: true
  roles:
    - role: freshwave_kmv.docker_ubuntu
      docker_packages:
        - docker-ce
        - docker-ce-cli
        - containerd.io
```

License
-------

MIT

