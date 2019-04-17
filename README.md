# ansible-greynoise

Ansible modules for the [GreyNoise](https://github.com/GreyNoise-Intelligence) API

A full example playbook can be found in `main.yml`.

`ansible-playbook main.yml -vvvv`

### Modules

* greynoise
  * list_tags
  * query_ip
  * query_tag

### Examples

```
- name: List all tags
  greynoise:
    action: list_tags
  register: results

- name: Query IP with GreyNoise
  greynoise:
    action: query_ip
    ip: "198.20.69.74"
    key: "{{ greynoise_api_key }}"
  register: results

- name: Query tag with GreyNoise
  greynoise:
    action: query_tag
    tag: "SHODAN"
    key: "{{ greynoise_api_key }}"
  register: results
```
