# Ansible Role: macos-docker-app

An Ansible role that installs the Docker application on macOS.

# Requirements

The `macos_docker_app_sudo_pass` must be available to this playbook. This can be provided via the command line with `-e @extravars.json` or with a prompt from within the playbook itself (see the example below).

See the `role-extravars.json` file in the `tests` directory for an example of how to format the `extravars.json` file in order to pass the `macos_docker_app_sudo_pass` variable to the `ansible-role-macos-docker-app` role.

# Role Variables

Available variables are listed below, along with default values in minutes:

  docker_prefs: { 'memoryMiB' : 6144, 'cpus' : 2, 'useCredentialHelper' : false  }

# Example Playbook

```yml
    - hosts: ci_macs
      vars_prompt:
      - name: "macos_docker_app_sudo_pass"
        prompt: "SUDO password"
        private: yes
      roles:
        - { role: macos-docker-app, 
            docker_prefs: {
              'memoryMiB' : 8192,
              'cpus' : 2,
              'useCredentialHelper' : false
            }
          }
```
## License

Apache 2.0
