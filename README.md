# Modul 10 - Advanced Programming

## Experiment 1.2: Understanding how it works

**Hasil Eksekusi:**
![alt text](image.png)

**Penjelasan:**
Mengapa tulisan `hey hey` muncul terlebih dahulu padahal ditulis setelah blok `spawner.spawn`? 

Hal ini terjadi karena fungsi `spawner.spawn` pada dasarnya hanya mengkonstruksi dan mengirimkan *future* (tugas) ke dalam antrean (channel) yang dimiliki oleh `executor`, tetapi **tidak langsung mengeksekusinya**. Eksekusi tugas asinkronus tersebut baru benar-benar berjalan ketika metode `executor.run()` dipanggil di akhir baris fungsi `main`.

Oleh karena itu, alur eksekusi *synchronous* pada *main thread* akan terus berjalan dan mengeksekusi `println!("Andi's Komputer: hey hey");` terlebih dahulu. Setelah itu, barulah `executor.run()` dipanggil, yang kemudian mengambil tugas dari antrean dan mulai mencetak `howdy!`, menunggu 2 detik, lalu mencetak `done!`.