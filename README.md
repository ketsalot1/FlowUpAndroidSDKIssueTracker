![FlowUp Logo][flowuplogo] FlowUp Android SDK Issue Tracker & Change Log
==============================

# Change Log

##0.2.6 (2016/12/15) Update Google Play Services dependency to 10.0.1, add background/foreground cross-metric data and minor fixes:

Bugfixes:

* Remove ``--printmapping out.map`` flag from the proguard configuration merged with users's proguard configuration.

Features:

* Update user agent header to contain information about the library configuration.
* Add a new header to the client indicating if the forceReport param is activated or not.
* Add cross-metric info to every report indicating if the report was collected in background or in foreground.
* Update Google Play Services transitive dependency to use the version ``10.0.1`` instead of the version ``9.6.1``.

##0.2.5 (2016/12/05) Fix SQLiteDatabaseLockedException:

Bugfixes:

* Fix the only crash we have found during the last releases where our database connection was throwing a [SQLiteDatabaseLockedException](https://developer.android.com/reference/android/database/sqlite/SQLiteDatabaseLockedException.html). Updating our ``SQLiteOpenHelper`` implementation to be a singleton we fixed this issue. **Now the SDK is crash free**.

##0.2.4 (2016/12/04)Fix config GCMTaskService:

Bugfixes:

* Change schedulers initialization related to the configuration implementation to be able to schedule the config task even if the client is disabled.

##0.2.3 (2016/11/30) Fix config GCMTaskService:

Bugfixes:

* Due to an error in a guard used in ``ConfigSyncService`` the config mechanism was not being updated when needed. This release fixes the issue. The config used by the library will be updated every hour.

##0.2.2 (2016/11/29) Synchronize reads and writes:

Bugfixes:

* Based on some documentation related to the [SQLite](https://developer.android.com/training/basics/data-storage/databases.html) implementation provided by the Android SDK we have updated the database access implementation to sync read and writes.

##0.2.1 (2016/11/28) Do not send empty reports:

Bugfixes:

* Due to a race condition some reports were being persisten and reported even if the report has no metrics associated. We have added a guard to fix this race condition.

##0.2.0 (2016/11/27) Change database access policy:

Bugfixes:

* Update how the different threads in the library access to the database. The static lock we were using has been replaced with a [ReentrantReadWriteLock](https://docs.oracle.com/javase/7/docs/api/java/util/concurrent/locks/ReentrantReadWriteLock.html).

##0.1.9 (2016/11/25) Remove AndroidManifest not needed attribute:

Bugfixes:

* Remove ``allowBackup`` attribute from the SDK AndroidManifest.

##0.1.8 (2016/11/23) Configure obfuscation as part of the artiact:

Bugfixes:

* In order to be able to easily distribute the library we have configured this artifact to merge the [proguard](https://www.guardsquare.com/en/proguard) configuration used with the current one configured in the project where the SDK is being installed. Based on this change we can remove all the information related to the proguard configuration from our documentation.

##0.1.7 (2016/11/23) Remove Realm dependency:

Bugfixes:

* Due to the problems found using [Realm](https://realm.io/) as a persistence mechansm we have replaced the usage of this library with [SQLDelight](https://github.com/square/sqldelight).

##0.1.6 (2016/11/17) Initial Release:

* First public release.


[flowuplogo]: ./art/FlowUpLogo.png
