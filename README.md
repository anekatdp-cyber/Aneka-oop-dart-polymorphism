OOP Dart - Polimorfisme & Abstraksi
📌 Deskripsi

Repository ini berisi ringkasan materi Object Oriented Programming (OOP) pada Dart, khususnya tentang Polimorfisme dan Abstraksi.
Dilengkapi dengan contoh kode yang dapat langsung dijalankan di dartpad.dev.

🧠 Materi yang Dipelajari
🔹 Polimorfisme

Polimorfisme adalah konsep OOP yang memungkinkan satu method memiliki banyak bentuk tergantung objek yang memanggilnya.

✅ Polimorfisme dengan Inheritance

Subclass dapat mengubah (override) method dari parent class.

🎯 Manfaat Polimorfisme
Kode lebih fleksibel
Mudah dikembangkan
Mengurangi duplikasi kode
🔹 Operator is dan as

Digunakan untuk pengecekan dan konversi tipe data:

is → mengecek tipe objek
as → melakukan casting tipe
🔹 Abstraksi

Abstraksi adalah proses menyembunyikan detail kompleks dan hanya menampilkan fungsi penting.

📦 Abstract Class
Tidak bisa dibuat objek langsung
Digunakan sebagai blueprint
⚙️ Abstract Method
Method tanpa isi
Wajib diimplementasikan oleh subclass
🔹 Interface di Dart

Dart tidak memiliki keyword khusus untuk interface.
Namun, semua class bisa dijadikan interface menggunakan implements.

🔹 Perbedaan extends vs implements
extends	implements
Mewarisi semua method	Harus override semua method
Bisa pakai method parent	Tidak mewarisi implementasi
🔹 Static Members & Method
Digunakan tanpa membuat objek
Dipanggil langsung dari class

Contoh:

// ====== POLIMORFISME ======
class Hewan {
  void bersuara() {
    print("Hewan bersuara");
  }
}

class Kucing extends Hewan {
  @override
  void bersuara() {
    print("Meaw");
  }
}

class Anjing extends Hewan {
  @override
  void bersuara() {
    print("Guk Guk");
  }
}

class Singa extends Hewan {
  @override
  void bersuara() {
    print("Rwarrwgh");
  }
}

// ====== ABSTRACT CLASS ======
abstract class Kendaraan {
  void jalan(); // abstract method
}

class Mobil extends Kendaraan {
  @override
  void jalan() {
    print("Mobil berjalan");
  }
}

// ====== INTERFACE ======
class Terbang {
  void terbang() {}
}

class Pesawat implements Terbang {
  @override
  void terbang() {
    print("Pesawat terbang");
  }
}

// ====== STATIC ======
class Matematika {
  static int tambah(int a, int b) {
    return a + b;
  }
}

void main() {
  // ====== POLIMORFISME LIST ======
  List<Hewan> daftarHewan = [
    Kucing(),
    Anjing(),
    Singa()
  ];

  for (var hewan in daftarHewan) {
    hewan.bersuara();
  }

  // ====== IS & AS ======
  Hewan h = Kucing();

  if (h is Kucing) {
    print("Ini adalah Kucing");
  }

  Kucing k = h as Kucing;
  k.bersuara();

  // ====== ABSTRACT ======
  Mobil mobil = Mobil();
  mobil.jalan();

  // ====== INTERFACE ======
  Pesawat pesawat = Pesawat();
  pesawat.terbang();

  // ====== STATIC ======
  print(Matematika.tambah(7, 3));
}
