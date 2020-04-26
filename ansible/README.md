Instructions to build and run

```bash
docker build -t ansible .
```

```bash
docker run --rm \
    -it \
    -v ${PWD}/hosts:/etc/ansible/hosts \
    -v ${PWD}/ansible.cfg:/etc/ansible/ansible.cfg \
    -v ${HOME}/.ssh:/root/.ssh:ro \
    ansible all -m ping
```
