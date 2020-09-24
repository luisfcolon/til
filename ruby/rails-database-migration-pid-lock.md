# Rails database migration Postgres locks

When a database migration runs, it sets a ppostgres lock. This prevents two sets of migrations from running against the database at the same time. If the database connection times out or is lost before the migration is complete:

* The lock is not removed
* Subsequent migrations will not execute until the lock is removed
* Rails server will not run due to pending migrations

To remove manually:

```sql
SELECT pid, locktype, mode FROM pg_locks WHERE locktype = 'advisory'
SELECT pg_terminate_backend(<PID>);.
```
