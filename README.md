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

```dart
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
  List<Hewan> daftarHewan = [
    Kucing(),
    Anjing(),
    Burung()
  ];

  for (var hewan in daftarHewan) {
    hewan.bersuara();
  }
}

Praktik 2 – Sistem Pembayaran

```dart
abstract class MetodePembayaran {
  void bayar(double jumlah);
}

class KartuKredit implements MetodePembayaran {
  @override
  void bayar(double jumlah) {
    print("Bayar Rp$jumlah dengan Kartu Kredit");
  }
}

class EWallet implements MetodePembayaran {
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
  List<MetodePembayaran> metode = [
    KartuKredit(),
    EWallet(),
    Tunai()
  ];

  for (var m in metode) {
    m.bayar(50000);
  }
}

### 🔸 Latihan (Lengkap 1–5)

```dart
import 'dart:math';

// =======================
// 1–3. PEKERJA (POLIMORFISME)
// =======================
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

// =======================
// 4. TABLET
// =======================
class Komputer {
  void prosesData() => print("Memproses data");
}

class Kamera {
  void ambilFoto() => print("Mengambil foto");
}

class Telepon {
  void telpon() => print("Melakukan panggilan");
}

class Tablet implements Komputer, Kamera, Telepon {
  @override
  void prosesData() => print("Tablet memproses data");

  @override
  void ambilFoto() => print("Tablet mengambil foto");

  @override
  void telpon() => print("Tablet melakukan panggilan");
}

// =======================
// 5. MATH UTILS (LENGKAP)
// =======================
class MathUtils {
  static int factorial(int n) =>
      n <= 1 ? 1 : n * factorial(n - 1);

  static bool isPrime(int n) {
    if (n < 2) return false;
    for (int i = 2; i <= sqrt(n); i++) {
      if (n % i == 0) return false;
    }
    return true;
  }

  static double roundTo(double value, int decimal) {
    double mod = pow(10, decimal).toDouble();
    return (value * mod).round() / mod;
  }

  static int randomInt(int min, int max) {
    return min + Random().nextInt(max - min + 1);
  }

  static double randomDouble(double min, double max) {
    return min + Random().nextDouble() * (max - min);
  }

  static double average(List<double> data) {
    return data.reduce((a, b) => a + b) / data.length;
  }

  static double median(List<double> data) {
    data.sort();
    int mid = data.length ~/ 2;

    if (data.length % 2 == 0) {
      return (data[mid - 1] + data[mid]) / 2;
    } else {
      return data[mid];
    }
  }
}

// =======================
// MAIN
// =======================
void main() {
  print("=== POLIMORFISME PEKERJA ===");
  List<Pekerja> pekerja = [
    Programmer(),
    Dokter(),
    Guru()
  ];

  for (var p in pekerja) {
    p.info();
    p.bekerja();
    print("----------------");
  }

  print("\n=== TABLET ===");
  Tablet t = Tablet();
  t.prosesData();
  t.ambilFoto();
  t.telpon();

  print("\n=== MATH UTILS ===");
  print("Faktorial 5: ${MathUtils.factorial(5)}");
  print("Prima 7: ${MathUtils.isPrime(7)}");
  print("Pembulatan: ${MathUtils.roundTo(3.14159, 2)}");
  print("Random int: ${MathUtils.randomInt(1, 10)}");
  print("Random double: ${MathUtils.randomDouble(1, 5)}");
  print("Rata-rata: ${MathUtils.average([10, 20, 30])}");
  print("Median: ${MathUtils.median([10, 20, 30, 40])}");
}
```
---

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
