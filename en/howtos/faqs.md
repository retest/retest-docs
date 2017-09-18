{% extends "en_docs-content.tmpl" %}
{% block primary %}

Frequently Asked Questions
==========================

### Java not recognized

I get the following error (under Windows):
`'java' is not recognized as an internal or external command, operable program or batch file.`

*Solution:* The error occurs because the java command (which is required by ReTest) is not within your path. 
Please make sure you have Java installed and the `JAVA_HOME` variable is set. 
You can have a look at [this tutorial](https://java.com/en/download/help/windows_manual_download.xml).

{% endblock primary %}