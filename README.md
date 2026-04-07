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

</> markdown

##📌 Manfaat Polimorfisme
Kode lebih fleksibel
Mudah dikembangkan
Mengurangi duplikasi kode

##🔍 is dan as Operator
##🔍 Operator is dan as di Dart

##🧠 1. Operator is (cek tipe data)
##📌 Pengertian
is digunakan untuk mengecek apakah suatu objek termasuk tipe tertentu
👉 Hasilnya: true / false

💻 Contoh
class Hewan {}
class Kucing extends Hewan {}

void main() {
  Hewan hewan = Kucing();

  if (hewan is Kucing) {
    print("Ini kucing");
  }
}

👉 Output:
Ini kucing

🔄 2. Operator as (casting tipe data)
📌 Pengertian
as digunakan untuk mengubah tipe objek ke tipe tertentu (casting)

💻 Contoh
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

👉 Output:
Meong

⚠️ Penting!

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

  // cek tipe
  if (hewan is Kucing) {
    print("Ini kucing");
  }

  // casting
  (hewan as Kucing).bersuara();
}
🧪  **Polimorfisme**
Polimorfisme adalah:

Kemampuan satu method (fungsi) untuk memiliki banyak bentuk atau perilaku berbeda, tergantung objek yang memanggilnya.

📌 Penjelasan Sederhana

Bayangkan ada method:

bersuara()

👉 Tapi hasilnya bisa berbeda:

Kucing → Meong
Anjing → Guk Guk

➡️ Method sama, hasil berbeda

Contohnya ;

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

**🧠 2. ABSTRAKSI**
📌 Pengertian
Abstraksi adalah menyembunyikan detail implementasi dan hanya menampilkan fungsi penting.

🧩 Abstract Class

Contohnys ;

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
🔌 Interface di Dart

Semua class bisa jadi interface menggunakan implements

class Mesin {
  void nyala() {}
}

class Motor implements Mesin {
  @override
  void nyala() {
    print("Mesin motor nyala");
  }
}

⚖️ Perbedaan extends vs implements

extends	implements
Turunan class	Implementasi interface
Bisa pakai method parent	Harus override semua method
Relasi "is-a"	Kontrak

🧮 Static Members & Method
📌 Pengertian
Static Members & Method adalah:
Properti atau fungsi yang dimiliki oleh class, bukan oleh objek.

👉 Artinya:
Tidak perlu membuat object
Bisa langsung dipanggil dari nama class.

Contohnya ;

class MathUtil {
  static int tambah(int a, int b) {
    return a + b;
  }
}

void main() {
  print(MathUtil.tambah(2, 3));
}

💼 CONTOH KASUS
💳 1. Sistem Pembayaran
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
🎯 Output
Bayar via transfer
Bayar via e-wallet

🔷 2. Sistem Bentuk Geometri

Contohnya ;

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
🎯 Output
Luas Persegi: 16.0
