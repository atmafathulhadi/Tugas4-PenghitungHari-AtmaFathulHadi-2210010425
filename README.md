
# Penghitung Hari

**Tugas Pemrograman GUI**  
Nama: Atma Fathul Hadi
NPM: 2210010425  

## 1. Deskripsi Program
Program ini adalah aplikasi GUI berbasis Java untuk menghitung jumlah hari dalam bulan tertentu pada tahun yang dipilih dan selisih hari antara tanggal pertama bulan dan tanggal yang dipilih menggunakan kalender. Program ini memungkinkan pengguna untuk memilih bulan dan tahun, serta memilih tanggal untuk perhitungan.

## 2. Komponen GUI
Aplikasi ini menggunakan komponen GUI berikut:

- **JFrame**: Sebagai jendela utama aplikasi
- **JPanel**: Wadah untuk komponen GUI lainnya
- **JComboBox**: Untuk memilih bulan (Januari hingga Desember)
- **JSpinner**: Untuk memilih tahun
- **JCalendar**: Untuk memilih tanggal
- **JLabel**: Menampilkan hasil perhitungan jumlah hari, hari pertama, hari terakhir, dan selisih hari
- **JButton**: Tombol untuk "HITUNG" dan "KELUAR"

## 3. Logika Program
Program ini menghitung jumlah hari dalam bulan yang dipilih, serta hari pertama dan hari terakhir bulan tersebut. Selain itu, program juga menghitung selisih hari antara tanggal pertama bulan dengan tanggal yang dipilih melalui **JCalendar**. Hasilnya akan ditampilkan pada **JLabel**.

### Kode Terkait:
```java
private void hitungJumlahHari() {
    int tahun = (Integer) jSpinner1.getValue();
    int bulan = jComboBox1.getSelectedIndex() + 1;

    LocalDate date = LocalDate.of(tahun, bulan, 1);
    int jumlahHari = date.lengthOfMonth();
    LocalDate hariPertama = date.withDayOfMonth(1);
    LocalDate hariTerakhir = date.withDayOfMonth(jumlahHari);

    LocalDate tanggalDipilih = jCalendar1.getDate().toInstant().atZone(ZoneId.systemDefault()).toLocalDate();

    long selisihHari = ChronoUnit.DAYS.between(hariPertama, tanggalDipilih);

    jLabel1.setText("<html>Jumlah Hari: " + jumlahHari + "<br>"
            + "Hari Pertama: " + translateDayOfWeek(hariPertama.getDayOfWeek().toString()) + "<br>"
            + "Hari Terakhir: " + translateDayOfWeek(hariTerakhir.getDayOfWeek().toString()) + "<br>"
            + "Selisih Hari: " + selisihHari + " hari</html>");
}
```

## 4. Events
- **ActionListener pada tombol Hitung**: Memanggil fungsi `hitungJumlahHari()` untuk menghitung dan menampilkan hasil saat tombol "HITUNG" ditekan.
   ```java
   hitung.addActionListener(new java.awt.event.ActionListener() {
       public void actionPerformed(java.awt.event.ActionEvent evt) {
           hitungJumlahHari();
       }
   });
   ```
- **ActionListener pada tombol Keluar**: Menutup aplikasi saat tombol "KELUAR" ditekan.
   ```java
   keluar.addActionListener(new ActionListener() {
       public void actionPerformed(ActionEvent e) {
           System.exit(0);
       }
   });
   ```

## 5. Variasi Program
- **Menampilkan Jumlah Hari dalam Bulan**: Program menampilkan jumlah hari dalam bulan yang dipilih berdasarkan tahun yang dipilih.
- **Menampilkan Hari Pertama dan Hari Terakhir**: Program juga menampilkan hari pertama dan hari terakhir dalam bulan yang dipilih.
- **Menghitung Selisih Hari**: Program menghitung selisih hari antara tanggal pertama bulan dan tanggal yang dipilih oleh pengguna.

## 6. Hasil Program
Aplikasi ini menampilkan jumlah hari dalam bulan yang dipilih, hari pertama dan hari terakhir bulan tersebut, serta selisih hari antara tanggal pertama bulan dan tanggal yang dipilih. Berikut adalah tampilan saat aplikasi dijalankan:

![Hasil Program](https://github.com/atmafathulhadi/Tugas4-PenghitungHari-AtmaFathulHadi-2210010425/blob/main/Screenshot%202024-11-10%20050416.png)

## 7. Indikator Penilaian

| No  | Komponen         |  Persentase  |
| :-: | ---------------- |   :-----:    |
|  1  | Komponen GUI     |    20%       |
|  2  | Logika Program   |    20%       |
|  3  | Kesesuaian UI    |    15%       |
|  4  | Constructor      |    15%       |
|  5  | Memenuhi Variasi |    30%       |
|     | **TOTAL**        | 100%         |

## 8. Cara Menjalankan Program
1. Buka program di IDE seperti NetBeans atau Eclipse.
2. Jalankan program, pilih bulan dan tahun pada combo box dan spinner.
3. Pilih tanggal menggunakan JCalendar.
4. Klik tombol "HITUNG" untuk melihat hasil jumlah hari, hari pertama, hari terakhir, dan selisih hari.
5. Klik tombol "KELUAR" untuk menutup aplikasi.
