{% extends "testprozess-content.tmpl" %}
{% block primary %}

Stable Test Environment
========================

An important point in relation to the test cases is their independence from each other. 
Independence means that if tests run in the order `A` `B` `C`, that test `B` has no dependencies 
to `A` and test `C` has no dependencies to `B` or `A`.

Such Dependencies often develop unconsciously, e.g. by working with data in test `B`, 
which are also processed in test `A` or even are first applied.

Dependencies between tests can have far-reaching negative consequences. 
Thus, tests can no longer be played independently of each other:

  
* If test `A` fails, test `B` and `C` fail automatically too, which means that no statement 
  can be made as to how far-reaching a problem actually is: Does the test fail because a problem affects all tests, 
  or only because of (unintended) dependencies?  
  
* The test order can‘ t be changed anymore. As a result, tests can no longer be randomly 
  provisioned and distributed or parallel executed.
  
* You can no longer play tests individually. If, e.g. only test `C` fails 
  but is dependent on `A` and `B`, this can lead to enormous time losses in the diagnosis and 
  resolution of the problem.


Similar to the programming itself, there is also a coupling which adversely affects 
the maintainability of the tests. Tests can therefore no longer be changed independently of each other: 
  
  
* If test `A` changes, test `B` and `C` must also be adjusted, 
  resulting in an increased maintenance effort and greater error probability.  
  
* Vice Versa, to adjust test `C`, it is also necessary to understand or know test `A` and `B` 
  in order to comprehend the origin of the data and / or the correctness of the test rules.  
  

These problems do not seem particularly "bad" at first sight. 
For a more complex software, however, hundreds of tests can become relatively fast thousand of tests. 
And then maintaining these can quickly devour the economic benefits of test automation. 
For this reason in more than one project the automatic tests were rejected completely, which means a huge economic loss.

 
Resetting Test environment
---------------------------

In order to counteract these problems effectively and not to allow these dependencies to arise (even unconsciously and unintentionally), it is advisable to set up the test environment in such a way that it can be quickly and easily "reset" to a defined original state. 
In the times of [virtualization](https://de.wikipedia.org/wiki/Virtualisierung_(Informatik)) with [VirtualBox](https://www.virtualbox.org), [VMware](http://www.vmware.com) and [Hyper-V](https://de.wikipedia.org/wiki/Hyper-V) and containerization with [Docker](https://www.docker.com), [Vagrant](https://www.vagrantup.com) and Co., this is no longer a problem. 
Furthermore, this does not usually represent a performance problem (depending on the scenario) because, in the worst case, a relatively simple distribution and parallelization in the cloud is possible with tools such as [Ansible](https://www.ansible.com), [Chef](https://www.chef.io/), [Saltstack](https://saltstack.com/) and [Puppet](https://puppet.com).

If you are looking for a solution, but you do not know how to implement it, [please contact us](https://retest.de/kontakt.html).

We recommend to reset the test environment as often as possible – preferably before recording or rather converting each individual suite. In order to automate the resetting of the SUT, we recommend so-called "[hooks](../konfiguration/konfigurationsdatei.md)".

{% endblock primary %}
