### Playbooks

    ansible-playbook <YAML>                   # Run on all hosts defined
    ansible-playbook <YAML> -f 10             # Run 10 hosts parallel
    ansible-playbook <YAML> --verbose         # Verbose on successful tasks
    ansible-playbook <YAML> -C                # Test run
    ansible-playbook <YAML> -C -D             # Dry run
    ansible-playbook <YAML> -l <host>         # Run on single host

Run Infos

    ansible-playbook <YAML> --list-hosts
    ansible-playbook <YAML> --list-tasks

Syntax Check

    ansible-playbook --syntax-check <YAML>

### Remote Execution

    ansible all -m ping

Execute arbitrary commands

    ansible <hostgroup> -a <command>
    ansible all -a "ifconfig -a"

### Debugging

List facts and state of a host

    ansible <host> -m setup                            # All facts for one host
    ansible <host> -m setup -a 'filter=ansible_eth*'   # Only ansible fact for one host
    ansible all -m setup -a 'filter=facter_*'          # Only facter facts but for all hosts

Save facts to per-host files in /tmp/facts

    ansible all -m setup --tree /tmp/facts

<?speakerdeck,dacfbe2fca344ffda3b93a5abcd155c7,Introduction to Ansible?>

### Ansible Module

Ansible modules are standalone scripts that can be used inside an Ansible playbook. You can use these modules to run whatever commands it needs to get its job done.

Ansible modules are categorized into various groups based on their functionality. There are hundreds of Ansible modules are available. You should read [Ansible Module](https://linuxbuz.com/linuxhowto/what-is-ansible-modules-and-how-to-use-it) for detail information of each module.
