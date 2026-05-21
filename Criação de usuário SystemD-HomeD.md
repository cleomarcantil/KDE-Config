# Ativar SystemD-HomeD

## Fedora

```bash

sudo authselect enable-feature with-systemd-homed
sudo authselect apply-changes
systemctl enable --now systemd-homed.service

```

## Kubuntu

```bash

sudo apt update
sudo apt install systemd-homed
sudo systemctl enable --now systemd-homed

sudo pam-auth-update
# [*] Enable user management by systemd-homed

# verifique
systemctl status systemd-homed

# Se não estiver "active (running)", use:
sudo systemctl enable --now systemd-homed


```



## Criar usuário

### Fedora

```bash

sudo homectl create nome_do_usuario --storage=luks --luks-discard=on --luks-extra-mount-options=defcontext=system_u:object_r:user_home_dir_t:s0

```

### Kubuntu

```bash


sudo homectl create nome_do_usuario --storage=luks --luks-discard=on
# ou
sudo homectl create nome_do_usuario --storage=luks --luks-discard=on --member-of=sudo


# Usuários do systemd-homed no Kubuntu podem precisar ser adicionados manualmente a grupos como sudo ou video para funcionarem corretamente:
sudo homectl update nome_do_usuario --member-of=sudo,video,render,audio

```

## Alterar nome de exibição

```bash

homectl update nome_do_usuario --real-name="Nome Desejado"

# Verificar
homectl inspect nome-do-usuario

```