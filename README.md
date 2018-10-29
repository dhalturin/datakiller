Datakiller
========================
Destroy data on disks.

WARNING: Be careful. All data on all disks will be erased.

# Datakiller scheme:
![](playbooks/files/datakiller.png#center)

# Directory structure
```
root@datakiller01.example.com:~# tree /var/www/html/
/var/www/html/
├── datakiller
│   ├── latest.sh -> /var/www/html/datakiller/release-20180131150313.sh
│   ├── release-20180131143804.sh
│   ├── release-20180131144133.sh
│   ├── release-20180131144546.sh
│   ├── release-20180131145822.sh
│   └── release-20180131150313.sh
├── image
│   ├── latest.iso -> /var/www/html/image/release-20180131183819.iso
│   ├── release-20180131133711.iso
│   ├── release-20180131142358.iso
│   ├── release-20180131144735.iso
│   └── release-20180131183819.iso
└── squashfs
    ├── latest.squashfs -> /var/www/html/squashfs/release-20180131184039.squashfs
    ├── release-20180131133829.squashfs
    ├── release-20180131141949.squashfs
    ├── release-20180131144556.squashfs
    ├── release-20180131150321.squashfs
    └── release-20180131184039.squashfs
3 directories, 17 files
```

# Env in group vars
- delay - Delay for start erase disks
- sleep - Sleep for next check dd process
- work_dir - Build directory
- device - Devise pattern
- slack.to - chat or username
- slack.token - slack bot token

# Examples:
### Build image iso
```
ansible-playbook -i inventory -vv -D main.yml -t image
```

### Build image squashfs
```
ansible-playbook -i inventory -vv -D main.yml -t squashfs
```

### Generate datakiller
```
ansible-playbook -i inventory -vv -D main.yml -t datakiller
```
