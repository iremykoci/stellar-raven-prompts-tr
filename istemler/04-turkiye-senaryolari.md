# 04 · Türkiye senaryoları

[← Ana sayfa](../README.md)

Türkiye'deki kullanıcılar için bir şey geliştiriyorsan, bu istemler yerel ihtiyaçları Stellar'ın yapı taşlarıyla eşleştirmene yardım eder.

## Önce bir deneme ortamı: TR Mock Anchor

TL ile Stellar arasında giriş ve çıkışı denemek için gerçek bir banka ya da kimlik doğrulama sağlayıcısına ihtiyacın yok. [TR Mock Anchor](https://tr-mock-anchor.fly.dev), Stellar test ağında çalışan bir TRY ⇄ USDC deneme ortamı:

- Standart kapılardan konuşur: SEP-1, SEP-10, SEP-6, SEP-12 ve SEP-38.
- Ana alan adı (home domain) `tr-mock-anchor.fly.dev`, varlık ise USDC.
- Banka havalesi ve kimlik doğrulama tarafı taklit edilir. Stellar tarafındaki ödemeler ise test ağında gerçekten gerçekleşir.
- [/explorer](https://tr-mock-anchor.fly.dev/explorer) sayfasında cüzdan kurmadan tüm akışı tarayıcıda deneyebilirsin. [/guide](https://tr-mock-anchor.fly.dev/guide) sayfası Türkçe ve İngilizce kavram rehberi içerir. [/mainnet](https://tr-mock-anchor.fly.dev/mainnet) sayfası gerçek bir köprü kuruma geçerken neyin değişeceğini anlatır.
- Yapay zekâ asistanları için [llms.txt](https://tr-mock-anchor.fly.dev/llms.txt) ve [llms-full.txt](https://tr-mock-anchor.fly.dev/llms-full.txt) dosyaları var. Bunları asistanına bağlam olarak verebilirsin.

> Bu bir deneme ortamıdır, gerçek bir finansal hizmet değildir. Test ağı adreslerini ana ağ koduna gömme.

## T1. TL ile giriş ve çıkış akışını tasarla

```
Stellar Raven'ı kullan ve köprü kurumlarla (anchor) ilgili belgelere ve SEP metinlerine dayan.
Uygulamamda kullanıcıların TL yatırıp USDC alabilmesi ve USDC'yi tekrar TL olarak bankasına çekebilmesi gerekiyor. Uygulamamın türü: [cüzdan, pazar yeri, maaş ödemesi, vb.].
Bu akış için SEP-1, SEP-10, SEP-12, SEP-38 ve SEP-6 veya SEP-24'ün sırasıyla hangi adımda devreye girdiğini anlat.
SEP-6 (programla, arayüzü ben yaparım) ile SEP-24 (arayüzü köprü kurum sunar) arasında benim durumum için hangisinin daha uygun olduğunu gerekçesiyle söyle.
Denemek için ana alan adı olarak tr-mock-anchor.fly.dev kullanacağım. Bu köprü kurumun stellar.toml dosyasında hangi alanlara bakmam gerektiğini ve akışı demo-wallet.stellar.org üzerinde nasıl deneyeceğimi adım adım yaz.
```

## T2. Köprü kurum entegrasyonunda tuzaklar

Köprü kurum entegrasyonunda en sık yapılan hatalar SEP metinlerinde pek vurgulanmaz. Bu istem onları kodundan önce yakalar.

```
Stellar Raven'ı kullan. Köprü kurum (anchor) entegrasyonu yapıyorum: [SEP-6 veya SEP-24, istemci tarafı mı sunucu tarafı mı].
Aşağıdaki tuzakların her biri için benim akışımda nasıl bir risk oluşturduğunu ve nasıl önleyeceğimi anlat, ilgili SEP bölümünü kaynak göster:
1. SEP-10 doğrulama işleminin (challenge) ağa gönderilmemesi gerektiği
2. home_domain ile web_auth_domain farkı
3. SEP-24 arayüzünün sayfa içi çerçeve (iframe) yerine açılır pencerede açılması ve postMessage ile tamamlanması
4. Ortak bir hesaba çekim yaparken memo ve memo_type alanlarının birebir gönderilmesi
5. Yatırma öncesi güven hattı (trustline) gerekliliği ve /info içindeki talep edilebilir bakiye desteği
6. Tutarların kayan noktalı sayı (float) olarak değil, metin ya da ondalık tip olarak işlenmesi
7. asset_code'un tek başına belirsiz olması, asset_issuer ile birlikte kullanılması
8. İşlem durumlarının (pending_user_transfer_start, pending_trust, on_hold vb.) her biri için kullanıcıya ne gösterileceği
9. SEP-38 fiyat teklifinin süresi dolduğunda yeniden teklif alınması
10. SEP-10 oturum anahtarının (JWT) süresi dolduğunda kullanıcıyı başa atmadan yeniden kimlik doğrulama
```

## T3. Yurt dışına para transferi

```
Stellar Raven'ı kullan.
Projem şu kullanıcıların sınır ötesi para gönderme sorununu çözmeyi hedefliyor: [kimin kime, hangi ülkeye, ayda ortalama ne kadar para gönderdiğini anlat, örneğin Almanya'daki bir işçinin Türkiye'deki ailesine gönderdiği para].
Bugünkü yöntemlerle (banka havalesi, SWIFT, döviz bürosu, para transfer uygulamaları) Stellar'ı maliyet, süre ve erişilebilirlik açısından karşılaştır.
Bu akışta yol ödemesinin (path payment), SEP-31'in ve köprü kurumların nasıl bir rol oynayacağını adım adım göster.
Karşı ülkede Stellar'a bağlı bir köprü kurum olup olmadığını ekosistem verisinden kontrol et. Bulamazsan tahmin yürütme, "bu kaynaklarda bulunamadı" de.
Yasal uyumluluk (kimlik doğrulama ve kara para aklamayla mücadele, KYC/AML) açısından dikkat etmem gereken noktaları listele ve bunun hukuki bir tavsiye olmadığını belirt.
```

## T4. Altın günü ve ortak birikim

Altın günü, kura, ortak kasa gibi dönüşümlü birikim grupları Türkiye'de çok yaygın ve güvene dayalı çalışıyor. Blokzincirin gerçekten değer katabileceği bir alan, ama doğru kurgulanırsa.

```
Stellar Raven'ı kullan.
Dönüşümlü bir birikim grubu (altın günü) uygulaması yapmak istiyorum: [kaç kişi, ne sıklıkla, hangi varlıkla (USDC, altın temelli bir token vb.), sıranın nasıl belirlendiği].
Şunları değerlendir:
1. Bu mantığı Soroban sözleşmesiyle mi kurmalıyım, yoksa talep edilebilir bakiye ve çoklu imza gibi yerleşik özellikler yeterli mi?
2. Bir üye ödemesini yapmazsa ne olur? Bu durumu sözleşme mi çözmeli, yoksa grup içi sosyal kurallar mı?
3. Paranın hiçbir aşamada benim (uygulama sahibinin) kontrolüne geçmemesi için mimari nasıl olmalı?
4. Ekosistemde bunu daha önce deneyen projeler var mı? (scout.searchHackathonBuilds ile "rotating savings" ve "ROSCA" terimlerini ara)
Sözleşme önerirsen depolama türlerini (instance, persistent, temporary) ve yaşam süresi (TTL) uzatmayı nasıl ele alacağımı da yaz.
```

## T5. Kripto bilmeyen kullanıcıya uygun deneyim

```
Projem şu: [fikrini anlat] ve hedef kitlem kripto deneyimi olmayan Türkiye'deki kullanıcılar.
Stellar Raven'ı kullanarak, kullanıcının kurtarma ifadesi (seed phrase), güven hattı, XLM rezervi gibi kavramlarla hiç karşılaşmadan uygulamamı kullanabilmesi için hangi seçeneklerim olduğunu söyle:
- Geçiş anahtarıyla (passkey) çalışan akıllı hesaplar (smart account)
- İşlem ücretinin kullanıcı yerine ödenmesi (ücret sponsorluğu, fee bump)
- Hesap açma ve güven hattı ekleme adımlarının arka planda yapılması
- Stellar Wallets Kit ile birden fazla cüzdan desteği
Her seçenek için: kullanıcı deneyimine etkisi, anahtarın kimde durduğu (kullanıcıda mı, sunucuda mı), hackathon süresinde uygulanabilirliği ve belge bağlantısı.
Anahtarı sunucuda tutan (emanetçi, custodial) bir çözüm önerirsen bunun risklerini ayrıca belirt.
```

## T6. Türkçe arayüz metinleri

```
Uygulamamın arayüzündeki şu İngilizce Stellar terimlerini, kripto bilmeyen bir Türk kullanıcının anlayacağı şekilde Türkçeye çevir: [terimleri listele, örneğin trustline, memo, claimable balance, transaction pending, insufficient balance].
Her terim için: kısa arayüz metni (düğme veya etiket için), bir cümlelik açıklama (yardım metni için) ve kaçınılması gereken yanıltıcı çeviri.
Özellikle hata mesajlarında kullanıcıyı suçlamayan, ne yapması gerektiğini söyleyen bir dil kullan.
```

[← Önceki: 03 · Ekosistem araştırması](03-ekosistem-arastirmasi.md) · [Sonraki: 05 · Güvenlik ve kod incelemesi →](05-guvenlik-ve-kod-inceleme.md)
