# Notes for Frontend Masters - Developer Productivity

## 02. The Problem Statement

```
docker run --rm -it nvim-computer bash
```

## 04. Creating Ansible Tasks to install Zsh

```yaml
- hosts: localhost
  become: true
  tasks:
    - name: Install Zsh
      apt: name=zsh state=present
    - name: Change shell
      shell: chsh -s `which zsh` 
    - name: Install Oh My Zsh
      shell: sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
    - name: Install the zsh plugin autosuggestions
      ansible.builtin.git:
        repo: 'https://github.com/zsh-users/zsh-autosuggestions.git'
        dest: ~/.oh-my-zsh/plugins/zsh-autosuggestions
    - name: Update ur zshrc
      shell: sed -i 's/(git/(git zsh-autosuggestions' ~/.zshrc

```