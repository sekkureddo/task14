Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Path Flow (цепочка путей)
-------------------------

```
Control node (Ansible)          Managed node (slave)           Container (nginx)
────────────────────────       ─────────────────────           ─────────────────
roles/install_nginx/files/
├── cpu-info.html               /opt/nginx/html/               /var/www/html/
├── firstpage.html     copy     ├── cpu-info.html    volume    ├── cpu-info.html
├── secondpage.html    ──────>  ├── firstpage.html   ──────>   ├── firstpage.html
├── images/                     ├── secondpage.html            ├── secondpage.html
│   ├── firstmeme.jpg           ├── images/                    ├── images/
│   └── secondmeme.png          │   ├── firstmeme.jpg         │   ├── firstmeme.jpg
└── music/                      │   └── secondmeme.png        │   └── secondmeme.png
    └── *.mp3                   └── music/                     └── music/
                                    └── *.mp3                      └── *.mp3
```

Переменные: `nginx_host_html` (хост) → volume → `nginx_root` (контейнер)

Role Variables
--------------

- `nginx_root` — путь внутри контейнера (default: /var/www/html)
- `nginx_host_base` — базовая директория на хосте (default: /opt/nginx)
- `nginx_host_html` — директория с файлами на хосте (default: /opt/nginx/html)

Остальные переменные — см. defaults/main.yml

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
