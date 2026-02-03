# Upgrade-PostgreSQL-16-to-17-on-Ubuntu
Steps to Upgrade PostgreSQL 16 to 17 on Ubuntu.

1. **<u>Install PostgreSQL 17</u>** 
    > Ensure the PostgreSQL repository is added, then install the new version:
    ```
    sudo apt update
    sudo apt install postgresql-17
    ```
    _Note: A new, empty PostgreSQL 17 cluster (e.g., 17/main) will be created automatically._

2. **<u>Stop PostgreSQL Services</u>**
    > Stop both the old and new services to ensure data integrity during the upgrade:
    ```
    sudo pg_ctlcluster 16 main stop
    sudo pg_ctlcluster 17 main stop
    ```
3. **<u>Upgrade the Cluster</u>**
    > Use pg_upgradecluster to migrate the data from 16 to 17
    ```
    sudo pg_upgradecluster 16 main -v 17
    ```
4. **<u>Verify and Start</u>**
    > Check that the new cluster is running on port 5432 or 5433:
    ```
    pg_lsclusters
    sudo systemctl start postgresql
    ```
5. **<u>Stop PostgreSQL-16 Service</u>**
    > Stop the new service to ensure data integrity during the upgrade:
    ```
    sudo pg_ctlcluster 16 main stop
    ```
6. **<u>Remove Old Cluster</u>**
    > After verifying the data in version 17, remove the old 16 cluster:
    ```
    sudo pg_dropcluster 16 main
    ```
