# 05 · Güvenlik ve kod incelemesi

[← Ana sayfa](../README.md)

Soroban, Solidity değildir. Ethereum'daki bazı klasik hataları tasarım gereği önler (delegatecall yok, klasik reentrancy yok, yetkilendirme açıktır). Ama kendi hata türlerini getirir. Bunların en önemlisi, Ethereum'da karşılığı olmayan **depolama türleri ve TTL (arşivlenme)** konusudur.

Bu dosyadaki prompt'lar Raven'daki resmi güvenlik rehberine ve `soroban-common-mistakes` skill'inin kontrol listesine dayanır. Hiçbiri profesyonel bir denetimin yerini tutmaz.

## G1. Kontratımı incele

Kontrat kodunu prompt'un altına yapıştır.

```
Stellar Raven'ı kullan ve Soroban güvenlik dokümantasyonuna dayan.
Aşağıdaki Soroban kontratını şu beş kategoriye göre incele ve sadece gerçekten var olan sorunları raporla:
1. Yetkilendirme: fon hareketi veya yönetici değişikliği yapan her fonksiyonda require_auth() var mı, doğru adres için mi çağrılıyor, initialize/__constructor iki kez çalışabilir mi?
2. Depolama ve TTL: büyüyen veya kullanıcıya özel veri instance depolamada mı duruyor, kritik persistent veri için extend_ttl var mı, kalıcı olması gereken veri temporary'de mi, anahtarlar tipli bir enum mu?
3. Matematik ve mantık: kontrolsüz aritmetik (checked_add vb. yok mu), bölmeden sonra çarpma, yuvarlama yönü, negatif veya sıfır tutar kontrolü, birikmesi gereken değerin üzerine yazılması, çekimden sonra bakiyenin düşülmemesi
4. Dış çağrılar: parametre olarak alınan bir kontrat adresi doğrulanmadan çağrılıyor mu, oracle dönüşleri kontrol ediliyor mu, clawback veya donmuş trustline hesaba katılmış mı, kaymaya (slippage) karşı min_out ve son tarih var mı?
5. Kod kalitesi: panic! yerine #[contracterror], güvensiz unwrap(), olay (event) yayınlanmayan durum değişiklikleri, test eksikliği, kodda gizli anahtar (S... ile başlayan), sabitlenmemiş soroban-sdk sürümü, sınırsız döngüler

Bulguları Kritik, Uyarı ve Bilgi başlıkları altında tablo halinde ver (kural, konum, bulgu, düzeltme). Her düzeltme somut kod önerisi içersin.

[kontrat kodunu buraya yapıştır]
```

## G2. Depolama ve TTL tasarımı

Soroban'a yeni başlayanların en çok zorlandığı konu.

```
Stellar Raven'ı kullan ve Soroban depolama dokümantasyonuna dayan.
Kontratımda şu verileri tutacağım: [verileri listele, örneğin yönetici adresi, kullanıcı bakiyeleri, grup üyeleri listesi, tek kullanımlık nonce'lar].
Her veri için instance, persistent ve temporary depolamadan hangisini seçmem gerektiğini, nedeniyle birlikte bir tabloda göster.
Arşivlenme (archival) nedir, arşivlenmiş bir veriye erişmeye çalışınca ne olur ve TTL'i ne zaman, ne kadar uzatmalıyım?
Sınırsız büyüyebilecek bir liste varsa bunu nasıl parçalamam gerektiğini göster.
```

## G3. Demo öncesi hızlı güvenlik turu

Son saatlerde, demo'dan önce:

```
Demo'ya [kalan süreyi yaz] kaldı. Projemin yapısı şu: [kontratlar, frontend, backend, anahtar yönetimi].
Canlı demo sırasında veya repom herkese açıldığında beni utandırabilecek güvenlik sorunlarını öncelik sırasıyla listele:
- Repoda veya frontend kodunda gizli anahtar, API anahtarı ya da .env dosyası var mı?
- Kullanıcı anahtarları sunucuda saklanıyor mu (şifreli bile olsa)?
- Testnet ile mainnet ayarları karışabilir mi?
- Herkesin çağırabileceği ve çağırmaması gereken bir kontrat fonksiyonu var mı?
Her madde için 10 dakikada yapılabilecek bir düzeltme öner.
```

## G4. Bu protokol denetlenmiş mi?

Entegre ettiğin bir protokolün güvenlik geçmişine bakmak için:

```
Stellar Raven'ın scout.listAudits aracıyla "[protokol adı]" için yayımlanmış güvenlik denetim raporlarını getir.
Her rapor için: denetimi yapan firma, yayımlanma tarihi, bulgu sayısı ve rapor bağlantısı.
Bulgu sayısı boş gelirse bunu "sıfır bulgu" diye yorumlama, "çıkarılmamış" de. Hiç rapor bulunamazsa "denetlenmemiş" deme, "kayıtlarda denetim bulunamadı" de.
Kontratımın bu protokolle etkileşen kısmında dikkat etmem gereken bir bulgu varsa işaretle.
```

## G5. Otomatik araçlar

```
Stellar Raven'ı kullan.
Soroban kontratım için kullanabileceğim otomatik güvenlik araçlarını (statik analiz, fuzzing, formal doğrulama) listele.
Her biri için ne yaptığını, nasıl kurulacağını ve CI'a nasıl ekleneceğini kısaca anlat.
Hackathon süresinde en az emekle en çok fayda sağlayacak olanı öner.
```

> **İpucu:** Bu listenin başında genellikle CoinFabrik'in Scout aracı çıkar (`cargo install cargo-scout-audit`, ardından `cargo scout-audit`). Hackathon süresinde bile kurulup çalıştırılabilecek kadar hafiftir.

## Demo öncesi kontrol listesi

- [ ] Repoda `S...` ile başlayan hiçbir gizli anahtar yok, `.env` dosyası `.gitignore` içinde.
- [ ] Fon hareket ettiren her fonksiyon `require_auth()` çağırıyor.
- [ ] Başlatma fonksiyonu iki kez çalıştırılamıyor.
- [ ] Kullanıcıya özel veriler persistent depolamada ve TTL uzatılıyor.
- [ ] Tutarlar için `checked_*` aritmetik kullanılıyor, `overflow-checks = true` açık.
- [ ] Önemli durum değişiklikleri olay (event) yayınlıyor.
- [ ] En az yetkilendirme ve aritmetik yolları için test var.
- [ ] Kullanıcı anahtarları sunucuda tutulmuyor.

[← Önceki: 04 · Türkiye senaryoları](04-turkiye-senaryolari.md) · [Sonraki: 06 · İleri konular →](06-ileri-konular.md)
