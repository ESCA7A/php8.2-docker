- Configuration files:
- - .docker/infra/*
- Build dokcerfile:
- - bin/build
- Run project:
- - bin/start
Open <a href="http://localhost">my localhost domain</a>
- Show container logs:
- - bin/logs `container name`
- Tty terminal
- - bin/bash `container name`
For add new site set:
- /etc/hosts configuration
- nginx `server_name`, `root` directives like:
```apacheconf
    server_name localhost my_host;
    root /var/www/html/my_host/public; # for laravel
```
