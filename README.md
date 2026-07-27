# STARTcloud Generic Provisioner

[![STARTcloud Generic Provisioner logo](https://raw.githubusercontent.com/STARTcloud/startcloud_roles/refs/heads/main/roles/startcloud_theme/files/github-header.svg)](https://github.com/STARTcloud/startcloud_generic_provisioner/)

Documentation for STARTcloud Generic Provisioner

[**Explore the docs »**](https://github.com/STARTcloud/startcloud_generic_provisioner/)

[Report Bug](https://github.com/STARTcloud/startcloud_generic_provisioner/issues) ·
[Request Feature](https://github.com/STARTcloud/startcloud_generic_provisioner/issues)

## Table of Contents

* [About the Project](#about-the-project)
* [Key Features](#key-features)
* [Roadmap](#roadmap)
* [Provider Support](#provider-support)
* [Built With](#built-with)
* [Contributing](#contributing)
* [License](#license)
* [Contact](#authors)
* [Acknowledgements](#acknowledgments)

## About the Project

STARTcloud Generic Provisioner is a collection of Generic STARTcloud Roles.

## Key Features

* **Role Management**: Offers a comprehensive set of Ansible roles for various aspects of VM preparation and configuration.
* **Technology Installation**: Automates the installation of proprietary technologies like Verse, Domino, Traveler, and Nomad, simplifying the deployment process.
* **Service Configuration**: Simplifies the setup of necessary services on VMs, streamlining the deployment process.
* **Dependency Installation**: Handles the installation of required dependencies, reducing manual setup efforts.

### Interacting with `Hosts.yml` and `Hosts.rb`

To integrate STARTcloud Generic Provisioner with the Core Provisioner, specifically with the `Hosts.yml` and `Hosts.rb` files, follow these steps:

STARTcloud Generic Provisioner enhances the provisioning process by automating the configuration of VMs. To utilize these roles effectively, they need to be referenced within the `Hosts.yml` for the Core Provisioner `Hosts.rb`.

1. **Reference Roles in `Hosts.yml`**: Within the `Hosts.yml` file, you can specify which roles from STARTcloud Generic Provisioner should be applied to a particular host. This is done by including the role names under the `roles` key for each host configuration. For example:

   ```yaml
   hosts: all
   roles:
     - startcloud.startcloud_roles.ssl
     - startcloud.startcloud_roles.haproxy
   ```

   This configuration indicates that the `ssl` and `haproxy` roles from STARTcloud Generic Provisioner should be applied to all hosts via `all`.

1. **Execution in `Hosts.rb`**: The `Hosts.rb` script is responsible for interpreting the `Hosts.yml` file and generating the necessary Vagrant configurations. When the `Hosts.rb` script encounters a host configuration that includes roles, it automatically applies these roles during the provisioning process. There's no need for additional modifications in `Hosts.rb` for this purpose, as the script is designed to handle role application based on the `Hosts.yml` configurations.

By following these steps, you can seamlessly integrate STARTcloud Generic Provisioner with the Core Provisioner, leveraging the power of Ansible roles to automate the configuration and security of your VMs. This approach enhances the flexibility and extensibility of your provisioning process, allowing for a more declarative and manageable setup.

## Roadmap

See the [open issues](https://github.com/STARTcloud/startcloud_generic_provisioner/issues) for a list of proposed features (and known issues).

## Provider Support

| Provider      | Supported by STARTcloud Generic Provisioner |
| ------------- | ------------------------------------------- |
| VirtualBox    | Yes                                         |
| Bhyve/Zones   | Yes                                         |
| VMware Fusion | No                                          |
| KVM           | Yes                                         |
| QEMU          | Yes                                         |
| WSL2          | No                                          |

## Built With

* [Vagrant](https://www.vagrantup.com/) - Portable Development Environment Suite.
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads) - Hypervisor.
* [Ansible](https://www.ansible.com/) - Virtual Machine Automation Management.
* [Core Provisioner](https://github.com/STARTcloud/core_provisioner) - Core Provisioner.

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Authors

* **Joel Anderson** - *Initial work* - [JoelProminic](https://github.com/JoelProminic)
* **Justin Hill** - *Initial work* - [JustinProminic](https://github.com/JustinProminic)
* **Mark Gilbert** - *Refactor* - [MarkProminic](https://github.com/MarkProminic)

See also the list of [contributors](https://github.com/STARTcloud/startcloud_generic_provisioner/graphs/contributors) who participated in this project.

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
