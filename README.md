# ansible-memory-profiler

This Docker image was created to aid in memory profiling an Ansible playbook using
the `cgroup_memory_recap` callback plugin on a system without access to cgroups

## Building

```
docker build --no-cache -t ansible-memory-profiler .
```

## Using

```
docker run --rm -ti --privileged -v /path/to/playbook_dir:/playbook \
    -v /path/to/ansible/source:/ansible ansible-memory-profiler \
    ansible-playbook -v -i /playbook/hosts /playbook/playbook.yml
```
