# Resume OOP Dart – Polimorfisme & Abstraksi

**Nama:** Risda Dwi Minarti
**NIM:** 23141022P
**Mata Kuliah:** Pemrograman Berorientasi Objek

---

## Ringkasan Materi

Pada sesi ini dibahas dua konsep utama dalam Object Oriented Programming (OOP), yaitu **Polimorfisme** dan **Abstraksi**.

### Polimorfisme

Polimorfisme adalah kemampuan suatu objek untuk memiliki banyak bentuk. Artinya, satu tipe data dapat digunakan untuk berbagai objek dengan perilaku yang berbeda.

Contoh: objek `Kucing`, `Anjing`, dan `Burung` dapat diperlakukan sebagai `Hewan`, namun menghasilkan suara yang berbeda.

**Manfaat:**

* Fleksibel
* Mudah dikembangkan
* Mengurangi duplikasi kode
* Mempermudah maintenance

---

### Abstraksi

Abstraksi adalah proses menyembunyikan detail implementasi dan hanya menampilkan fungsi utama.

Dilakukan dengan:

* `abstract class`
* `implements` (interface)

---

### Interface

Interface adalah kontrak yang harus diimplementasikan oleh class lain.

---

### Static Method

Static method adalah method milik class, digunakan tanpa membuat objek.

---

## Implementasi Program

Praktik 1 – Polimorfisme dengan List

abstract class Hewan {
  void bersuara();
}

class Kucing implements Hewan {
  @override
  void bersuara() => print("Kucing: Meong");
}

class Anjing implements Hewan {
  @override
  void bersuara() => print("Anjing: Guk guk");
}

class Burung implements Hewan {
  @override
  void bersuara() => print("Burung: Cuit cuit");
}

void main() {
  List<Hewan> daftarHewan = [Kucing(), Anjing(), Burung()];

  for (var hewan in daftarHewan) {
    hewan.bersuara();
  }
}

---

Praktik 2 – Sistem Pembayaran

abstract class MetodePembayaran {
  void bayar(double jumlah);
}

class KartuKredit implements MetodePembayaran {
  @override
  void bayar(double jumlah) {
    print("Bayar Rp$jumlah dengan Kartu Kredit");
  }
}

class Ewallet implements MetodePembayaran {
  @override
  void bayar(double jumlah) {
    print("Bayar Rp$jumlah dengan E-Wallet");
  }
}

class Tunai implements MetodePembayaran {
  @override
  void bayar(double jumlah) {
    print("Bayar Rp$jumlah dengan Tunai");
  }
}

void main() {
  MetodePembayaran metode;

  metode = KartuKredit();
  metode.bayar(100000);

  metode = Ewallet();
  metode.bayar(50000);

  metode = Tunai();
  metode.bayar(20000);
}

---

// 1–3. PEKERJA (POLIMORFISME)

abstract class Pekerja {
  void bekerja();

  void info() {
    print("Ini adalah pekerja");
  }
}

class Programmer implements Pekerja {
  @override
  void bekerja() => print("Programmer sedang coding");

  @override
  void info() => print("Profesi: Programmer");
}

class Dokter implements Pekerja {
  @override
  void bekerja() => print("Dokter memeriksa pasien");

  @override
  void info() => print("Profesi: Dokter");
}

class Guru implements Pekerja {
  @override
  void bekerja() => print("Guru mengajar");

  @override
  void info() => print("Profesi: Guru");
}

void main() {
  print("=== POLIMORFISME PEKERJA ===");

  List<Pekerja> pekerjaList = [Programmer(), Dokter(), Guru()];

  for (var p in pekerjaList) {
    p.info();
    p.bekerja();
    print("----------------");
  }
}

---

// 4. TABLET

abstract class Komputer {
  void prosesData();
}

abstract class Kamera {
  void ambilFoto();
}

abstract class Telepon {
  void telpon();
}

class Tablet implements Komputer, Kamera, Telepon {
  @override
  void prosesData() => print("Tablet memproses data");

  @override
  void ambilFoto() => print("Tablet mengambil foto");

  @override
  void telpon() => print("Tablet melakukan panggilan");

  void gunakanSemua() {
    prosesData();
    ambilFoto();
    telpon();
  }
}

void main() {
  Tablet t = Tablet();
  t.gunakanSemua();
}

---

import 'dart:math';

// 5. MATH UTILS

class MathUtils {
  // Faktorial
  static int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
  }

  // Cek bilangan prima
  static bool isPrime(int n) {
    if (n < 2) return false;
    for (int i = 2; i <= sqrt(n).toInt(); i++) {
      if (n % i == 0) return false;
    }
    return true;
  }

  // Pembulatan desimal
  static double roundTo(double value, int decimal) {
    double mod = pow(10, decimal).toDouble();
    return (value * mod).round() / mod;
  }

  // Random integer
  static int randomInt(int min, int max) {
    return min + Random().nextInt(max - min + 1);
  }

  // Random double
  static double randomDouble(double min, double max) {
    return min + Random().nextDouble() * (max - min);
  }

  // Rata-rata
  static double average(List<int> data) {
    return data.reduce((a, b) => a + b) / data.length;
  }

  // Median
  static double median(List<int> data) {
    data.sort();
    int mid = data.length ~/ 2;
    if (data.length % 2 == 0) {
      return (data[mid - 1] + data[mid]) / 2;
    } else {
      return data[mid].toDouble();
    }
  }
}

void main() {
  print("Faktorial 5: ${MathUtils.factorial(5)}");
  print("Apakah 7 prima: ${MathUtils.isPrime(7)}");
  print("Pembulatan: ${MathUtils.roundTo(3.14159, 2)}");
  print("Random int: ${MathUtils.randomInt(1, 10)}");
  print("Random double: ${MathUtils.randomDouble(1, 5)}");
  print("Rata-rata: ${MathUtils.average([1, 2, 3, 4, 5])}");
  print("Median: ${MathUtils.median([1, 2, 3, 4])}");
}


## Kesimpulan

* Polimorfisme memungkinkan satu tipe memiliki banyak perilaku
* Abstraksi menyederhanakan sistem
* Interface memastikan konsistensi implementasi
* Static method berguna untuk fungsi utilitas

---

## Dokumentasi

Tambahkan screenshot hasil running program dari DartPad di sini.

---

## Penutup

Dengan memahami Polimorfisme dan Abstraksi, program menjadi lebih fleksibel, terstruktur, dan mudah dikembangkan.
