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

## Metode Dalam Kelas Abstrak
### 1. Apa yang dimaksud dengan method dalam kelas abstrak?

Method dalam kelas abstrak adalah fungsi yang dideklarasikan di dalam abstract class yang digunakan sebagai pedoman bagi class turunannya. Method ini bisa berupa method tanpa isi maupun dengan isi.

### 2. Apa itu method abstrak?

Method abstrak adalah method yang tidak memiliki isi (body) dan wajib diimplementasikan oleh subclass (class turunan).

Contoh:
```dart
abstract class Mesin {
  void start();
}

class Motor extends Mesin {
  @override
  void start() {
    print("Mesin motor menyala");
  }
}

void main() {
  Motor motor = Motor();
  motor.start();
}
```
### 3. Apa itu method biasa (concrete method)?

Method biasa adalah method yang memiliki isi (implementasi) dan dapat langsung digunakan oleh subclass tanpa harus di-override.

Contoh:
```dart
abstract class Mesin {
  void stop() {
    print("Mesin berhenti");
  }
}

class Motor extends Mesin {}

void main() {
  Motor motor = Motor();
  motor.stop(); // langsung bisa dipakai
}
```
## BONUS 2
### 4. Apa perbedaan method abstrak dan method biasa?
Method Abstrak	Method Biasa
Tidak memiliki isi	Memiliki isi
Wajib di-override	Tidak wajib di-override
Hanya deklarasi	Sudah ada implementasi

## BONUS 3
### 5. Apa tujuan penggunaan method dalam kelas abstrak?

Tujuannya adalah untuk:

Menjadi kerangka (template) bagi subclass
Memastikan subclass memiliki method tertentu
Membantu penerapan konsep polimorfisme
Membuat kode lebih terstruktur dan konsisten
