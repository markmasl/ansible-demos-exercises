andrewrothstein.flask
=====================
[![Build Status](https://travis-ci.org/andrewrothstein/ansible-flask.svg?branch=master)](https://travis-ci.org/andrewrothstein/ansible-flask)

Uses the system pip to install [Flask](https://www.pocoo.org/projects/flask/#flask).

Requirements
------------

See [meta/main.yml](meta/main.yml)

Role Variables
--------------

See [defaults/main.yml](defaults/main.yml)

Dependencies
------------

See [meta/main.yml](meta/main.yml)

Example Playbook
----------------
```yml
- hosts: servers
  roles:
    - andrewrothstein.flask
```

License
-------

MIT

Author Information
------------------

Andrew Rothstein <andrew.rothstein@gmail.com>
