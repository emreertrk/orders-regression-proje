## Siparişler - Çok Değişkenli Doğrusal Regresyon

`orders` veri setinin hızlı analizi, `review_score`'un `wait_time` ve `delay_vs_expected` gibi özelliklerle çoğunlukla ilişkili olduğunu göstermiştir.

Ancak, bu iki özellik de birbirleriyle yüksek oranda ilişkiliydi.

Bu alıştırmada, bir özelliğin etkisini belirlemek için `statsmodels` kullanacağız, **diğerini sabit tutarak**

`orders_regression.ipynb` dosyasını açın ve talimatları izleyin

## Çalışma Notları

Bu proje, Olist sipariş verisinde teslimat sürelerinin (`wait_time`, `delay_vs_expected`) müşteri puanı (`review_score`) üzerindeki etkisini `statsmodels` ile tek değişkenli, çok değişkenli ve standardize edilmiş OLS modelleriyle inceler. Şablon yönerge notebook'u yerine kendi notebook'um (`Orders-Regression-OLS.ipynb`) kullanıldı. Özellikler önceki ünitedeki `olist` paketi yerine doğrudan notebook içinde hesaplandı.

1. Ortam: `workintech` sanal ortamı. Proje klasöründe `pyenv local workintech` ile etkinleştirilir. `statsmodels` ve `seaborn` yoksa `pip install statsmodels seaborn` ile kurulur.
2. Olist veri setinin 6 CSV dosyasını (`olist_orders`, `olist_order_items`, `olist_order_reviews`, `olist_customers`, `olist_sellers`, `olist_geolocation`) `data/` klasörüne koy. CSV dosyaları `.gitignore` içindedir, repoda yoktur.
3. `jupyter notebook` ile notebook'u aç ve hücreleri sırayla çalıştır. Tüm notebook birkaç saniyede çalışır.

Özet: 95.870 teslim edilmiş sipariş kullanıldı. Tek başına her ek bekleme günü puanı 0.045, her ek gecikme günü 0.075 düşürüyor. İkisi birlikte modellendiğinde etkiler -0.038 (bekleme) ve -0.021 (gecikme) oluyor, ikisi de p < 0.001. R² en fazla 0.145, teslimat süreleri puan varyansının küçük bir kısmını açıklıyor. Kalıntılar puanın 1-5 arasında kesikli olması yüzünden normal dağılmıyor. Alternatif olarak denenen lojistik regresyonda gecikme, 1-2 yıldız alma riskini gün başına bekleme süresinden daha fazla artırıyor. Ayrıntılar ve sınırlılıklar notebook'un sonuç bölümünde.
