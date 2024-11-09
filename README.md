# Aplikasi Penghitung Hari

**Tugas Pemrograman GUI**  
Nama: Atma Fathul Hadi  
NPM: 2210010425  

## 1. Deskripsi Program
Program ini adalah aplikasi GUI berbasis Java untuk menghitung jumlah hari dalam satu bulan tertentu dan menunjukkan beberapa informasi terkait, seperti hari pertama dan hari terakhir bulan tersebut serta selisih hari dengan tanggal yang dipilih dari kalender. Program ini dibuat menggunakan `JFrame` dan beberapa komponen lainnya.

## 2. Komponen GUI
Aplikasi ini dibuat menggunakan komponen GUI berikut:

- **JFrame**: Sebagai kerangka utama aplikasi
- **JPanel**: Wadah komponen GUI
- **JLabel**: Menampilkan teks untuk elemen seperti "Jumlah Hari" dan informasi lainnya
- **JComboBox**: Memilih bulan dalam setahun
- **JSpinner**: Memilih tahun
- **JCalendar**: Kalender untuk memilih tanggal tertentu
- **JButton**: Tombol untuk "Hitung" dan "Keluar"

## 3. Logika Program
Program ini menghitung jumlah hari dalam bulan yang dipilih dengan mengambil nilai dari `JComboBox` dan `JSpinner`, dan menggunakan API Java `LocalDate` untuk menentukan jumlah hari dan hari pertama dan terakhir bulan tersebut. Jika pengguna memilih tanggal di `JCalendar`, aplikasi akan menghitung selisih hari dari awal bulan hingga tanggal tersebut.

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
## 4. Events
ActionListener pada tombol Hitung: Memanggil fungsi hitungJumlahHari() untuk menghitung dan menampilkan hasil saat tombol "Hitung" ditekan.
java
Copy code
btnHitung.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        hitungJumlahHari();
    }
});
ActionListener pada tombol Keluar: Menutup aplikasi saat tombol "Keluar" ditekan.
java
Copy code
Exit.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        System.exit(0);
    }
});
## 5. Variasi Program
Program ini menampilkan informasi hari pertama dan terakhir pada bulan yang dipilih dalam bahasa Indonesia. Misalnya, jika hari pertama adalah "Senin", maka akan diterjemahkan ke bahasa Indonesia.

Kode Terkait Terjemahan Hari:
java
Copy code
private String translateDayOfWeek(String day) {
    switch (day) {
        case "MONDAY":
            return "Senin";
        case "TUESDAY":
            return "Selasa";
        case "WEDNESDAY":
            return "Rabu";
        case "THURSDAY":
            return "Kamis";
        case "FRIDAY":
            return "Jumat";
        case "SATURDAY":
            return "Sabtu";
        case "SUNDAY":
            return "Minggu";
        default:
            return day;
    }
}
## 6. Hasil Program
Aplikasi ini menampilkan jumlah hari dalam satu bulan, hari pertama, hari terakhir, serta selisih hari dengan tanggal yang dipilih. Contoh hasil ketika dijalankan:



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
Buka program di IDE seperti NetBeans atau Eclipse.
Jalankan program.
Pilih tahun menggunakan spinner dan bulan menggunakan combo box.
Pilih tanggal pada kalender.
Klik "Hitung" untuk melihat jumlah hari, hari pertama, hari terakhir, dan selisih hari.
Klik "Keluar" untuk menutup aplikasi.
