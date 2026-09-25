# 05 · Güvenlik ve kod incelemesi

[← Ana sayfa](../README.md)

Soroban, Ethereum'un sözleşme dili Solidity'ye benzemez. Ethereum'daki bazı klasik hataları tasarım gereği önler (başka sözleşmenin kodunu kendi bağlamında çalıştırma yok, klasik yeniden giriş (reentrancy) saldırısı yok, yetkilendirme açıktır). Ama kendi hata türlerini getirir. Bunların en önemlisi, Ethereum'da karşılığı olmayan **depolama türleri ve yaşam süresi (TTL, arşivlenme)** konusudur.

Bu dosyadaki istemler Raven'daki resmi güvenlik rehberine ve `soroban-common-mistakes` becerisinin kontrol listesine dayanır. Hiçbiri profesyonel bir denetimin yerini tutmaz.

## G1. Sözleşmemi incele

Sözleşme kodunu istemin altına yapıştır.

```
Stellar Raven'ı kullan ve Soroban güvenlik belgelerine dayan.
Aşağıdaki Soroban sözleşmesini şu beş kategoriye göre incele ve sadece gerçekten var olan sorunları raporla:
1. Yetkilendirme: Para hareketi veya yönetici değişikliği yapan her fonksiyonda require_auth() var mı, doğru adres için mi çağrılıyor, başlatma fonksiyonu (initialize/__constructor) iki kez çalışabilir mi?
2. Depolama ve yaşam süresi: Büyüyen veya kullanıcıya özel veri instance depolamada mı duruyor, önemli persistent veri için extend_ttl var mı, kalıcı olması gereken veri temporary depolamada mı, anahtarlar tipli bir enum mu?
3. Matematik ve mantık: Taşmaya karşı kontrolsüz aritmetik (checked_add vb. yok mu), bölmeden sonra çarpma, yuvarlama yönü, negatif veya sıfır tutar kontrolü, birikmesi gereken değerin üzerine yazılması, çekimden sonra bakiyenin düşülmemesi
4. Dış çağrılar: Parametre olarak alınan bir sözleşme adresi doğrulanmadan çağrılıyor mu, fiyat verisi sağlayıcısından (oracle) gelen değerler kontrol ediliyor mu, geri alma (clawback) veya dondurulmuş güven hattı hesaba katılmış mı, fiyat kaymasına (slippage) karşı en az çıkış tutarı (min_out) ve son tarih var mı?
5. Kod kalitesi: panic! yerine #[contracterror] kullanımı, güvensiz unwrap(), olay (event) yayınlamayan durum değişiklikleri, test eksikliği, kodda gizli anahtar (S... ile başlayan), sürümü sabitlenmemiş soroban-sdk, sınırsız döngüler

Bulguları Kritik, Uyarı ve Bilgi başlıkları altında tablo halinde ver (kural, konum, bulgu, düzeltme). Her düzeltme somut kod önerisi içersin.

[sözleşme kodunu buraya yapıştır]
```

## G2. Depolama ve yaşam süresi tasarımı

Soroban'a yeni başlayanların en çok zorlandığı konu.

```
Stellar Raven'ı kullan ve Soroban depolama belgelerine dayan.
Sözleşmemde şu verileri tutacağım: [verileri listele, örneğin yönetici adresi, kullanıcı bakiyeleri, grup üyeleri listesi, tek kullanımlık numaralar (nonce)].
Her veri için instance, persistent ve temporary depolamadan hangisini seçmem gerektiğini, nedeniyle birlikte bir tabloda göster.
Arşivlenme nedir, arşivlenmiş bir veriye erişmeye çalışınca ne olur ve yaşam süresini (TTL) ne zaman, ne kadar uzatmalıyım?
Sınırsız büyüyebilecek bir liste varsa bunu nasıl parçalamam gerektiğini göster.
```

## G3. Demo öncesi hızlı güvenlik turu

Son saatlerde, demodan önce:

```
Demoya [kalan süreyi yaz] kaldı. Projemin yapısı şu: [sözleşmeler, ön yüz, arka uç, anahtar yönetimi].
Canlı demo sırasında veya kod deposu herkese açıldığında beni utandırabilecek güvenlik sorunlarını öncelik sırasıyla listele:
- Kod deposunda veya ön yüz kodunda gizli anahtar, API anahtarı ya da .env dosyası var mı?
- Kullanıcı anahtarları sunucuda saklanıyor mu (şifreli bile olsa)?
- Test ağı ile ana ağ ayarları karışabilir mi?
- Herkesin çağırabileceği ama çağırmaması gereken bir sözleşme fonksiyonu var mı?
Her madde için 10 dakikada yapılabilecek bir düzeltme öner.
```

## G4. Bu protokol denetlenmiş mi?

Entegre ettiğin bir protokolün güvenlik geçmişine bakmak için:

```
Stellar Raven'ın scout.listAudits aracıyla "[protokol adı]" için yayımlanmış güvenlik denetim raporlarını getir.
Her rapor için: denetimi yapan firma, yayımlanma tarihi, bulgu sayısı ve rapor bağlantısı.
Bulgu sayısı boş gelirse bunu "sıfır bulgu" diye yorumlama, "bulgu sayısı çıkarılmamış" de. Hiç rapor bulunamazsa "denetlenmemiş" deme, "kayıtlarda denetim bulunamadı" de.
Sözleşmemin bu protokolle etkileşen kısmında dikkat etmem gereken bir bulgu varsa işaretle.
```

## G5. Otomatik araçlar

```
Stellar Raven'ı kullan.
Soroban sözleşmem için kullanabileceğim otomatik güvenlik araçlarını (durağan analiz, rastgele girdiyle test (fuzzing), biçimsel doğrulama) listele.
Her biri için ne yaptığını, nasıl kurulacağını ve sürekli entegrasyona (CI) nasıl ekleneceğini kısaca anlat.
Hackathon süresinde en az emekle en çok fayda sağlayacak olanı öner.
```

> **İpucu:** Bu listenin başında genellikle CoinFabrik'in Scout aracı çıkar (`cargo install cargo-scout-audit`, ardından `cargo scout-audit`). Hackathon süresinde bile kurulup çalıştırılabilecek kadar hafiftir.

## Demo öncesi kontrol listesi

- [ ] Kod deposunda `S...` ile başlayan hiçbir gizli anahtar yok, `.env` dosyası `.gitignore` içinde.
- [ ] Para hareket ettiren her fonksiyon `require_auth()` çağırıyor.
- [ ] Başlatma fonksiyonu iki kez çalıştırılamıyor.
- [ ] Kullanıcıya özel veriler persistent depolamada ve yaşam süreleri uzatılıyor.
- [ ] Tutarlar için `checked_*` aritmetik kullanılıyor, `overflow-checks = true` açık.
- [ ] Önemli durum değişiklikleri olay (event) yayınlıyor.
- [ ] En azından yetkilendirme ve aritmetik yolları için test var.
- [ ] Kullanıcı anahtarları sunucuda tutulmuyor.

[← Önceki: 04 · Türkiye senaryoları](04-turkiye-senaryolari.md) · [Sonraki: 06 · İleri konular →](06-ileri-konular.md)
