Role Name
=========

Anisble role to install Miniconda3 + optional environments.

Requirements
------------

No special requirements above a working ansible setup.

Role Variables
--------------

  tags:
   - install  # download and install miniconda3
   - user     # symlink profile / bashrc for specified users
   - envs    # install environments from templated environment.yml files

### defaults/main.yml: 

```
  miniconda_download_dir       := location of miniconda3 download  
  miniconda_root_prefix        := location of install prefix (e.g., "/opt/miniconda") 

  miniconda_bin                := path to conda binary

  miniconda_base_url           := url to miniconda download area (e.g., "https://repo.anaconda.com/miniconda")
  miniconda_download_name      := the specific miniconda binary  (e.g., "Miniconda3-latest-Linux-x86_64.sh")
  miniconda_download_url       := full download url (base_url+download_name) 
  miniconda_download_name_full := full local download name (download_dir+download_name)

  miniconda_profile_shell      := path to bash shell profile 
  miniconda_envs_dir           := path to conda envs install folder
  miniconda_import_dir         := a place to put environment.yml files for import

  miniconda_templates_dir      := role templates 
  miniconda_templates_glob     := environment templates glob

  #miniconda.base_version      := TODO
  #miniconda.version           := TODO
```

Dependencies
------------

No external dependencies.

Example Playbook
----------------

conda-envs.yml:
=======
  ---
    - hosts: 
    - pipeline-servers 

  roles:
    - role: ansible-conda-role  
    vars:
      miniconda_root_prefix: /opt/miniconda3
      lusers: [alice,bob] 
Example Usage
-------------

  shell> ansible-playbook -i <hostsfile> conda-envs.yml

=======

Example Ansible Usage
---------------------

  To Install, setup user help files and create environments:
  |shell> ansible-playbook -i hosts conda-envs.yml.yml 

  To Intsall Only: 
  |shell> ansible-playbook -i hosts conda-envs.yml.yml --tags install

  To create environments only:
  |shell> ansible-playbook -i hosts conda-envs.yml.yml --tags envs 

License
-------

    GPLv2

Author Information
------------------

    Joe-OpenSrc
