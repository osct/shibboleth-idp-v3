shibboleth-idp-v3
=================

The role will install the Shibboleth Identity Provider v. 3 with tomcat8 into a debian based machine.
The integration is made with the packaged version of tomcat which has to be installed in the machine.


Requirements
------------

The user database is not installed by this role but it should be created in advance. Currently, only LDAP is supported by this role but MySqL could be integrated in the future. If none is available a role for LDAP is provided (look at the role named *ldap*).

The data time in the machine has to be correct so it would be good to syncronize with a time server using some pre-tasks or roles for the time.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.


``idp_attributes_scope``


``LDAP_server_certificate``

``idp_custom_templates_path``

``idp_custom_css_path``

``idp_custom_images_path``


Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

pexpect >= 3.3 (The version packaged with Debian jessy is too old and not working, it has to be installed with pip)

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: idp
      roles:
         - osct.shibboleth-idp-v3

License
-------

Apache v2.0

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
