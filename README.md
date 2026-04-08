# 📘 RESUME SESI 4

## Polimorfisme & Abstraksi (Dart)

### 🎯 Tujuan
Peserta memahami konsep Polimorfisme dan Abstraksi serta mampu mengimplementasikannya dalam program Dart.

---

# 🧠 1. POLIMORFISME

## 📌 Pengertian
Polimorfisme adalah kemampuan objek untuk memiliki banyak bentuk, biasanya melalui inheritance (pewarisan).

## 📌 Contoh Konsep
Satu method → hasil berbeda tergantung objeknya.

## 💡 Contoh Polimorfisme (Inheritance)

```dart
class Hewan {
  void bersuara() {
    print("Hewan bersuara");
  }
}

class Kucing extends Hewan {
  @override
  void bersuara() {
    print("Meong");
  }
}

class Anjing extends Hewan {
  @override
  void bersuara() {
    print("Guk Guk");
  }
}

void main() {
  Hewan h1 = Kucing();
  Hewan h2 = Anjing();

  h1.bersuara();
  h2.bersuara();
}

```

## 📌 Manfaat Polimorfisme
Kode lebih fleksibel
Mudah dikembangkan
Mengurangi duplikasi kode

## 🔍 Operator is dan as
🧠 Operator is (cek tipe data)

```dart
class Hewan {}
class Kucing extends Hewan {}

void main() {
  Hewan hewan = Kucing();

  if (hewan is Kucing) {
    print("Ini kucing");
  }
}
```
### Output:
Ini kucing

## 🔄 Operator as (casting)
```dart
class Hewan {
  void bersuara() {
    print("Hewan bersuara");
  }
}

class Kucing extends Hewan {
  @override
  void bersuara() {
    print("Meong");
  }
}

void main() {
  Hewan hewan = Kucing();

  (hewan as Kucing).bersuara();
}
```
### Output:
Meong


## 🧪 Contoh Polimorfisme (List)
```dart
class Hewan {
  void bersuara() {
    print("Hewan bersuara");
  }
}

class Kucing extends Hewan {
  @override
  void bersuara() => print("Meong");
}

class Anjing extends Hewan {
  @override
  void bersuara() => print("Guk Guk");
}

class Burung extends Hewan {
  @override
  void bersuara() => print("Cuit Cuit");
}

void main() {
  List<Hewan> daftarHewan = [
    Kucing(),
    Anjing(),
    Burung()
  ];

  for (var h in daftarHewan) {
    h.bersuara();
  }
}
```

## 🧠 2. ABSTRAKSI
## 📌 Pengertian

Abstraksi adalah menyembunyikan detail implementasi dan hanya menampilkan fungsi penting.

## 🧩 Abstract Class
```dart
abstract class Kendaraan {
  void jalan();
}

class Mobil extends Kendaraan {
  @override
  void jalan() {
    print("Mobil berjalan");
  }
}

void main() {
  Kendaraan mobil = Mobil();
  mobil.jalan();
}
```
## 🔌 Interface (implements)
```dart
class Mesin {
  void nyala() {}
}

class Motor implements Mesin {
  @override
  void nyala() {
    print("Mesin motor nyala");
  }
}

void main() {
  Motor motor = Motor();
  motor.nyala();
}
```
## ⚖️ Perbedaan extends vs implements
 extends	implements
Turunan class	Implementasi interface
Bisa pakai method parent	Wajib override semua method
Relasi "is-a"	Kontrak

## 🧮 Static Members & Method
### 📌 Pengertian

Static adalah method atau variabel yang dimiliki oleh class, bukan objek.

```dart
class MathUtil {
  static int tambah(int a, int b) {
    return a + b;
  }
}

void main() {
  print(MathUtil.tambah(2, 3));
}
```
## 💼 CONTOH KASUS
### 💳 Sistem Pembayaran
```dart
abstract class Pembayaran {
  void bayar();
}

class TransferBank extends Pembayaran {
  @override
  void bayar() {
    print("Bayar via transfer");
  }
}

class EWallet extends Pembayaran {
  @override
  void bayar() {
    print("Bayar via e-wallet");
  }
}

void main() {
  Pembayaran p1 = TransferBank();
  Pembayaran p2 = EWallet();

  p1.bayar();
  p2.bayar();
}
```
### Output:
Bayar via transfer
Bayar via e-wallet


