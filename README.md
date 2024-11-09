# Perhitungan Diskon

**Tugas Pemrograman GUI**  
Nama: Atma Fathul Hadi  
NPM: 2210010425  

## 1. Deskripsi Program
Program ini adalah aplikasi GUI berbasis Java untuk menghitung diskon harga barang. Pengguna memasukkan harga asli, memilih persentase diskon melalui slider atau combo box, dan dapat memasukkan kode kupon untuk tambahan diskon. Program ini akan menampilkan harga akhir setelah diskon serta penghematan yang diperoleh.

## 2. Komponen GUI
Aplikasi ini dibuat menggunakan komponen GUI berikut:

- **JFrame**: Sebagai kerangka utama aplikasi
- **JPanel**: Wadah komponen GUI
- **JLabel**: Label teks untuk elemen seperti "Harga" dan "Kode Diskon"
- **JTextField**: Input untuk harga asli dan kode diskon
- **JComboBox**: Memilih persentase diskon (10%, 30%, 50%, dll.)
- **JSlider**: Alternatif untuk memilih persentase diskon
- **JButton**: Tombol untuk "Hitung" dan "Keluar"
- **JTextArea**: Menampilkan riwayat perhitungan diskon

## 3. Logika Program
Program melakukan perhitungan diskon sederhana menggunakan rumus aritmatika. Setelah pengguna memasukkan harga asli dan memilih diskon, aplikasi menghitung harga akhir dan penghematan, serta menampilkan hasilnya. Jika pengguna memasukkan kode kupon yang valid ("DISKON10"), diskon tambahan 10% akan diterapkan.

### Kode Terkait:
```java
private void hitungDiskon() {
    try {
        double harga = Double.parseDouble(inputharga.getText());
        int diskon = jSliderValue.getValue();
        double penghematan = harga * diskon / 100;
        double hargaSetelahDiskon = harga - penghematan;

        hasil.setText("Harga Akhir: Rp " + hargaSetelahDiskon + ", Penghematan: Rp " + penghematan);

        // Simpan riwayat perhitungan
        String riwayatEntry = "Harga: Rp " + harga + ", Diskon: " + diskon;
        riwayatList.add(riwayatEntry);

        StringBuilder sb = new StringBuilder();
        for (String entry : riwayatList) {
            sb.append(entry).append("\n");
        }
        jTextArea1.setText(sb.toString());
    } catch (NumberFormatException e) {
        JOptionPane.showMessageDialog(this, "Masukkan harga yang valid!", "Error", JOptionPane.ERROR_MESSAGE);
    }
}
```
4. Events
ActionListener pada tombol Hitung: Memanggil fungsi hitungDiskon() untuk menghitung dan menampilkan hasil saat tombol "Hitung" ditekan.
```java
hitung.addActionListener(new java.awt.event.ActionListener() {
    public void actionPerformed(java.awt.event.ActionEvent evt) {
        hitungDiskon();
    }
});
```
ActionListener pada tombol Keluar: Menutup aplikasi saat tombol "Keluar" ditekan.
```java
keluar.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        System.exit(0);
    }
});
```
ChangeListener pada JSlider: Memperbarui nilai persentase diskon pada combo box dan tooltip saat slider digeser.
```java
jSliderValue.addChangeListener(new ChangeListener() {
    public void stateChanged(ChangeEvent evt) {
        int diskon = jSliderValue.getValue();
        jComboBox1.setSelectedItem(diskon + "%");
        jSliderValue.setToolTipText(diskon + "%");
    }
});
```
### 5. Variasi Program
Kode Kupon: Pengguna dapat memasukkan kode kupon "DISKON10" untuk diskon tambahan 10%.
Slider untuk Persentase Diskon: Alternatif pilihan diskon melalui slider.
Riwayat Perhitungan: Riwayat perhitungan ditampilkan di JTextArea.
Kode Terkait Riwayat Perhitungan:
```java
String riwayatEntry = "Harga: Rp " + harga + ", Diskon: " + diskon;
riwayatList.add(riwayatEntry);

StringBuilder sb = new StringBuilder();
for (String entry : riwayatList) {
    sb.append(entry).append("\n");
}
jTextArea1.setText(sb.toString());
```
### 6. Hasil Program
Aplikasi menampilkan harga akhir, penghematan yang diperoleh, serta menyimpan dan menampilkan riwayat perhitungan diskon pada JTextArea. hasil ketika dijalankan ![Screenshot 2024-11-10 050416](https://github.com/atmafathulhadi/Tugas4-PenghitungHari-AtmaFathulHadi-2210010425/blob/main/Screenshot%202024-11-10%20050416.png)

### 7. Indikator Penilaian
| No  | Komponen         |  Persentase  |
| :-: | ---------------- |   :-----:    |
|  1  | Komponen GUI     |    20%       |
|  2  | Logika Program   |    20%       |
|  3  | Kesesuaian UI    |    15%       |
|  4  | Constructor      |    15%       |
|  5  | Memenuhi Variasi |    30%       |
|     | **TOTAL**        | 100%         |

8. Cara Menjalankan Program
Buka program di IDE seperti NetBeans atau Eclipse.
Jalankan program, masukkan harga asli pada kolom "Harga".
Pilih diskon menggunakan combo box atau slider.
Jika memiliki kode kupon "DISKON10", masukkan di kolom "Kode Diskon".
Klik "Hitung" untuk melihat harga akhir dan penghematan.
Riwayat perhitungan akan muncul di area riwayat.
Klik "Keluar" untuk menutup aplikasi.
