## Example

```
# ~/.ssh/authorized_keys
command="echo 'This account can only be used for forwarding'",no-agent-forwarding,no-X11-forwarding,permitopen="localhost:3306" ssh-rsa ...
```


```yaml
# docker-compose.yml
services:
    main:
        environment:
            MYSQL_DSN: mysql://user:pass@mysql_forward:3306/database
    # ...
    mysql_forward:
        image: mlebkowski/ssh-forward
        environment:
            ID_RSA_PATH: /root/id_rsa
            SSH_HOST: example.com
            PORT: 3306
            FORWARD_HOST: localhost
        volumes:
            - ./config/id_rsa:/root/id_rsa:ro
```
