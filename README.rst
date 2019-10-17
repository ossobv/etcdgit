etcdgit :: Keep track of your etcd history using a Git repository
=================================================================

*This is largely untested. See also its DNS and mail counterparts*
`dnsgit`_ *and* `mailgit`_.

When you're using *Kubernetes* (k8s), you may want to know what changes
are done by k8s itself, and by the administrative users. *etcdgit* will
do a daily snapshot and commit it. This allows you to scan through the
changes and find causes.

**On a daily basis, etcdgit (re)creates a filesystem structure based on
the current etcd contents and commits that state to a local Git
repository.**

Any undo operation still has to be performed manually, but at least
you'll know what to undo.

*NOTE: We may want to add exclude rules. And we may want to add some
kind of auto-squash to keep the repository size down.*

.. _dnsgit: https://github.com/ossobv/dnsgit
.. _mailgit: https://github.com/ossobv/mailgit


Example setup
-------------

Optional configuration overrides go into ``/etc/default/etcdgit``. See
the top of ``etcdgit``.

.. code-block:: console

    # install -T -o755 etcdgit /usr/local/bin/etcdgit
    # mkdir /srv/etcdgit
    # cd /srv/etcdgit

    # git init; touch README.rst; git add README.rst; git commit -m Initial

    # etcdgit update-all

Run that last one -- ``etcdgit update-all`` -- from a daily cron job.

This will initialize and update the local repository and keep track of
changes.

For instance, a change may look like this:

    FIXME


License
-------

mailgit is free software: you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free
Software Foundation, either version 3 of the License, or (at your
option) any later version.
