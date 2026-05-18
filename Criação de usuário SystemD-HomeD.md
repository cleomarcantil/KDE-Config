# Ativar SystemD-HomeD

```bash

sudo authselect enable-feature with-systemd-homed
sudo authselect apply-changes
systemctl enable --now systemd-homed.service

```

## Criar usuário


```bash

sudo homectl create nome_do_usuario --storage=luks  --luks-extra-mount-options=defcontext=system_u:object_r:user_home_dir_t:s0

```


