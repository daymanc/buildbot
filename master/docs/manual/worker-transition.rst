Transition to "worker" terminology
==================================

.. todo::

    * ReStructured text formatting should be reviewed in scope of using
      Buildbot-specific directives.

    * This page may be splitted in parts or merged with other pages.

    * This page should be placed in a proper place in the TOC.

    * Links on this page should be added, e.g. from 0.9.0 changelog.

Since version 0.9.0 of Buildbot "slave"-based terminology is deprecated
in favor of "worker"-based terminology.

API change is done in backward compatible way, so old "slave"-containing
classes, functions and attributes are still available and can be used.
Complete removal of "slave"-containing terminology is planned in version
**TODO**.

Old names fallback settings
---------------------------

Use of obsolete names will raise Python warnings with category
:py:exc:`buildbot.worker_transition.DeprecatedWorkerNameError`.
By default these warnings are printed in the application log.
This behaviour can be changed by setting appropriate Python warnings settings
via Python's :py:mod:`warnings` module:

.. code-block:: python

    import warnings
    from buildbot.worker_transition import DeprecatedWorkerNameError
    # Treat old-name usage as errors:
    warnings.simplefilter("error", DeprecatedWorkerNameError)

See Python's :py:mod:`warnings` module documentation for complete list of
available actions, in particular warnings can be disabled using
``"ignore"`` action.

It's recommended to configure warnings inside :file:`buildbot.tac`, before
using any other Buildbot classes.

Changed API
-----------

In general "Slave" and "Buildslave" parts in identifiers was replaced with
"Worker".

Here is the complete list of changed API:

.. todo::

    This list will be updated along with actual changing of the API.

================================================================== =====
Old name                                                           New name
================================================================== =====
:py:class:`buildbot.interfaces.IBuildSlave`                        :py:class:`~buildbot.interfaces.IWorker`
------------------------------------------------------------------ -----
:py:attr:`buildbot.buildslave.base.AbstractBuildSlave.slavename`   :py:attr:`~buildbot.buildslave.base.AbstractBuildSlave.workername`
------------------------------------------------------------------ -----
:py:meth:`buildbot.buildslave.base.AbstractBuildSlave.updateSlave` :py:attr:`~buildbot.buildslave.base.AbstractBuildSlave.updateWorker`
------------------------------------------------------------------ -----
:py:attr:`buildbot.master.BuildMaster.buildslaves`                 :py:attr:`~buildbot.buildslave.base.AbstractBuildSlave.workers`
================================================================== =====