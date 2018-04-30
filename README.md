# ansible-memory-profiler

This Docker image was created to aid in memory profiling an Ansible playbook using
the `cgroup_memory_recap` callback plugin on a system without access to cgroups

## Using

```
docker run --rm -ti --privileged \
    -v /path/to/playbook_dir:/playbook \
    -v /path/to/ansible/source:/ansible \
    sivel/ansible-memory-profiler \
    ansible-playbook -v -i /playbook/hosts /playbook/playbook.yml
```

## Notes

### ansible directory

This image assumes that `/ansible` will be mounted, and should be the path to the Ansible source. It will be used following the [Running from Source](http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#running-from-source) instructions. If `/ansible` is not mounted, you will presented with an error.

### playbook directory

The `/playbook` directory can be whatever you want, I've just used it as an easy to follow convention.

### cgroup_memory_recap callback plugin

This is the same callback plugin that will be included in Ansible 2.6.0, but bundled here for use in earlier Ansible versions.

## Why?

I develop on a Mac, and as such I don't have direct access to cgroups, but I do have access to Docker. This image gives easy access to use cgroup based memory profiling locally, with little hoops to jump through.
