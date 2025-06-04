# Remedial-Informatika-
// ABSTRACTION
abstract class Kendaraan {
    private String merk; // ENCAPSULATION (private field)
    private int tahunProduksi;

    public Kendaraan(String merk, int tahunProduksi) {
        this.merk = merk;
        this.tahunProduksi = tahunProduksi;
    }

    // ENCAPSULATION (getter methods)
    public String getMerk() {
        return merk;
    }

    public int getTahunProduksi() {
        return tahunProduksi;
    }

    // ABSTRACT METHOD (harus diimplementasikan oleh subclass)
    public abstract void info();
}

// HIERARCHICAL INHERITANCE (Kendaraan -> Mobil)
class Mobil extends Kendaraan {
    private int jumlahPintu;

    public Mobil(String merk, int tahunProduksi, int jumlahPintu) {
        super(merk, tahunProduksi);
        this.jumlahPintu = jumlahPintu;
    }

    // POLYMORPHISM (override method info)
    @Override
    public void info() {
        System.out.println("Mobil " + getMerk() + " tahun " + getTahunProduksi() + 
                          " dengan " + jumlahPintu + " pintu.");
    }

    public void klakson() {
        System.out.println("Tin tin!");
    }
}

// HIERARCHICAL INHERITANCE (Kendaraan -> Motor)
class Motor extends Kendaraan {
    private String jenisMotor;

    public Motor(String merk, int tahunProduksi, String jenisMotor) {
        super(merk, tahunProduksi);
        this.jenisMotor = jenisMotor;
    }

    // POLYMORPHISM (override method info)
    @Override
    public void info() {
        System.out.println("Motor " + getMerk() + " tahun " + getTahunProduksi() + 
                          ", jenis: " + jenisMotor);
    }

    public void klakson() {
        System.out.println("Tit tit!");
    }
}

public class DemoOOP {
    public static void main(String[] args) {
        // POLYMORPHISM (menggunakan parent class sebagai tipe referensi)
        Kendaraan kendaraan1 = new Mobil("Toyota", 2020, 4);
        Kendaraan kendaraan2 = new Motor("Honda", 2021, "Sport");
        
        kendaraan1.info(); // Akan memanggil method info dari Mobil
        kendaraan2.info(); // Akan memanggil method info dari Motor
        
        // Untuk memanggil method khusus subclass, perlu casting
        if (kendaraan1 instanceof Mobil) {
            ((Mobil) kendaraan1).klakson();
        }
        
        if (kendaraan2 instanceof Motor) {
            ((Motor) kendaraan2).klakson();
        }
        
        // ENCAPSULATION (mengakses field melalui getter)
        System.out.println("Merk kendaraan1: " + kendaraan1.getMerk());
        System.out.println("Tahun produksi kendaraan2: " + kendaraan2.getTahunProduksi());
    }
}
