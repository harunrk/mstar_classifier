Bu projede, MSTAR veri setindeki 4 sınıf üzerinde görüntü işleme filtrelerini inceleyip bu veri seti için bir sınıflandırma modeli oluşturdum. Amacım, havadan çekilmiş askeri araçların Yapay Açıklıklı Radar (SAR) görüntülerine uygulanan filtrelerin, bu görüntüler üzerinde eğitilen sınıflandırma modelinin performansına etkisini gözlemlemek. Hem filtreli hem de filtresiz görüntülerle yapılan eğitim sonuçlarını karşılaştırarak, filtrelerin model performansına olan etkisini analiz etmeye çalıştım.

MSTAR veri setini [buradan](https://www.kaggle.com/datasets/atreyamajumdar/mstar-dataset-8-classes) indirdikten sonra, Python yardımıyla kopya olan fotoğrafları temizledim. Veri setinden 4 sınıf seçerek projede kullanmak üzere ayırdım. Bu seçilen sınıflardaki fotoğraflara EAW (Edge-Aware Wavelet), Lee, BM3D (Block-Matching and 3D Filtering) ve Median filtrelerini uyguladım. Filtrelerin parametreleriyle oynayarak en optimum sonuçları bulmaya çalıştım.

Filtrelerin sonuçlarını karşılaştırdım (GÖRSEL1). En iyi sonuçları Medyan ve BM3D filtreleri verdi. Bu filtrelerin üzerine, nesnelerin kenarlarını daha belirgin hale getirmek için keskinleştirme filtresi uyguladım. Keskinleştirme filtresi uyguladığımda benek gürültüsünün arttığını gözlemledim, ancak kenarların daha belirginleştiğini gördüm (GÖRSEL2). Bu işlemleri yaparken yazdığım Python kodlarına filterin.zip klasörü üzerinden ulaşabilirsiniz.

Görüntü işleme adımlarından sonra LeNet-5 mimarisine benzer bir model oluşturdum ve görsellerin önişlemesini sağlamak için uygun kodu yazdım. Modelimi ilk olarak filtre uygulanmamış görüntüler ile eğittim ve doğruluk oranını karmaşıklık matrisi ile test ettim. Daha sonra aynı işlemleri BM3D+Keskinleştirme ve Median+Keskinleştirme filtreleri uygulanmış görüntüler ile de gerçekleştirdim.

50 epoch ve 32 batch size kullanarak eğittiğim üç modelin karmaşıklık matrisleri ve doğruluk oranları aşağıdaki gibidir:

   Filtre uygulanmamış görseller ile oluşturulan model
   (GÖRSEL3)

   Median+Keskinleştirme filtresi uygulanmış görseller ile oluşturulan model
   (GÖRSEL3)

   BM3D+Keskinleştirme filtresi uygulanmış görseller ile oluşturulan model
   (GÖRSEL3)
