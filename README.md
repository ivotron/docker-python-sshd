# python + sshd + docker

Image used to test ansible playbooks

Usage:

```bash
docker run --rm --name=node1 \
  -p 2221:22 \
  -e ADD_INSECURE_KEY=true \
  -v /var/run/docker.sock:/var/run/docker.sock \
  ivotron/python-sshd:debian-9
```

Launch more "nodes" by instantiating more containers using distinct 
ports, e.g. another `node2` container on port `2222`, `node3` on 
`2223`, and so on. Then, write a `hosts` file:

```
node1 ansible_host=localhost ansible_port=2221 ansible_user=root
node2 ansible_host=localhost ansible_port=2222 ansible_user=root
node3 ansible_host=localhost ansible_port=2223 ansible_user=root
```

And run a playbook.
