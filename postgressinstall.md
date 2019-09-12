#### PostgreSql Install Manual Dengan Source Code

Step 1

Install package yang diperlukan

        $ apt install gcc zlib1g-dev libreadline6-dev

Step 2

Download Source PostgreSql dari sumbernya lalu ekstrak dan masuk ke directorinya

        $ wget https://ftp.postgresql.org/pub/source/v11.5/postgresql-11.5.tar.gz
        $ tar -xf postgresql-11.5.tar.gz
        $ cd postgresql-11.5

Step 3

Configure dengan prefix foldernya (agar PostgreSQL terinstall pada directory yang kita inginkan)

        $ ./configure --prefix=/tekkom/app/


Step 4

Compile dan Install

        $ make
        $ sudo make install

Step 5

Buat user dan password untuk owner PostgreSQL, buat folder untuk data, dan setting path

        $ useradd postgres
        $ passwd postgres
        $ mkdir -p /tekkom/data
        $ chown -R postgres. /tekkom/data
        $ echo 'export PATH=$PATH:/tekkom/app/bin' > /etc/profile.d/postgres.sh

Step 6

Masuk user postgres dan initdb

        $ su -l postgres
        $ initdb -D /tekkom/data

-D adalah dimana kita ingin menyimpan directory data database cluster.

Step 7

Nyalakan service PostgreSQL

      pg_ctl -D /tekkom/data/ -l start.log start


Step 8

Cek prosesnya

        $ ps -ef |grep -i postgres

Step 9

Buat script agar mudah untuk start/stop/reload service PostgreSQL

        $ vim postgres.sh
        pg_ctl -D /equnix/data -l start.log $1
        $ chmod +x postgres.sh
        $ ./postgres.sh start|stop|reload

Step 10

Masuk cli PostgreSql

        $ psql
        postgres=# create database test;
