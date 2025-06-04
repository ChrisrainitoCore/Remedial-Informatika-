# Remedial-Informatika-
abstract class Kendaraan {
    private String merk; 
    private int tahunProduksi;

    public Kendaraan(String merk, int tahunProduksi) {
        this.merk = merk;
        this.tahunProduksi = tahunProduksi;
    }

    public String getMerk() {
        return merk;
    }

    public int getTahunProduksi() {
        return tahunProduksi;
    }

    public abstract void info();
}

class Mobil extends Kendaraan {
    private int jumlahPintu;

    public Mobil(String merk, int tahunProduksi, int jumlahPintu) {
        super(merk, tahunProduksi);
        this.jumlahPintu = jumlahPintu;
    }

    @Override
    public void info() {
        System.out.println("Mobil " + getMerk() + " tahun " + getTahunProduksi() + 
                          " dengan " + jumlahPintu + " pintu.");
    }

    public void klakson() {
        System.out.println("Tin tin!");
    }
}

class Motor extends Kendaraan {
    private String jenisMotor;

    public Motor(String merk, int tahunProduksi, String jenisMotor) {
        super(merk, tahunProduksi);
        this.jenisMotor = jenisMotor;
    }

    @Override
    public void info() {
        System.out.println("Motor " + getMerk() + " tahun " + getTahunProduksi() + 
                          ", jenis: " + jenisMotor);
    }

    public void klakson() {
        System.out.println("Tit tit!");
    }
}

public class App {
    public static void main(String[] args) {
    
        Kendaraan kendaraan1 = new Mobil("Toyota", 2020, 4);
        Kendaraan kendaraan2 = new Motor("Honda", 2021, "Sport");
        
        kendaraan1.info(); 
        kendaraan2.info(); 
        
        if (kendaraan1 instanceof Mobil) {
            ((Mobil) kendaraan1).klakson();
        }
        
        if (kendaraan2 instanceof Motor) {
            ((Motor) kendaraan2).klakson();
        }
        
        System.out.println("Merk kendaraan1: " + kendaraan1.getMerk());
        System.out.println("Tahun produksi kendaraan2: " + kendaraan2.getTahunProduksi());
    }
}
