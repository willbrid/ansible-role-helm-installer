# Ansible-role-helm-installer

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/willbrid/ansible-role-helm-installer/blob/main/LICENSE)

Le rôle **ansible-role-helm-installer** permet d’installer l’outil **Helm** sur des systèmes Linux via son archive officielle. Il prend en charge différentes architectures (comme amd64, arm64, etc.) et versions spécifiques d’**Helm**. Ce rôle peut également vérifier l’intégrité de l’archive téléchargée en validant automatiquement son checksum (SHA256), si fourni.

## Exigences

- **Systèmes Linux** : distributions RedHat et Debian

## Description des Variables

|Nom|Type|Description|Obligatoire|Valeur par défaut|
|---|----|-----------|-----------|-----------------|
`helm_version`|str|numéro de version de helm. Format : vx.y.z|non|`"v3.17.3"`
`helm_bin_dir`|str|répertoire d'installation du binaire de helm|non|`"/usr/local/bin`
`should_verify_helm_checksum`|bool|dire s'il faut vérifier l'intégrité du fichier archive de helm après téléchargement|non|`true`

## Dépendances

Aucune.

## Exemple Playbook

- Installation du rôle

```bash
mkdir -p $HOME/install-helm/roles
```

```bash
vim $HOME/install-helm/requirements.yml
```

```yaml
- name: ansible-role-helm-installer
  src: git+https://github.com/willbrid/ansible-role-helm-installer.git
  version: v0.0.1
```

```bash
cd $HOME/install-helm && ansible-galaxy install -r requirements.yml --roles-path roles
```

- Utilisation du rôle dans un playbook

```bash
vim $HOME/install-helm/playbook.yml
```

```yaml
---
- hosts: localhost
  vars:
    helm_version: "v3.17.3"
    should_verify_helm_checksum: true

  roles:
    - ansible-role-helm-installer
```

```bash
cd $HOME/install-helm && ansible-playbook playbook.yml
```

## Licence

MIT

## Informations sur l'auteur

William Bridge NGASSAM
