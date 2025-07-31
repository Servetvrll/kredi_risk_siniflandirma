# Kredi Riski Sınıflandırma Projesi

## 📚 Proje Tanımı

Bu proje, bir finans kuruluşunun müşteri verilerini kullanarak kredi başvurusunun onaylanıp onaylanmayacağını (riskli olup olmadığını) tahmin eden bir makine öğrenimi modeli geliştirmeyi amaçlamaktadır.
Proje, veri analizi, önişleme, modelleme ve değerlendirme adımlarını kapsar. Amacımız, bankaların daha bilinçli kredi kararları almasına yardımcı olmak ve potansiyel finansal riskleri azaltmaktır.

## 📊 Veri Seti

Bu projede kullanılan veri seti, çeşitli kişisel ve finansal bilgileri içeren sentetik bir kredi başvuru veri setidir. Veri seti aşağıdaki ana sütunları içermektedir:

* `person_age`: Başvuranın yaşı
* `person_income`: Başvuranın yıllık geliri
* `person_home_ownership`: Başvuranın ev sahipliği durumu (Kira, Mortgage, Sahip, Diğer)
* `person_emp_length`: Başvuranın çalışma süresi (yıl)
* `loan_intent`: Kredi amacı (Eğitim, Sağlık, Kişisel, Girişimcilik vb.)
* `loan_grade`: Kredi derecesi (A, B, C, D, E, F, G)
* `loan_amnt`: Başvurulan kredi miktarı
* `loan_int_rate`: Kredi faiz oranı
* `loan_status`: Kredi durumu (0: Onaylandı/Düşük Risk, 1: Reddedildi/Yüksek Risk) - **Hedef Değişken**
* `loan_percent_income`: Kredi miktarının gelire oranı
* `cb_person_default_on_file`: Başvuranın daha önce temerrüde düşüp düşmediği (Y/N)
* `cb_person_cred_hist_length`: Başvuranın kredi geçmişi uzunluğu (yıl)

## 🚀 Proje Adımları

Proje aşağıdaki ana adımları içermektedir:

1.  **Veri Yükleme ve Genel Bakış:** Veri setinin yüklenmesi, ilk 5 satırının ve genel bilgilerinin (veri tipleri, sütunlar vb.) incelenmesi.
2.  **Keşifsel Veri Analizi (EDA):**
    * Sayısal ve kategorik sütunların dağılımlarının incelenmesi.
    * Eksik değerlerin tespiti ve analizi.
    * Aykırı değerlerin belirlenmesi.
    * Sınıf dengesizliğinin incelenmesi.
3.  **Veri Temizliği ve Önişleme:**
    * Eksik değerlerin stratejik olarak doldurulması (mod ve medyan/ortalama).
    * `person_income` ve diğer sayısal sütunlardaki aykırı değerlerin IQR metoduna göre kırpılması (clipping).
    * Kategorik değişkenlerin One-Hot Encoding ile sayısal formata dönüştürülmesi.
    * Sayısal özelliklerin `StandardScaler` ile ölçeklendirilmesi.
    * `loan_status` hedef değişkenindeki sınıf dengesizliğinin SMOTE (Synthetic Minority Over-sampling Technique) ile giderilmesi.
4.  **Model Seçimi ve Eğitimi:**
    * Veri setinin eğitim ve test setlerine ayrılması.
    * Aşağıdaki sınıflandırma algoritmalarının kullanılması:
        * Lojistik Regresyon (Logistic Regression)
        * K-En Yakın Komşu (KNeighborsClassifier)
        * Karar Ağaçları (DecisionTreeClassifier)
        * Rastgele Orman (RandomForestClassifier)
        * Gradient Boosting (GradientBoostingClassifier)
        * XGBoost (XGBClassifier)
    * Modellerin K-Fold Çapraz Doğrulama ile eğitilmesi ve performanslarının değerlendirilmesi.
5.  **Model Değerlendirme:**
    * Her model için F1 Skoru'nun hesaplanması ve sınıflandırma raporlarının incelenmesi.
    * Modellerin ROC eğrileri ve AUC değerlerinin karşılaştırılması.
    * En iyi performans gösteren modelin belirlenmesi.

## ✨ Kullanılan Teknolojiler

* `Python`
* `Pandas`: Veri manipülasyonu ve analizi için.
* `NumPy`: Sayısal işlemler için.
* `Scikit-learn`: Makine öğrenimi algoritmaları ve önişleme araçları için.
* `Matplotlib`: Veri görselleştirmesi için.
* `Seaborn`: Gelişmiş veri görselleştirmesi için.
* `XGBoost`: Güçlü gradient boosting modeli için.
* `imblearn`: Sınıf dengesizliği giderme (SMOTE) için.

## 🚀 Kurulum

Projeyi yerel olarak çalıştırmak için aşağıdaki adımları izleyebilirsiniz:

1.  Depoyu klonlayın:
    ```bash
    git clone [https://github.com/Servetvrll/kredi_risk_siniflandirma.git](https://github.com/Servetvrll/kredi_risk_siniflandirma.git)
    cd kredi_risk_siniflandirma
    ```
2.  Gerekli kütüphaneleri yükleyin. Aşağıdaki komutu kullanarak bir `requirements.txt` dosyası oluşturduysanız:
    ```bash
    pip install -r requirements.txt
    ```
    Eğer `requirements.txt` dosyanız yoksa, notebook'ta kullanılan ana kütüphaneleri manuel olarak yükleyebilirsiniz:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn xgboost imblearn
    ```
3.  Jupyter Notebook'u başlatın:
    ```bash
    jupyter notebook
    ```
4.  `credit_risk_analysis.ipynb` dosyasını açarak projeyi inceleyebilir ve çalıştırabilirsiniz.

## 📈 Sonuçlar

Yapılan analizler ve modellemeler sonucunda, kredi riskini tahmin etmede çeşitli makine öğrenimi modelleri test edilmiştir. Özellikle **XGBoost Classifier** ve **Random Forest Classifier** gibi ağaç tabanlı modellerin, sınıf dengesizliği olan bu veri setinde diğer modellere göre daha iyi performans gösterdiği gözlemlenmiştir.

En iyi modelin, belirlenen metrikler (örn. F1 Skoru ve ROC AUC) açısından tatmin edici sonuçlar verdiği ve kredi red oranlarını doğru bir şekilde tahmin etme potansiyeli taşıdığı görülmüştür.

*(**Not:** Bu kısmı, notebook'unuzdaki nihai model performans skorlarına göre güncelleyebilirsiniz. Örneğin: "En iyi model olan XGBoost Classifier, test setinde %XX F1 Skoru ve YY ROC AUC değeri elde etmiştir.")*

## 📧 İletişim

* **Servet Varol** - [GitHub Profilim](https://github.com/Servetvrll)
* [LinkedIn Profilim](www.linkedin.com/in/servet-varol-b35a7224b) 
