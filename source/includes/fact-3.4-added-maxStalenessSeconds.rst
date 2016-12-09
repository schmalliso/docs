.. versionadded:: 3.4
   MongoDB 3.4 adds the ``maxStalenessSeconds`` read preference option,
   which lets you specify a maximum replication lag, or "staleness",
   for reads from :term:`secondaries <secondary>`. When a secondary's
   estimated staleness exceeds ``maxStalenessSeconds``, the client
   stops using it for read operations.
   
.. include:: /includes/fact-important-maxStalenessSeconds-intended-use.rst
