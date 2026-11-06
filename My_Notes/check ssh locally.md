# check ssh locally

```bash
sudo ss -tlnp | grep :22

sudo systemctl status ssh
```

timeout 2 bash -c 'cat < /dev/tcp/127.0.0.1/22'
