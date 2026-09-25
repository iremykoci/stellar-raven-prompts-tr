# 02 · Stellar'ı doğru kullanmak

[← Ana sayfa](../README.md)

Bu istemler, Stellar'ın çözümüne doğru şekilde oturduğunu ve doğru yapı taşlarını seçtiğini kontrol etmene yardım ediyor. Hepsi Raven'dan resmi Stellar belgelerine (stellarDocs) dayanmasını istiyor.

## B1. Doğru teknik uyumu bul

```
Stellar Raven'ı kullan ve resmi Stellar belgelerine dayan.
Projem şu: [fikrini anlat] ve Stellar üzerinde yapmak istediğim şey şu: [işlevi anlat].
Hangi Stellar özelliğinin en iyi uyduğunu söyle (örneğin ödemeler, varlık çıkarma, yol ödemesi (path payment), Stellar'ın yerleşik borsası (SDEX), talep edilebilir bakiye (claimable balance), köprü kurumlar (anchor) ya da Soroban akıllı sözleşmeleri).
Önerini gerekçelendir ve dayandığın belge sayfasının bağlantısını ver.
```

## B2. Geçerli standartları (SEP) belirle

```
Stellar Raven'ı kullanarak ekosistem standartlarını (SEP) incele.
Projemin ihtiyacı şu: [ihtiyacı anlat, örneğin yerel parayla bağlantı kurmak, kullanıcı doğrulamak veya token çıkarmak].
Benim durumum için hangi SEP'lerin geçerli olduğunu, her birinin ne işe yaradığını ve hangi sırayla incelemem gerektiğini söyle.
Her SEP için stellar-protocol deposundaki bağlantıyı ver ve durumunun (Taslak/Draft, Etkin/Active, Nihai/Final) güncel olup olmadığını kontrol et.
Var olmayan ya da işime yaramayan bir SEP'ten bahsedersem beni düzelt.
```

> **İpucu:** Sık karşılaşılan eşleşmeler şöyle. Token için SEP-41, kullanıcı doğrulama için SEP-10, köprü kurumu bulmak için SEP-1, programla yatırma-çekme için SEP-6, arayüzlü yatırma-çekme için SEP-24, kimlik doğrulama (KYC) için SEP-12, fiyat teklifi için SEP-38, sınır ötesi ödeme için SEP-31. Yine de Raven'a doğrulat, standartlar değişebiliyor.

## B3. Soroban mı, klasik Stellar mı?

```
Mimariye karar vermeme yardım et.
Projemin ana mantığı şu: [ana mantığı anlat].
Stellar belgelerine dayanarak bunu klasik Stellar işlemleriyle mi çözmem gerektiğini, yoksa Soroban akıllı sözleşmelerine mi ihtiyacım olduğunu söyle.
Özellikle şunu kontrol et: Yazmayı düşündüğüm sözleşme, Stellar'da zaten yerleşik olarak bulunan bir şeyi mi yeniden icat ediyor? (talep edilebilir bakiye, çoklu imza, varlık yetkilendirme bayrakları, Stellar Varlık Sözleşmesi (SAC), SEP-24 gibi)
Zamanı kısıtlı bir hackathon ekibi için iki yolun avantajlarını ve maliyetlerini açıkla.
```

## B4. En küçük mimariyi tasarla

```
Stellar Raven'ı kullanarak bana en küçük (minimum) bir mimari çıkar.
Projem şu: [fikrini anlat]. Kullandığım dil ve çatı: [örneğin Next.js + TypeScript, Rust].
Bir ilk sürüm (prototip) için gereken parçaları listele (test ağı, uygun yazılım geliştirme kiti (SDK), Stellar RPC veya Horizon, Freighter ya da Stellar Wallets Kit gibi bir cüzdan, varsa Soroban sözleşmesi) ve her birini tek cümleyle anlat.
Horizon ile RPC arasında seçim yapmam gerekiyorsa hangisini neden önerdiğini söyle.
İlk çalışan sürüme ulaşmak için adımları sırasıyla yazarak bitir.
```

## B5. Hackathon süresinde yapılabilir mi?

```
Kalan süreme göre gerçekçi bir plan istiyorum.
Projem şu: [fikrini anlat], ekibim [kişi sayısı ve yetkinlikleri] ve elimde [kalan saati veya günü yaz] var.
Bu sürede Stellar üzerinde gerçekten hangi kısmı yapabileceğimi, hangi kısmı ise sadece fikir olarak sunmamın daha doğru olacağını söyle.
Canlı gösterilebilecek en küçük bir kapsam öner ve gösterimde neyin gerçek (test ağında çalışan), neyin taklit olacağını açıkça ayır.
```

## B6. Sık yapılan hatalardan kaçın

```
Stellar Raven'ı kullanarak iyi uygulamaları gözden geçir.
Stellar'daki teknik yaklaşımım şu: [Stellar'ı nasıl kullanmayı planladığını anlat].
Kaçınmam gereken yaygın hataları, yaklaşımımda gördüğün kötü uygulamaları ve bunları nasıl düzelteceğimi söyle; uygun olan yerlerde belgeleri kaynak göster.
Özellikle şunlara bak: güven hattı (trustline) eksikliği, 7 ondalık hassasiyetin kayan noktalı sayılarla (float) bozulması, not (memo) gerektiren ödemeler, hesabın en az bakiye (rezerv) gereksinimi, test ağı ve ana ağ adreslerinin karışması.
```

## B7. Varlığımı tasarla

Token ya da sabit değerli bir kripto para (stablecoin) çıkaracaksan:

```
Stellar Raven'ı kullan ve varlık (asset) belgelerine dayan.
Çıkarmak istediğim varlık şu: [ne temsil ettiğini, kimin çıkaracağını ve kimlerin tutacağını anlat].
Bunu klasik bir Stellar varlığı olarak mı çıkarmalıyım, yoksa özel bir Soroban tokenı mı yazmalıyım? Stellar Varlık Sözleşmesi (SAC) bu ikisini nasıl birleştiriyor?
Hangi yetkilendirme bayraklarını (AUTH_REQUIRED, AUTH_REVOCABLE, AUTH_CLAWBACK_ENABLED) açmam gerektiğini ve bunun kullanıcıya etkisini açıkla.
Düzenlemeye tabi bir varlıksa SEP-8 veya SEP-57'nin işime yarayıp yaramayacağını söyle.
```

[← Önceki: 01 · Problem doğrulama](01-problem-dogrulama.md) · [Sonraki: 03 · Ekosistem araştırması →](03-ekosistem-arastirmasi.md)
