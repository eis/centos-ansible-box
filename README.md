Vagrantbox with Centos 7 and ansible.

Tested with Windows 7, Cygwin64 installed and in path

There seems to be an open [issue](https://github.com/mitchellh/vagrant/issues/4073)
with rsync in my setup, so had to do also this:

```
set VAGRANT_DETECTED_OS=cygwin
```

Before running vagrant up.

Once installed, go to your box with `vagrant ssh`.
