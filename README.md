# ansible-role-exabgp

###### Status: Unstable

Minimal setup for setting up static IPv4 BGP sessions with ExaBGP.

## Example

```yaml
- name: Ensure BGP sessions
  ansible.builtin.include_role: mangadex.exabgp
  vars:
    exabgp_sessions:
      - name: external
        router_id: "{{ public_ip }}"
        local_address: "{{ public_ip }}"
        local_as: 1234
        peer_as: 1235
        hold_time: 60
        announced_routes:
          - name: "IP1"
            announce: "1.2.3.4/32"
            med: 1
          - name: "IP2"
            announce: "1.2.3.5/32"
            med: 2
        peers:
          - 10.0.0.1
          - 10.0.0.2
```
