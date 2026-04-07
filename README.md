📘 RESUME SESI 4
Polimorfisme & Abstraksi (Dart)
🎯 Tujuan

Peserta memahami konsep Polimorfisme dan Abstraksi serta mampu mengimplementasikannya dalam program Dart.

🧠 1. POLIMORFISME
📌 Pengertian

Polimorfisme adalah kemampuan objek untuk memiliki banyak bentuk, biasanya melalui inheritance (pewarisan).

📌 Contoh Konsep

Satu method → hasil berbeda tergantung objeknya.

💡 Polimorfisme dengan Inheritance
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

📌 Manfaat Polimorfisme
Kode lebih fleksibel
Mudah dikembangkan
Mengurangi duplikasi kode

🔍 is dan as Operator
➤ is (cek tipe data)
if (hewan is Kucing) {
  print("Ini kucing");
}
➤ as (casting tipe)
(hewan as Kucing).bersuara();

🧪 Latihan Polimorfisme 
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
🧠 2. ABSTRAKSI
📌 Pengertian

Abstraksi adalah menyembunyikan detail implementasi dan hanya menampilkan fungsi penting.

🧩 Abstract Class
abstract class Kendaraan {
  void jalan();
}
⚙️ Abstract Method
class Mobil extends Kendaraan {
  @override
  void jalan() {
    print("Mobil berjalan");
  }
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

🔷 2. Sistem Bentuk Geometri
abstract class Bentuk {
  double hitungLuas();
}

class Persegi extends Bentuk {
  double sisi;

  Persegi(this.sisi);

  @override
  double hitungLuas() => sisi * sisi;
}

Berikut saya buatkan 1 file Dart lengkap (sudah mencakup semua materi: polimorfisme, abstraksi, latihan, dan contoh kasus).
Tinggal copy ke DartPad (dartpad.dev) atau ke file main.dart di GitHub ✅

📄 main.dart (Siap Submit)
// ================================
// SESI 4 - POLIMORFISME & ABSTRAKSI
// ================================

void main() {
  print("=== POLIMORFISME ===");

  // Polimorfisme dengan List
  List<Hewan> daftarHewan = [
    Kucing(),
    Anjing(),
    Burung(),
  ];

  for (var h in daftarHewan) {
    h.bersuara(); // hasil berbeda (polimorfisme)
  }

  print("\n=== OPERATOR is & as ===");

  Hewan hewan = Kucing();

  if (hewan is Kucing) {
    print("Objek adalah Kucing");
  }

  (hewan as Kucing).bersuara();

  print("\n=== ABSTRAKSI ===");

  Kendaraan mobil = Mobil();
  mobil.jalan();

  print("\n=== INTERFACE ===");

  Motor motor = Motor();
  motor.nyala();

  print("\n=== STATIC METHOD ===");
  print("Hasil tambah: ${MathUtil.tambah(5, 3)}");

  print("\n=== SISTEM PEMBAYARAN ===");

  List<Pembayaran> metodeBayar = [
    TransferBank(),
    EWallet(),
  ];

  for (var bayar in metodeBayar) {
    bayar.bayar();
  }

  print("\n=== SISTEM GEOMETRI ===");

  Bentuk persegi = Persegi(4);
  print("Luas Persegi: ${persegi.hitungLuas()}");
}

// ================================
// POLIMORFISME
// ================================

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

// ================================
// ABSTRAKSI
// ================================

abstract class Kendaraan {
  void jalan();
}

class Mobil extends Kendaraan {
  @override
  void jalan() {
    print("Mobil berjalan");
  }
}

// ================================
// INTERFACE (implements)
// ================================

class Mesin {
  void nyala() {}
}

class Motor implements Mesin {
  @override
  void nyala() {
    print("Mesin motor nyala");
  }
}

// ================================
// STATIC METHOD
// ================================

class MathUtil {
  static int tambah(int a, int b) {
    return a + b;
  }
}

// ================================
// CONTOH KASUS - PEMBAYARAN
// ================================

abstract class Pembayaran {
  void bayar();
}

class TransferBank extends Pembayaran {
  @override
  void bayar() {
    print("Bayar via Transfer Bank");
  }
}

class EWallet extends Pembayaran {
  @override
  void bayar() {
    print("Bayar via E-Wallet");
  }
}

// ================================
// CONTOH KASUS - GEOMETRI
// ================================

abstract class Bentuk {
  double hitungLuas();
}

class Persegi extends Bentuk {
  double sisi;

  Persegi(this.sisi);

  @override
  double hitungLuas() {
    return sisi * sisi;
  }
}
