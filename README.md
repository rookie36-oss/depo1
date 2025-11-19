// Basit Java Dosya Okuma-Yazma Projesi
// FileIOProject.java

import java.io.*;
import java.util.*;

public class FileIOProject {
    private static final String FILE_NAME = "data.txt";

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("\n=== DOSYA OKUMA - YAZMA PROJESİ ===");
            System.out.println("1) Dosyaya yaz");
            System.out.println("2) Dosyadan oku");
            System.out.println("3) Çıkış");
            System.out.print("Seçiminiz: ");

            int secim = scanner.nextInt();
            scanner.nextLine();

            switch (secim) {
                case 1:
                    System.out.print("Yazılacak metni girin: ");
                    String metin = scanner.nextLine();
                    dosyayaYaz(metin);
                    break;

                case 2:
                    dosyadanOku();
                    break;

                case 3:
                    System.out.println("Çıkılıyor...");
                    return;

                default:
                    System.out.println("Hatalı seçim!");
            }
        }
    }

    // Dosyaya yazma
    public static void dosyayaYaz(String metin) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(FILE_NAME, true))) {
            writer.write(metin);
            writer.newLine();
            System.out.println("Metin başarıyla dosyaya yazıldı.");
        } catch (IOException e) {
            System.out.println("Yazma hatası: " + e.getMessage());
        }
    }

    // Dosyadan okuma
    public static void dosyadanOku() {
        try (BufferedReader reader = new BufferedReader(new FileReader(FILE_NAME))) {
            String satir;
            System.out.println("--- DOSYA İÇERİĞİ ---");
            while ((satir = reader.readLine()) != null) {
                System.out.println(satir);
            }
        } catch (FileNotFoundException e) {
            System.out.println("Dosya bulunamadı. Önce dosyaya yazmayı deneyin.");
        } catch (IOException e) {
            System.out.println("Okuma hatası: " + e.getMessage());
        }
    }
}
