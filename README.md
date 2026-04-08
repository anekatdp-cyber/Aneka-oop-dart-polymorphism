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
  // abstract method
  void bekerja();

  // non-abstract method
  void istirahat() {
    print("Sedang istirahat");
  }
}

// 2. IMPLEMENTASI CLASS
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
```
