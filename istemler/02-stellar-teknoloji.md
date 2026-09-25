# 02 · Stellar'ı doğru kullanmak

[← Ana sayfa](../README.md)

Bu prompt'lar, Stellar'ın çözümüne doğru şekilde oturduğunu ve doğru yapı taşlarını seçtiğini kontrol etmene yardım ediyor. Hepsi Raven'dan resmi dokümantasyona (stellarDocs) dayanmasını istiyor.

## B1. Doğru teknik uyumu bul

```
Stellar Raven'ı kullan ve resmi Stellar dokümantasyonuna dayan.
Projem şu: [fikrini anlat] ve Stellar üzerinde yapmak istediğim şey şu: [işlevi anlat].
Hangi Stellar özelliğinin en iyi uyduğunu söyle (örneğin ödemeler, varlık çıkarma, path payment, SDEX, claimable balance, anchor'lar ya da Soroban akıllı kontratları).
Önerini gerekçelendir ve dayandığın dokümantasyon sayfasının bağlantısını ver.
```

## B2. Geçerli standartları (SEP) belirle

```
Stellar Raven'ı kullanarak ekosistem standartlarını (SEP) incele.
Projemin ihtiyacı şu: [ihtiyacı anlat, örneğin yerel parayla bağlantı kurmak, kullanıcı doğrulamak veya token çıkarmak].
Benim durumum için hangi SEP'lerin geçerli olduğunu, her birinin ne işe yaradığını ve hangi sırayla incelemem gerektiğini söyle.
Her SEP için stellar-protocol reposundaki bağlantıyı ver ve durumunun (Draft, Active, Final) güncel olup olmadığını kontrol et.
Var olmayan ya da işime yaramayan bir SEP'ten bahsedersem beni düzelt.
```

> **İpucu:** Sık karşılaşılan eşleşmeler şöyle. Token için SEP-41, kullanıcı doğrulama için SEP-10, anchor keşfi için SEP-1, programatik yatırma-çekme için SEP-6, arayüzlü yatırma-çekme için SEP-24, KYC için SEP-12, fiyat teklifi için SEP-38, sınır ötesi ödeme için SEP-31. Yine de Raven'a doğrulat, standartlar değişebiliyor.

## B3. Soroban mı, klasik Stellar mı?

```
Mimariye karar vermeme yardım et.
Projemin ana mantığı şu: [ana mantığı anlat].
Stellar dokümantasyonuna dayanarak bunu klasik Stellar işlemleriyle mi çözmem gerektiğini, yoksa Soroban akıllı kontratlarına mı ihtiyacım olduğunu söyle.
Özellikle şunu kontrol et: Yazmayı düşündüğüm kontrat, Stellar'da zaten yerleşik olarak bulunan bir şeyi mi yeniden icat ediyor? (claimable balance, çoklu imza, varlık yetkilendirme bayrakları, SAC, SEP-24 gibi)
Zamanı kısıtlı bir hackathon ekibi için iki yolun avantajlarını ve maliyetlerini açıkla.
```

## B4. Minimum mimariyi tasarla

```
Stellar Raven'ı kullanarak bana minimum bir mimari çıkar.
Projem şu: [fikrini anlat]. Kullandığım dil ve çatı: [örneğin Next.js + TypeScript, Rust].
Bir prototip için gereken parçaları listele (testnet, uygun SDK, Stellar RPC veya Horizon, Freighter ya da Stellar Wallets Kit gibi bir cüzdan, varsa Soroban kontratı) ve her birini tek cümleyle anlat.
Horizon ile RPC arasında seçim yapmam gerekiyorsa hangisini neden önerdiğini söyle.
İlk çalışan versiyona ulaşmak için adımları sırasıyla yazarak bitir.
```

## B5. Hackathon süresinde yapılabilir mi?

```
Kalan süreme göre gerçekçi bir plan istiyorum.
Projem şu: [fikrini anlat], ekibim [kişi sayısı ve yetkinlikleri] ve elimde [kalan saati veya günü yaz] var.
Bu sürede Stellar üzerinde gerçekten hangi kısmı inşa edebileceğimi, hangi kısmı ise sadece fikir olarak sunmamın daha doğru olacağını söyle.
Canlı demo yapılabilecek minimum bir kapsam öner ve demoda neyin gerçek (testnet üzerinde), neyin taklit (mock) olacağını açıkça ayır.
```

## B6. Sık yapılan hatalardan kaçın

```
Stellar Raven'ı kullanarak iyi uygulamaları gözden geçir.
Stellar'daki teknik yaklaşımım şu: [Stellar'ı nasıl kullanmayı planladığını anlat].
Kaçınmam gereken yaygın hataları, yaklaşımımda gördüğün kötü uygulamaları ve bunları nasıl düzelteceğimi söyle; uygun olan yerlerde dokümantasyonu kaynak göster.
Özellikle şunlara bak: trustline eksikliği, 7 ondalık hassasiyetin float ile bozulması, memo gerektiren ödemeler, hesabın minimum bakiye (reserve) gereksinimi, testnet ve mainnet adreslerinin karışması.
```

## B7. Varlığımı tasarla

Token ya da stablecoin çıkaracaksan:

```
Stellar Raven'ı kullan ve varlık (asset) dokümantasyonuna dayan.
Çıkarmak istediğim varlık şu: [ne temsil ettiğini, kimin çıkaracağını ve kimlerin tutacağını anlat].
Bunu klasik bir Stellar varlığı olarak mı çıkarmalıyım, yoksa özel bir Soroban tokenı mı yazmalıyım? SAC (Stellar Asset Contract) bu ikisini nasıl birleştiriyor?
Hangi yetkilendirme bayraklarını (AUTH_REQUIRED, AUTH_REVOCABLE, AUTH_CLAWBACK_ENABLED) açmam gerektiğini ve bunun kullanıcıya etkisini açıkla.
Düzenlemeye tabi bir varlıksa SEP-8 veya SEP-57'nin işime yarayıp yaramayacağını söyle.
```

[← Önceki: 01 · Problem doğrulama](01-problem-dogrulama.md) · [Sonraki: 03 · Ekosistem araştırması →](03-ekosistem-arastirmasi.md)
