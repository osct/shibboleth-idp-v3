shibboleth-idp-v3
=================

The role will install the Shibboleth Identity Provider v. 3 with tomcat8 into a debian based machine.
The integration is made with the packaged version of tomcat which has to be installed in the machine.


Requirements
------------

The user database is not installed by this role but it should be created in advance. Currently, only LDAP is supported by this role but MySqL could be integrated in the future.

The data time in the machine has to be correct so it would be good to syncronize with a time server using some pre-tasks or roles for the time.

The role requires root privileges so the become parameters must be provided.

Role Variables
--------------

The  variables should be configured by the user (default values provided) :

* ``idp_attribute_database``: Attribute database type (string, mandatory, possible values *ldap* and *mysql*, default: *ldap*)
* ``idp_authn_LDAP_attribute_resolver``: Path to the default attribute resolver to use for an LDAP based IdP (string, optional, default: *shibboleth-idp/conf/attribute-resolver-ldap-nossl.xml*)
* ``idp_authn_LDAP_ldapURL``: LDAP URL (string, optional: *ldap://localhost:389*)
* ``idp_authn_LDAP_useStartTLS``: LDAP uses StartTLS (boolean, optional, default: *False*)
* ``idp_authn_LDAP_baseDN``: LDAP base DN (string, optional default: *ou=people,dc=example,dc=org*)
* ``idp_authn_LDAP_userFilter``: LDAP user filter (string, optional, default: *(uid={user})*)
* ``idp_authn_LDAP_bindDN``: LDAP bind DN (string, optional, default: *uid=myservice,ou=system*)
* ``idp_authn_LDAP_bindDNCredential``: LDAP bind DN credentials (string, optional, default: *myServicePassword*)
* ``idp_authn_LDAP_dnFormat``: LDAP DN format (string, optional, default: *uid=%s,ou=people,dc=example,dc=org*)
* ``idp_attribute_resolver_LDAP_searchFilter``: LDAP resolver search filter (sting, optional, default: *(uid=$resolutionContext.principal)*)
* ``idp_attribute_resolver_LDAP_returnAttributes``: LDAP resolver attribute list (string, optional, default: *cn,homephone,mail*)
* ``idp_attribute_filter``: Path to the default attribute filer releasing eppn, mail, surname, givenname and displayname to services requiring them (string, optional, default: *shibboleth-idp/conf/attribute-filter.xml*)
* ``idp_attribute_persistent_id``: Enable the release of a persistent identifier (boolean, optional, default: *False*)
* ``idp_attributes_scope`: Scope for IdP metadata and scoped attributes (string, mandatory, default: *N/A*)
* ``idp_persistentId_salt``: Salt for the persistent Id (string, optional, default: *provideasecuresaltpassphraseforthepersistentid*)
* ``idp_session_trackSPSessions``: Enable Single LogOut (SLO) (boolean, optional, default: *False*)
* ``idp_session_secondaryIndex``: Enable secondary index for SLO (boolean, optional, default: *N/A*)
* ``idp_storage_html_local``: Enable html based session storage (boolean, optional, default: *N/A*)
* ``idp_logout_elaboration``: Enable logout user request (boolean, optional, default: *N/A*)
* ``idp_ui_fallbackLanguages``: Browser language support (string, optional, default: *en*)
* ``idp_nameid_format``: Format to use for the subject name identifier (string, optional, default: *urn:oasis:names:tc:SAML:2.0:nameid-format:persistent*)
* ``idp_backchannel_PKCS12_password``: Password for the backend channel certificate/key (string, optional, default: *changeit*)
* ``idp_cookie_encryption_key_password``: Password for cookie encryption certificate/key (string, optional, default: *changeit2*)
* ``idp_custom_images_path``: Path to a folder with custom images to add to the IdP (string, optional, default: *N/A*)
* ``idp_custom_css_path``: Path to a folder with custom style sheets to add to the IdP (string, optional, default: *N/A*)
* ``idp_custom_templates_path``: Path to a folder with custom templates to add to the IdP (string, optional, default: *N/A*)
* ``idp_custom_messages_path``: Path to a property file with custom messages to add to the IdP (string, optional, default: *N/A*)
* ``metadataproviders``: List of metadata provider to include (array of objects, mandatory, default: *N/A*)

The *metadataproviders* should have a format like the following:

    metadataproviders:
    - name: 'federation1'
      url: 'url to federation metadata file'
    - name: 'federation2'
      url: 'url to federation metadata file'
      certificate:
        url: 'url providing the metadata signing certificate'
    - name: 'federation3'
      url: 'url to federation metadata file'
      certificate:
        path: 'local path to metadata signing certificate'


Dependencies
------------

Packages:

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
