// Basit C++ Dosya Okuma - Yazma Projesi
// FileIOProject.cpp

#include <iostream>
#include <fstream>
#include <string>
using namespace std;

const string FILE_NAME = "data.txt";

void dosyayaYaz(const string& metin) {
    ofstream file(FILE_NAME, ios::app);
    if (!file) {
        cout << "Yazma hatası!" << endl;
        return;
    }
    file << metin << endl;
    cout << "Metin başarıyla dosyaya yazıldı." << endl;
}

void dosyadanOku() {
    ifstream file(FILE_NAME);
    if (!file) {
        cout << "Dosya bulunamadı. Önce dosyaya yazmayı deneyin." << endl;
        return;
    }

    string satir;
    cout << "--- DOSYA İÇERİĞİ ---" << endl;
    while (getline(file, satir)) {
        cout << satir << endl;
    }
}

int main() {
    int secim;
    string metin;

    while (true) {
        cout << "\n=== DOSYA OKUMA - YAZMA PROJESİ ===" << endl;
        cout << "1) Dosyaya yaz" << endl;
        cout << "2) Dosyadan oku" << endl;
        cout << "3) Çıkış" << endl;
        cout << "Seçiminiz: ";
        cin >> secim;
        cin.ignore(); // Buffer temizleme

        switch (secim) {
            case 1:
                cout << "Yazılacak metni girin: ";
                getline(cin, metin);
                dosyayaYaz(metin);
                break;
            case 2:
                dosyadanOku();
                break;
            case 3:
                cout << "Çıkılıyor..." << endl;
                return 0;
            default:
                cout << "Hatalı seçim!" << endl;
        }
    }
}

