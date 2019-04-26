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
    ip: "178.153.38.136"
    key: "{{ greynoise_api_key }}"
  register: results

- name: Show name and category with intention malicious from previous results
  debug:
    msg: "{{ item.name }} - {{ item.category }}"
  with_items:
    - "{{ results.json.records }}"
  when: item.intention == "malicious"

- name: Query tag with GreyNoise
  greynoise:
    action: query_tag
    tag: "PHP_WORM"
    key: "{{ greynoise_api_key }}"
  register: results

- name: Show IP and organization with intention malicious from previous results
  debug:
    msg: "{{ item.ip }} - {{ item.metadata.org }}"
  with_items:
    - "{{ results.json.records }}"
  when: item.intention == "malicious"
```
