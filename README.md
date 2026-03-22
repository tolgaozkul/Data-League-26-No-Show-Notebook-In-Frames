# 🏥 Data League '26: Hospital No-Show Prediction
## Team In Frames - Kaggle Yarışması Çözüm Notebook'u

Bu depo (repository), **Data League '26** veri bilimi yarışması için **In Frames** takımı tarafından geliştirilen çözüm notebook'unu içermektedir.

**Takım Üyeleri:** Tolga ÖZKUL, Burak Turan, Atalay Aktaş

---

## 🎯 Proje Amacı
Sağlık sistemlerinde ciddi kaynak israfına yol açan "randevuya gelmeme (No-Show)" problemini önceden tahmin etmek. 200.000'den fazla sentetik randevu kaydı üzerinden, hastaların randevuya gelmeme olasılıkları makine öğrenmesi modelleriyle hesaplanmıştır. Sınıf dengesizliği (%24 No-Show) sebebiyle temel değerlendirme metriği olarak **PR-AUC (Average Precision)** kullanılmıştır.

## 🚀 Teknik Yaklaşım
1. **Feature Engineering:** Zaman bazlı özellikler (`clinic_hour_count`), geçmiş randevu oranları ve klinik bazlı istatistikler türetilmiş; sızıntı (data leakage) yaratabilecek tüm veriler özenle ayıklanmıştır.
2. **Validasyon:** Zaman bazlı genellemeyi doğru ölçmek için **StratifiedKFold (5-Fold)** ile OOF (Out-of-Fold) tahminleri kullanılmıştır.
3. **Modelleme (Ensemble):** Kategorik değişkenlerdeki performansı ve farklı Gradient Boosting algoritmalarının avantajlarını birleştirmek için ağırlıklı harmanlama (blend) yapılmıştır:
   * **%45 CatBoost**
   * **%35 LightGBM**
   * **%20 XGBoost**

## 🏆 Sonuçlar
* **Local OOF PR-AUC:** 0.49919
* **Public Leaderboard:** 0.51573
* **Private Leaderboard:** 0.50731
* **Final Sıralaması:** 72 takım arasında **15. sıra** 🥈

## 💻 Kurulum ve Çalıştırma

GitHub dosya boyutu sınırları nedeniyle veri seti (.csv) dosyaları bu depoya **eklenmemiştir**. Projeyi kendi ortamınızda incelemek ve çalıştırmak için aşağıdaki adımları izleyebilirsiniz:

1. Repoyu bilgisayarınıza klonlayın:
   ```bash
   git clone https://github.com/tolgaozkul/Data-League-26-No-Show-Notebook-In-Frames.git
   ```

2. Veri setini [Kaggle Veri Seti Sayfasından (tolgaozkul)](https://www.kaggle.com/datasets/tolgaozkul/data-league-26-no-show-dataset) indirin.

3. İndirdiğiniz veri seti dosyalarını (`appointments_train.csv`, `appointments_test.csv`, `patients.csv`, `clinics.csv`) klonladığınız dizinin içine (notebook ile aynı yere) yerleştirin.

4. Gerekli kütüphanelerin yüklü olduğundan emin olun:
   ```bash
   pip install pandas numpy scikit-learn lightgbm catboost xgboost
   ```

5. `data-league-26-final-notebook-team-in-frames.ipynb` dosyasını Jupyter Notebook veya VS Code üzerinden açarak çalıştırın.
