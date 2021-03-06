# prometheus-builder
Ansible scripts to build prometheus RPMs in a clean virtualbox environment. Built RPMs are uploaded into bintray public repository.

## Usage
Bintray manuals with screenshots if needed: - go to https://bintray.com/docs/usermanual/

1) Create repository, for example, "prometheus" via web interface at your organization:

2) Create packages via web interface (if not yet) with names:
 - prometheus
 - alertmanager
 - node-exporter
 - jmx-exporter

3) Add new versions, trackers, avatars via web interface, example:
 - 0.20 (for prometheus) 
 - 0.1.1 (for alertmanager)
 - 0.12.0 (for node-exporter)
 - 0.6 (for jmx-exporter)

4) Accordingly to https://github.com/UnitedTraders/prometheus-builder repo look here:
~~~
deploy-bintray: rpm
        curl -T $(RPM_FILE) -u$(CREDENTIALS) \
        https://api.bintray.com/content/$(REPOSITORY)/prometheus/$(VERSION)/$(RPM_NAME)
~~~

5) Insert your data, get API KEY at your account settings before:

~~~
$ vi group_vars/all.yml
repository_path: "organization/repository"    
bintray_credentials: "username:0123456789abcdefghijklmnopqrstuv"
~~~

6) Check if needed, do as you code: 
~~~
$ vi Vagrantfile
$ vi ansible.cfg
~~~
7) Run: 
~~~
vagrant up
~~~

8) Check uploaded packets at http://bintray.com/ and add them additional info (descripting, avatar)

9) Find in packets at http://bintray.com/ "Notice: You have 4 unpublished item(s) for this version"

10) Click "Publish" button to make packet availablie and wait 5min...6h before it will be available

11) See notice "4 new files will be publicly available shortly"

12) Save our planet :deciduous_tree: :
~~~
vagrant destroy
~~~

13) Optionally: GPG sign your packets :closed_lock_with_key: via bintray web interface

14) Optionally: do new pull-request :octocat:
