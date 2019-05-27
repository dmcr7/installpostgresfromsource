#### PostgreSql Install Manual Dengan Source Code

Step 1
Install package yang diperlukan

        $ apt install gcc zlib1g-dev libreadline6-dev

Step 2

Download Source PostgreSql dari sumbernya lalu ekstrak dan masuk ke directorinya

Step 3

Apabila ingin PostgreSql kita letakan pada suatu directori yang kita inginkan, maka buat dulu foldernya, kemudian configure dengan prefix foldernya

        mkdir /opt/PostgreSQL11/
        ./configure --prefix=/opt/PostgreSQL11

Step 4
Compile dan Install

        make
        make install


Step 5

      # useradd postgres
      # passwd postgres
      # mkdir -p /pgdatabase/data
      # chown -R postgres. /pgdatabase/data
      # echo 'export PATH=$PATH:/opt/PostgreSQL11/bin' > /etc/profile.d/postgres.sh


Step 6

    # su -l postgres
    $ initdb -D /pgdatabase/data/ -U postgres -W

-D adalah dimana kita ingin menyimpan directory data database cluster, -U untuk superuser name and -W untuk password db superuser.

Step 7

      pg_ctl -D /pgdatabase/data/ -l /pglog/db_logs/start.log start

sebelumnya buat dulu folder /pglog/db_logs untuk menyimpan log database. kemudian lakukan command diatas untuk memulai server postgres

Step 8

Cek prosesnya

        $ ps -ef |grep -i postgres

Step 9

Masuk cli PostgreSql

      psql
      postgres=# create database test;
      postgres=# \l to list all databases in cluster
      postgres=# \q to quit form postgres console
