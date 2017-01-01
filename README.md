# Roboto
Configurable automation script executor

Name borrowed from the Mr. Roboto, this project aims at creating a environment to
create and execute automation scripts with ease.

Features in conceiving:
* YAML-based configuration
* Pluginable module system

## Blueprint

```yaml
- name: send server fee for clients from Example Company
  schedule: monthly(-1)
  tasks:
    - name: calculate server fee
      aws:
        user: example-company.com
        periods: this_month
      register: aws

    - name: send email
      email:
        sender: reporter@my-company.com
        receivers:
          client1: client1@example-company.com
          client2: client2@example-company.com
        template: |
          Dear {{this.receiver.name}},

          The fee for {{aws.period}} is {{aws.fee}}
```
