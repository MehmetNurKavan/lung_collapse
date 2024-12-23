# Akciğer Hastalıkları Tespiti – Makine Öğrenimi Projesi

Bu proje, tıbbi görüntüler üzerinde çalışan bir makine öğrenimi modelinin, akciğer hastalıklarını (akciğer çökmesi, sağlıklı, verem ve zatüre) tespit etmek için geliştirilmesini içerir. Veri setleri özel olarak düzenlenmiştir ve test ve eğitim veri setleri program tarafından istenilen oranlarda ayrılmıştır.

## Veri Seti

- **Veri kaynağı**: [Google Drive Linki](https://drive.google.com/file/d/1T0ZrHiic1WarBCEGd8yONws6lvTNm-pj/view?usp=sharing)
- **Veri Dağılımı**:
  - **Akciğer Çökmesi**: 10.047 görüntü, 1024x1024 boyutunda
  - **Sağlıklı**: 6.666 görüntü, karışık boyutlarda
  - **Verem**: 3.369 görüntü, 200x256 çapraz boyutlar
  - **Zatüre**: 4.273 görüntü, karışık boyutlarda

Görüntüler, 128x128 boyutuna yeniden boyutlandırılmış ve normalize edilmiştir.

## Model Mimarisinin Özellikleri

- **Temel Model**: MobileNetV2, transfer öğrenme kullanılmıştır.
- **Katmanlar**:
  - Fully Connected (Dense) katmanlar: 256 nöron, ReLU aktivasyonu.
  - Dropout katmanı: Overfitting'i azaltmak için 0.5 oranı.
- **Optimizasyon**:
  - Optimizer: Adam (learning rate: 0.0001)
  - Loss: Categorical Crossentropy
  - Erken durdurma ve öğrenme oranı azaltma gibi callback fonksiyonları kullanılmıştır.

## Proje İçeriği

1. **Veri Yükleme ve Ayrım**:
   - Veriler, verilen dizinden yüklenir.
   - Eğitim ve test veri setleri, %80 eğitim, %20 test olacak şekilde ayrılmıştır.
2. **Model Eğitimi**:
   - Veriler augmentation (döndürme, kaydırma, şekil bozuklukları) ile çeşitlendirilmiştir.
   - Model 15 epoch boyunca eğitilmiştir.
3. **Sonuçların Değerlendirilmesi**:
   - Karmaşıklık matrisi ve sınıflandırma raporu oluşturulmuştur.
   - Test verileri üzerindeki başarı oranı analiz edilmiştir.
4. **Görsel Tahmin**:
   - Rastgele seçilen görüntüler tahmin edilmiş ve gerçek/yanlış etiketi gösterilmiştir.

## Proje Kullanımı

1. **Gerekli Kütüphaneleri Yükleyin**:
   ```bash
   pip install numpy pillow tensorflow matplotlib seaborn scikit-learn
