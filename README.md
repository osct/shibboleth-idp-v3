Role Name
=========

The roles will install the Shibboleth Identity Provider v. 3 with tomcat8 into a debian based machine.
Tomcat has to be configured from the debian packages because it is

Requirements
------------

The user database is not installed by this role but it should be created in advance. Currently, OpenLDAP or MySql are supported by this role.
If none is available a role for LDAP is provided (look at the role named *ldap*)

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.


``idp_attributes_scope``


``LDAP.server.certificate``



Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

pexpect >= 3.3

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
