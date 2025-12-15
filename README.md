# Genetik Algoritma ile Kimyasal Reaksiyon Optimizasyonu

Bu proje, bir kimya tesisindeki üretim verimliliğini maksimize etmek amacıyla **Genetik Algoritma (Genetic Algorithm)** kullanılarak geliştirilmiş bir optimizasyon uygulamasıdır. 

Proje, belirli kısıtlamalar altında (sıcaklık ve süre sınırları) en yüksek verimi sağlayacak parametreleri evrimsel hesaplama yöntemleriyle bulur.

## 📋 Öğrenci Bilgileri

* **Adı:** Ceyda
* **Soyadı:** Metin
* **Okul Numarası:** 2212721025
* **Ders:** Yapay Zeka / Algoritmalar (Dersin Tam Adı)

---

## 🧪 Proje Senaryosu (Senaryo 5)

Bu çalışmada gerçek bir hayat problemi olan **"Kimya Tesisinde Reaksiyon Süresi ve Sıcaklık Ayarı"** modellenmiştir. 

### Amaç Fonksiyonu
Sistemin verimliliği ($y$), reaksiyon süresi ($x_1$) ve sıcaklığa ($x_2$) bağlı olarak aşağıdaki formülle hesaplanmaktadır:

$$y = 8x_1 + 3x_2 - x_1x_2 + x_1^2$$

### Değişkenler ve Sınırlar
Genetik algoritma, aşağıdaki aralıklarda en uygun $x_1$ ve $x_2$ değerlerini arar:
* **$x_1$ (Reaksiyon Süresi):** 10 ile 60 dakika arası.
* **$x_2$ (Sıcaklık):** 60 ile 120 °C arası (Kısıt gereği alt sınır revize edilmiştir).

### Kısıtlar (Constraints)
Sistemin fiziksel sınırları gereği, süre ve sıcaklık toplamı belirli bir değeri aşamaz:
* $$x_1 + x_2 \le 140$$

---

## 🧬 Algoritmanın Çalışma Mantığı

Bu projede kullanılan Genetik Algoritma, doğadaki evrim sürecini taklit eder. Süreç şu adımlardan oluşur:

1.  **Popülasyon Oluşturma:** Çözüm uzayında rastgele 20 adet birey (çözüm adayı) oluşturulur. Her birey bir kromozom setine ($x_1, x_2$) sahiptir.
2.  **Uygunluk (Fitness) Hesaplama:** Her bireyin formüldeki başarısı (verim skoru) hesaplanır.
    * *Ceza Yöntemi (Penalty Method):* Eğer bir birey $x_1 + x_2 \le 140$ kuralını ihlal ederse, skoru çok düşük bir değere (-99999) çekilerek elenmesi sağlanır.
3.  **Seçilim (Selection):** En yüksek skora sahip bireyler (Elitizm) bir sonraki nesle aktarılmak üzere seçilir.
4.  **Çaprazlama (Crossover):** Seçilen ebeveynlerin genleri karıştırılarak (Tek Noktalı Çaprazlama) yeni çocuklar üretilir.
5.  **Mutasyon:** Yerel tuzaklardan kurtulmak ve çeşitliliği sağlamak amacıyla, belirli bir olasılıkla (%10) genlerde rastgele küçük değişimler yapılır.

Bu döngü **50 nesil** boyunca devam eder ve her nesilde çözüm iyileştirilir.

---

## 🛠️ Kurulum ve Çalıştırma

Bu projeyi kendi bilgisayarınızda çalıştırmak için aşağıdaki adımları izleyebilirsiniz.

### Gereksinimler
Proje **Python 3** ile yazılmıştır. Görselleştirme için `matplotlib` kütüphanesine ihtiyaç duyar.

Gerekli kütüphaneyi yüklemek için terminale şu kodu yazın:
```bash
pip install matplotlib


Çalıştırma
Projeyi indirdikten sonra, terminal veya komut satırında proje klasörüne giderek şu komutu çalıştırın:
python main.py
# Veya Jupyter Notebook kullanıyorsanız .ipynb dosyasını çalıştırın.

📊 Sonuçlar ve Görselleştirme
Algoritma çalıştığında:

Her 10 nesilde bir en iyi skoru ekrana yazdırır.

İşlem bittiğinde En İyi Süre, En İyi Sıcaklık ve Maksimum Verim değerlerini raporlar.

Nesiller boyunca gelişimi gösteren bir Performans Grafiği (Convergence Plot) çizer.
⚠️ Önemli Notlar
Hazır Kütüphane Kullanımı: Bu projede scikit-opt veya benzeri hazır genetik algoritma kütüphaneleri kullanılmamış, algoritmanın temel mantığı (seleksiyon, çaprazlama, mutasyon) tarafımdan saf Python kodu ile yazılmıştır.

Özgünlük: Kod yapısı ve yorum satırları tamamen özgün bir çalışmadır.
