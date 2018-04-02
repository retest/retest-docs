{% extends "en_docs-content.tmpl" %}
{% block primary %}

Connection of retest to your application (SUT)
==============================================

For retest to be able to record and replay actions in your application, it first must connect to it.
That connection is always over network, even if everything happens on the same machine.
This is the reason, that the Windows Firewall can disallow that connection.

The first time you start a Java application that wants to connect to the network, there is a window asking for access.
In that case, please click on "allow access".

In case this has already happened some time in the past, you now need to allow access if you disallowed it then. 
Then you need to open your windows configuration (depending on your version of Windows) and allow access there.

{% endblock primary %}
