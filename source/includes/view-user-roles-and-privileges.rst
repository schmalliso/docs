Use the :dbcommand:`usersInfo` command or :method:`db.getUser()`
method to display user information. The following procedure retrieves
user information for the ``reportsUser``. ``reportsUser`` was
created in the ``reporting`` database.

#. Switch to the user's authentication database:

   .. code-block:: sh
  
     use reporting
     
#. Use :method:`db.getUser()` to retrieve user information for the
   user with username ``reportsUser``.


   .. code-block:: sh
  
     db.getUser("reportsUser")


   In the returned document, the ``roles``
   field displays all roles for ``reportsUser``:
   
   .. code-block:: javascript
   
      ...
      "roles" : [
         { "role" : "readWrite", "db" : "accounts" },
         { "role" : "read", "db" : "reporting" },
         { "role" : "read", "db" : "products" },
         { "role" : "read", "db" : "sales" }
      ]

#. To retrieve a complete list of the user's :ref:`privileges`,
   include the optional ``showPrivileges`` argument when
   invoking :method:`db.getUser()`, as in the following:
   
   .. code-block:: sh
   
      db.getUser( "reportsUser", { showPrivileges : true } )
      
   The returned document includes an ``inheritedPrivileges`` field
   which shows the user’s full set of privileges, including
   expanded information for the inherited roles:
   
   .. code-block:: javascript
   
      {
               "resource" : {
                  "db" : "reporting",
                  "collection" : ""
               },
               "actions" : [
                  "bypassDocumentValidation",
                  "changeCustomData",
                  "changePassword",
                  "changeStream",
                  "collMod",
                  "collStats",
                  "compact",
                  "convertToCapped",
                  "createCollection",
                  "createIndex",
                  "createRole",
                  "createUser",
                  "dbHash",
                  "dbStats",
                  "dropCollection",
                  "dropDatabase",
                  "dropIndex",
                  "dropRole",
                  "dropUser",
                  "emptycapped",
                  "enableProfiler",
                  "enableSharding",
                  "find",
                  "getDatabaseVersion",
                  "getShardVersion",
                  "grantRole",
                  "indexStats",
                  "insert",
                  "killCursors",
                  "listCollections",
                  "listIndexes",
                  "moveChunk",
                  "planCacheIndexFilter",
                  "planCacheRead",
                  "planCacheWrite",
                  "reIndex",
                  "remove",
                  "renameCollectionSameDB",
                  "repairDatabase",
                  "revokeRole",
                  "setAuthenticationRestriction",
                  "splitChunk",
                  "splitVector",
                  "storageDetails",
                  "update",
                  "validate",
                  "viewRole",
                  "viewUser"
               ]
      }
      ...  
