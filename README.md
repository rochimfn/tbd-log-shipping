# RC Custom Log Shipping

## Deskripsi

Repositori ini berisi dokumentasi pemasangan aplikasi custom log shipping untuk SQL Server 2019 Express edition. Terdapat tiga komponen dari aplikasi ini.

### [tbd-backup-script](https://github.com/rochimfn/tbd-backup-script)

`tbd-backup-script` dipasang pada primary node. Program ini berisi script yang akan melakukan backup log dari database pada primary nodes. Program ini juga bertugas mengirimkan file log dan mengambil status restore dari log. Program ini mencatat konfigurasi dan aktivitas pada database mongodb.

### [tbd-server-webserver](https://github.com/rochimfn/tbd-server-webserver)

`tbd-server-webserver` dapat dipasang dimana saja asalkan dapat mengakses server mongodb yang mencatat konfigurasi dan aktivitas dari `tbd-backup-script`. Aplikasi web ini dapat digunakan untuk konfigurasi dan monitoring jalannya log shipping.

### [tbd-client-webserver](https://github.com/rochimfn/tbd-client-webserver)

`tbd-client-webserver` dipasang pada secondary node. Program ini berisi dua aplikasi yaitu web api yang berperan menerima kiriman log dari `tbd-backup-script` dan script restore yang berperan me-restore log yang telah dikirim. 

## Arsitektur

![.github/arsitektur.png](.github/arsitektur.png)

* Primary node hanya boleh ada satu.
* Secondary node boleh lebih dari satu node.