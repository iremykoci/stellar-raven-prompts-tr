# 03 · Ekosistem araştırması

[← Ana sayfa](../README.md)

Raven sadece dokümantasyon okumaz. Stellar ekosisteminin canlı verisine de erişir: proje dizini, önceki hackathon projeleri, SCF fonlamaları, açık RFP'ler, güvenlik denetim raporları, haberler ve konuşmalar. Bu dosyadaki prompt'lar bu veriyi kullanır.

Prompt'ların içinde Raven'ın araç adlarını (`scout.hackathonBrief` gibi) açıkça yazdık. Böylece Raven doğru aracı seçer ve cevabı tahmine değil veriye dayandırır. Araçların ne yaptığını [Raven nasıl çalışır?](../rehber/raven-nasil-calisir.md) sayfasında bulabilirsin.

> **Önemli:** Ekosistem verisi hızla değişir. Her cevapta verinin hangi tarihe ait olduğunu sor. Raven "bulamadım" diyorsa bu, o şeyin var olmadığı anlamına gelmez, sadece bu kaynaklarda bulunamadığı anlamına gelir.

## E1. Tek seferde hackathon brifi

Hackathon'un ilk saati için en verimli prompt bu.

```
Stellar Raven'ın scout.hackathonBrief aracını şu fikir için çalıştır: "[fikrini İngilizce, kısa bir ifadeyle yaz, örneğin 'rotating savings circle for friends']".
Sonucu Türkçe olarak şu başlıklarla özetle:
1. Rakipler ve olgunlukları (canlı mı, denetlenmiş mi, terk edilmiş mi)
2. Daha önce hackathon'larda yapılmış benzer projeler ve ne kazandıkları
3. Başlangıç noktası olarak inceleyebileceğim açık kaynak repolar
4. Bu alanda şu an açık olan SCF fonlaması
5. Sunumda iddia etmemem gereken şeyler (whatNotToClaim)
Her maddenin kaynağını ve tarihini yaz.
```

> **Neden İngilizce ifade?** Raven'ın ekosistem verisinin büyük kısmı İngilizce. Arama ifadesini İngilizce yazıp cevabı Türkçe istemek daha iyi sonuç verir.

## E2. Fikrimi sına

```
Stellar Raven'ın scout.vetIdea aracını "[fikrin, İngilizce kısa ifade]" için çalıştır.
Sonuca göre bana şunu söyle: Bu alan kalabalık mı, boş mu? Boşsa bunun nedeni fırsat mı, yoksa daha önce denenip başarısız olunması mı?
Rakiplerimden en güçlü üç tanesini seç ve benim fikrimin onlardan nerede ayrıştığını (ya da ayrışmadığını) dürüstçe yaz.
Hiçbir rakip çıkmazsa bunu "rakip yok" diye yorumlama. lumenloop.search_content_semantic ile bir tur daha ara.
```

## E3. Nerede boşluk var?

Henüz fikrin yoksa ya da iki fikir arasında kaldıysan:

```
Stellar Raven'ın scout.getClusters ve scout.analyzeEcosystem (dimension: "gaps") araçlarını kullan.
Stellar ekosistemindeki en kalabalık ve en boş alanları bir tablo halinde göster (küme adı, proje sayısı, kalabalık puanı, SCF fonlaması).
Sonra benim ilgi alanıma ([ilgi alanını yaz, örneğin ödemeler, DeFi, gerçek dünya varlıkları, ajan ödemeleri]) ve ekibimin yetkinliğine ([yetkinlikleri yaz]) göre en mantıklı iki boşluğu öner.
Verilerin hangi tarihe ait olduğunu belirt.
```

## E4. Bu daha önce hackathon'da yapıldı mı?

```
Stellar Raven'ın scout.searchHackathonBuilds aracını "[konu, İngilizce]" için çalıştır, önce tüm projeleri, sonra sadece kazananları (winnersOnly) getir.
Kazanan projelerin neyi iyi yaptığını, kazanamayanların nerede eksik kaldığını kısaca çıkar.
Bu projelerden hangileri hâlâ geliştiriliyor, hangileri hackathon'dan sonra bırakılmış? Bırakılanların neden bırakıldığına dair bir ipucu varsa göster.
Benim projemin bu listeden farklı olması için ne yapması gerektiğini söyle.
```

## E5. Neyi entegre etmeliyim?

Her şeyi sıfırdan yazmak yerine, ekosistemde var olan bir şeyi kullanmak çoğu zaman daha doğru.

```
Stellar Raven'ın stellar-integration-finder skill'ini kullan.
Projemde şuna ihtiyacım var: [ihtiyacı anlat, örneğin fiyat oracle'ı, DEX üzerinden takas, cüzdan bağlama, anchor, escrow, indeksleyici].
Bu ihtiyacı karşılayan en fazla üç ekosistem projesini öner. Her biri için: ne yaptığı, mainnet'te canlı olup olmadığı, denetim raporu olup olmadığı (scout.listAudits ile kontrol et), dokümantasyon bağlantısı ve entegrasyonun zorluğu.
Denetim bilgisi bulunamazsa "denetlenmemiş" deme, "kayıtlarda denetim bulunamadı" de.
```

## E6. Bir projenin dosyasını çıkar

Rakibini ya da ortak olmayı düşündüğün bir projeyi yakından tanımak için:

```
Stellar Raven'ın stellar-project-dossier skill'ini "[proje adı]" için kullan.
Projenin ne yaptığını, ekibini, SCF geçmişini, katıldığı etkinlikleri, hakkında yapılmış konuşmaları ve benzer projeleri özetle.
Bulduğun her bilginin kaynağını ve tarihini yaz. Proje adıyla birebir eşleşmeyen sonuçları bu projeye aitmiş gibi gösterme.
```

## E7. Son gelişmeler

```
Stellar Raven'ın stellar-ecosystem-digest skill'ini "[tema veya proje adı, İngilizce]" için son [30/60/90] günü kapsayacak şekilde çalıştır.
Haberleri, konuşmaları, etkinlikleri ve araştırmaları tarih sırasıyla, her biri için tek cümlelik Türkçe özet ve bağlantıyla listele.
Bu gelişmelerden projemi ([fikrini anlat]) doğrudan etkileyebilecek olanları işaretle.
```

## E8. Ekosistem ne istiyor?

```
Stellar Raven'ın scout.getRfps aracıyla şu an açık olan RFP'leri (SCF tarafından fonlanan talepleri) listele.
Her birinin kategorisini, ne istediğini ve teknik gereksinimlerini kısaca yaz.
Şu anki SCF turunun başvuru penceresinin açık olup olmadığını meta.scfRound bilgisinden kontrol et ve tarihini belirt.
Bu RFP'lerden hangisi benim ekibime ([ekibini ve yetkinliklerini anlat]) gerçekçi olarak uyar? Hiçbiri uymuyorsa bunu açıkça söyle.
```

[← Önceki: 02 · Stellar'ı doğru kullanmak](02-stellar-teknoloji.md) · [Sonraki: 04 · Türkiye senaryoları →](04-turkiye-senaryolari.md)
