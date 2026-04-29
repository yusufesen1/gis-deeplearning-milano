# 🏢 Milano Bina Tespiti (U-Net + Sentinel-2)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/KULLANICI_ADIN/REPO_ADIN/blob/main/milano_building_detection.ipynb)

Uydu görüntüsünden derin öğrenme tabanlı **semantic segmentation** ile bina alanlarının otomatik tespiti. Çalışma alanı: Milano, İtalya (Via Luca Ghini bölgesi).

## 📊 Sonuçlar

- **Ortalama IoU:** %85.1 (profesyonel araştırma seviyesi)
- **Eğitim süresi:** ~6 dakika (NVIDIA Tesla T4 GPU)
- **Model:** U-Net (31M parametre)
- **Eğitim veri seti:** 6 tile × 8 augmentation = 40 örnek

## 🛠️ Kullanılan Teknolojiler

- **Python** (PyTorch, geoai, rasterio, geopandas)
- **Google Colab** + NVIDIA Tesla T4 GPU
- **Sentinel-2** uydu görüntüsü (Microsoft Planetary Computer)
- **Overture Maps** bina poligonları (8.551 bina)
- **U-Net** segmentasyon mimarisi

## 📂 Proje Akışı

1. Çalışma alanı tanımlama (Bbox)
2. Sentinel-2 görüntüsü indirme (RGB bantları)
3. Overture Maps'ten bina verisi indirme
4. CRS dönüşümü ve hizalama
5. 256×256 tile üretme (%50 örtüşme)
6. Maske düzeltme (instance → semantic)
7. PyTorch Dataset + Augmentation
8. U-Net mimarisi
9. 50 epoch eğitim (Adam + BCE+Dice loss)
10. IoU değerlendirme
11. Via Luca Ghini bölgesinde test (genelleştirme)

## 🎯 Performans Metrikleri

| Tile | IoU |
|------|-----|
| Tile 1 (Tarihi merkez) | 0.890 |
| Tile 2 (Yoğun şehir) | 0.875 |
| Tile 3 (Orta yoğunluk) | 0.876 |
| Tile 4 (Kenar mahalle) | 0.858 |
| Tile 5 (Modern semt) | 0.846 |
| Tile 6 (Şehir-kırsal sınırı) | 0.760 |
| **Ortalama** | **0.851** |

## 🚀 Kullanım

Yukarıdaki "Open in Colab" butonuna tıklayarak notebook'u Google Colab'da doğrudan açıp çalıştırabilirsiniz. GPU gereksinimi: NVIDIA Tesla T4 (Colab ücretsiz sürümünde mevcut).

## 📚 Veri Kaynakları

- **Sentinel-2:** [Microsoft Planetary Computer](https://planetarycomputer.microsoft.com/)
- **Overture Maps:** [overturemaps.org](https://overturemaps.org/)

## 👤 Yazar

**Yusuf Mıraz Esen**

OpenGIS Türkiye | Açık Kaynak CBS Kullanıcıları Topluluğu

---

⭐ Bu proje yapay zeka + coğrafi bilgi sistemleri (GIS + AI) entegrasyonunun pratik bir uygulamasıdır.
