.. _whatsnew_upgrade41:

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Upgrading to Varnish 4.1 (unreleased)
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

Changes to VCL
==============

Not documented yet.

Version statement is kept
~~~~~~~~~~~~~~~~~~~~~~~~~

The VCL syntax has not chanced significantly, and as such the Varnish 4.0
version marker is kept for Varnish 4.1.

One of the initial lines in a Varnish 4.1 VCL should read::

    vcl 4.0;

Remote address accessors
~~~~~~~~~~~~~~~~~~~~~~~~

New in 4.1 is the `local.ip` and `remote.ip` representing the (local) TCP
connection endpoints.

With PROXY listeners the `server.ip` and `client.ip` are set from the PROXY
preamble. On normal HTTP listeners the behaviour is unchanged.


Management interface
====================

The management interface enabled with ``-M`` used to support the telnet
protocol.

Support for telnet control sequences have been retired. Replacements are netcat
or (preferred) ``varnishadm``.


Runtime users and groups
========================

With the new jail support, an additional runtime user (`vcache`) should be used
for the Varnish worker child process.

Additionally, the ``varnishlog``, ``varnishncsa`` and other Varnish shared log
utilities must now be run in a context with `varnish` group membership.


Protocol support
================

Support for HTTP/0.9 on the client side has been retired.


Changes to parameters
=====================

`vcl_cooldown` is new, and decides how long time a VCL is kept warm after being
replaced as the active VCL.

The following parameters have been retired:

* `group` (security rewamp)
* `group_cc` (security rewamp)
* `listen_address` (security rewamp)
* `pool_vbc`
* `timeout_req` - merged with `timeout_idle`.
* `user` (security rewamp)

Minor changes of default values on `workspace_session` and `vsl_mask`.

