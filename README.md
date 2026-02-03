# Upgrade-PostgreSQL-16-to-17-on-Ubuntu
Upgrade PostgreSQL 16 to 17 on Ubuntu by installing version 17, stopping both services, and using pg_upgradecluster to migrate data. Key commands include sudo apt install postgresql-17, sudo pg_ctlcluster 16 main stop, sudo pg_upgradecluster 16 main -v 17, and optionally sudo pg_dropcluster 16 main