## 🔷 Sistem Geometri
```dart
abstract class Bentuk {
  double hitungLuas();
}

class Persegi extends Bentuk {
  double sisi;

  Persegi(this.sisi);

  @override
  double hitungLuas() => sisi * sisi;
}

void main() {
  Bentuk persegi = Persegi(4);
  print("Luas Persegi: ${persegi.hitungLuas()}");
}
```

### Output:
Luas Persegi: 16.0

## BONUS 1

import 'dart:math';

// 1. ABSTRACT CLASS (ADA ABSTRACT + NON-ABSTRACT METHOD)
```dart
abstract class Pekerja {
  void bekerja();

  void istirahat() {
    print("Sedang istirahat");
  }
}

class Programmer extends Pekerja {
  @override
  void bekerja() {
    print("Programmer sedang coding");
  }
}

class Dokter extends Pekerja {
  @override
  void bekerja() {
    print("Dokter sedang memeriksa pasien");
  }
}

class Guru extends Pekerja {
  @override
  void bekerja() {
    print("Guru sedang mengajar");
  }
}


void main() {
  List<Pekerja> pekerjaList = [
    Programmer(),
    Dokter(),
    Guru(),
  ];

  for (var p in pekerjaList) {
    p.bekerja();
    p.istirahat();
  }
}

```
## BONUS 2
```dart
class Komputer {
  void coding() {
    print("Menjalankan coding");
  }
}

class Kamera {
  void foto() {
    print("Mengambil foto");
  }
}

class Telepon {
  void telpon() {
    print("Melakukan panggilan");
  }
}

void main() {
  Komputer k = Komputer();
  k.coding();

  Kamera cam = Kamera();
  cam.foto();

  Telepon t = Telepon();
  t.telpon();
}

```
## BONUS 3
```dart
import 'dart:math';

class MathUtils {
  // 1. Faktorial
  static int faktorial(int n) {
    if (n <= 1) return 1;
    return n * faktorial(n - 1);
  }

  // 2. Cek bilangan prima
  static bool isPrima(int n) {
    if (n < 2) return false;
    for (int i = 2; i <= sqrt(n); i++) {
      if (n % i == 0) return false;
    }
    return true;
  }

  // 3. Pembulatan desimal
  static double roundDouble(double value, int places) {
    double mod = pow(10, places).toDouble();
    return (value * mod).round() / mod;
  }

  // 4. Random integer [min, max]
  static int randomInt(int min, int max) {
    return min + Random().nextInt(max - min + 1);
  }

  // 5. Random double [min, max]
  static double randomDouble(double min, double max) {
    return min + Random().nextDouble() * (max - min);
  }

  // 6. Rata-rata
  static double rataRata(List<int> data) {
    return data.reduce((a, b) => a + b) / data.length;
  }

  // 7. Median
  static double median(List<int> data) {
    List<int> sorted = List.from(data)..sort();
    int n = sorted.length;

    if (n % 2 == 1) {
      return sorted[n ~/ 2].toDouble();
    } else {
      return (sorted[n ~/ 2 - 1] + sorted[n ~/ 2]) / 2;
    }
  }
}

// WAJIB ADA MAIN AGAR BISA DIJALANKAN DI DARTPAD
void main() {
  print("=== MathUtils ===");

  print("Faktorial 5: ${MathUtils.faktorial(5)}");
  print("Prima 7: ${MathUtils.isPrima(7)}");
  print("Pembulatan: ${MathUtils.roundDouble(3.14159, 2)}");

  print("Random int: ${MathUtils.randomInt(1, 10)}");
  print("Random double: ${MathUtils.randomDouble(1, 10)}");

  List<int> data = [1, 2, 3, 4, 5];
  print("Rata-rata: ${MathUtils.rataRata(data)}");
  print("Median: ${MathUtils.median(data)}");
}
```
