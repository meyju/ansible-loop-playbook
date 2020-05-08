# ansible-loop-playbook

Running `ansible-playbook` in loop for multiple inventorys. It is parsing the '-i|--inventory|--inventory-file' argument and looping over it. It works like the '-l' argument for specificing host limits, but it is translated to the inventory parameter.

After a run over multiple inventorys a total "PLAY RECAP" will be shown.

Tested on a Mac.

# Usage

- 'all' is a special inventory specification. It searches all inventory folders in your inventory-directory which have a 'hosts*.yml' file in it
- '!inventory_name' disables this inventory. Useful if you use 'all' and want to exclude some
- 'group1:group2' with ':' you can concatenate some inventorys

## inventory aliases

It is possible to use a aliases file to map some inventory names. By default this file is in the local direcotry and shuld be named `.ansible-loop.aliases`. The shema is `key value1 (value2)`. See [example ansible-loop.aliases](ansible-loop.aliases.example)

## example usage

Some example calls:

```
./ansible-loop-playbook -i 'all' playbook.yml -D -t task1
./ansible-loop-playbook -i 'all:!cai:!cas' playbook.yml -D -t task2 -l 'webservers'
./ansible-loop-playbook -i 'stage:prod' playbook.yml -D -t task3 -l 'webservers:applicationserver'
```

# Setup

Place `ansible-loop-playbook` in your ansible repostiroy and then run it from there.

```
wget https://raw.githubusercontent.com/meyju/ansible-loop-playbook/master/ansible-loop-playbook
chmod +x ./ansible-loop-playbook
```
