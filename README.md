# aplikasigudang
/*driver*/
import java.util.Scanner;

public class Driver {
	public static void main (String[] args){
		Gudang g = new Gudang("PT. Toleng");
		Pegawai p1 = new Pegawai("Raka","123");
		PerusahaanSupplier ps = new PerusahaanSupplier("PT. Raka","PTR");
                Barang b1 = new Barang("Sunsilk","Shampo",5,ps);
		g.addBarang(b1);
		b1.setPJ(p1);
		/*System.out.println(b1.toString());*/
		System.out.println(g.searchBarang("Makan"));
                System.out.println(g.toString());
	}
}

/*gudang*/

public class Gudang {

    private String nama;
    private int totalBarang = 0;
    private Barang[] b = new Barang[50];
    private int i;

    public Gudang(String nama) {
        this.nama = nama;
    }

    public String searchBarang(String cari) {
        try {
            int i;
            for (i = 0; i >= totalBarang; i++) {
                if (b[i].getNama() == cari) {
                    break;
                }
                throw new IllegalArgumentException("Hasil ditemukan");
            }
        } catch (IllegalArgumentException e) {
            System.out.println("Hasil tidak dapat ditemukan");
        }
        return b[i].toString();
    }

    public void addBarang(Barang b) {
        this.b[totalBarang] = b;
        totalBarang++;
    }

    public int getTotalBarang() {
        return totalBarang;
    }

    public String getNama() {
        return nama;
    }
    public String toString(){
        return "Nama Gudang : "+getNama()+"\nTotal Barang : "+getTotalBarang();
    }
}

/*pegawai*/

public class Pegawai{
	private String nama,kodePegawai;
	private Barang b;
	public Pegawai (String nama, String kodePegawai){
		this.nama=nama;
		this.kodePegawai=kodePegawai;
		try{
            if(kodePegawai.length()!=5){
                throw new IllegalArgumentException("Kode pegawain tidak 5 digit");
            }}catch (IllegalArgumentException e){
                    throw new IllegalArgumentException();}
	}
	public String getNama(){
		return nama;
	}
	public String getKodePegawai(){
		return kodePegawai;
	}
	public String toString(){
		return "/nNama Pegawai : "+getNama()+"/nNIP : "+kodePegawai;
	}
}

/*perusahaansupplier*/


public class PerusahaanSupplier {

    private String nama, kode;

    public PerusahaanSupplier(String nama, String kode) {
        this.nama = nama;
        this.kode = kode;
    }

    public String getNama() {
        return nama;
    }

    public String getKode() {
        return kode;
    }

    public void setNama(String nama) {
        this.nama = nama;
    }

    public void setKode(String kode) {
        this.kode = kode;
    }

}

/*barang*/

public class Barang {

    private String nama, jenis;
    private int jumlah;
    private PerusahaanSupplier perusahaan;
    private Pegawai PJ;

    public Barang(String nama, String jenis, int jumlah, PerusahaanSupplier perusahaan) {
        try {
            this.nama = nama;
            this.jenis = jenis;
            this.jumlah = jumlah;
            this.perusahaan = perusahaan;
            throw new IllegalArgumentException("Inputan benar");
        }catch (IllegalArgumentException e){
            System.out.println("Inputan salah");
        }

    }

    public String getNama() {
        return nama;
    }

    public String getJenis() {
        return jenis;
    }

    public int getJumlah() {
        return jumlah;
    }

    public void setNamaPerusahaan(String nama) {
        perusahaan.setNama(nama);
    }

    public String getNamaPerusahaan() {
        return perusahaan.getNama();
    }

    @Override
    public String toString() {
        return "\nNama Barang : " + nama + "\nJenis Barang : " + jenis + "\nNama perusahaan : " + getNamaPerusahaan() + "\nNama Pegawai Penanggung Jawab: " + getNamaPJ();
    }

    public void setPJ(Pegawai PJ) {
        this.PJ = PJ;
    }

    public String getNamaPJ() {
        return PJ.getNama();
    }
}

