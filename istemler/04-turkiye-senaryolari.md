# 04 · Türkiye senaryoları

[← Ana sayfa](../README.md)

Türkiye'deki kullanıcılar için bir şey geliştiriyorsan, bu prompt'lar yerel ihtiyaçları Stellar'ın yapı taşlarıyla eşleştirmene yardım eder.

## Önce bir test ortamı: TR Mock Anchor

TL ile Stellar arasında giriş ve çıkışı denemek için gerçek bir banka ya da KYC sağlayıcısına ihtiyacın yok. [TR Mock Anchor](https://tr-mock-anchor.fly.dev), Stellar testnet üzerinde çalışan bir TRY ⇄ USDC kum havuzu:

- Standart kapılardan konuşur: SEP-1, SEP-10, SEP-6, SEP-12 ve SEP-38.
- Home domain değeri `tr-mock-anchor.fly.dev`, varlık ise USDC.
- Banka havalesi ve KYC tarafı taklit edilir. Stellar tarafındaki ödemeler ise gerçek testnet işlemleridir.
- [/explorer](https://tr-mock-anchor.fly.dev/explorer) sayfasında cüzdan kurmadan tüm akışı tarayıcıda deneyebilirsin. [/guide](https://tr-mock-anchor.fly.dev/guide) sayfası Türkçe ve İngilizce kavram rehberi içerir. [/mainnet](https://tr-mock-anchor.fly.dev/mainnet) sayfası gerçek bir anchor'a geçerken neyin değişeceğini anlatır.
- Yapay zekâ asistanları için [llms.txt](https://tr-mock-anchor.fly.dev/llms.txt) ve [llms-full.txt](https://tr-mock-anchor.fly.dev/llms-full.txt) dosyaları var. Bunları asistanına bağlam olarak verebilirsin.

> Bu bir kum havuzudur, gerçek bir finansal hizmet değildir. Testnet adreslerini mainnet koduna gömme.

## T1. TL ile giriş ve çıkış akışını tasarla

```
Stellar Raven'ı kullan ve anchor dokümantasyonuna ve SEP metinlerine dayan.
Uygulamamda kullanıcıların TL yatırıp USDC alabilmesi ve USDC'yi tekrar TL olarak bankasına çekebilmesi gerekiyor. Uygulamamın türü: [cüzdan, pazar yeri, maaş ödemesi, vb.].
Bu akış için SEP-1, SEP-10, SEP-12, SEP-38 ve SEP-6 veya SEP-24'ün sırasıyla hangi adımda devreye girdiğini anlat.
SEP-6 (programatik, arayüzü ben yaparım) ile SEP-24 (arayüzü anchor sunar) arasında benim durumum için hangisinin daha uygun olduğunu gerekçesiyle söyle.
Test için home domain olarak tr-mock-anchor.fly.dev kullanacağım. Bu anchor'ın stellar.toml dosyasında hangi alanlara bakmam gerektiğini ve akışı demo-wallet.stellar.org üzerinde nasıl deneyeceğimi adım adım yaz.
```

## T2. Anchor entegrasyonunda tuzaklar

Anchor entegrasyonunda en sık yapılan hatalar SEP metinlerinde pek vurgulanmaz. Bu prompt onları kodundan önce yakalar.

```
Stellar Raven'ı kullan. Anchor entegrasyonu yapıyorum: [SEP-6 veya SEP-24, istemci tarafı mı sunucu tarafı mı].
Aşağıdaki tuzakların her biri için benim akışımda nasıl bir risk oluşturduğunu ve nasıl önleyeceğimi anlat, ilgili SEP bölümünü kaynak göster:
1. SEP-10 challenge işleminin ağa gönderilmemesi gerektiği
2. home_domain ile web_auth_domain farkı
3. SEP-24 arayüzünün iframe yerine açılır pencerede açılması ve postMessage ile tamamlanması
4. Ortak bir hesaba çekim yaparken memo ve memo_type'ın birebir gönderilmesi
5. Yatırma öncesi trustline gerekliliği ve /info içindeki claimable balance desteği
6. Tutarların float değil string/decimal olarak işlenmesi
7. asset_code'un tek başına belirsiz olması, asset_issuer ile birlikte kullanılması
8. İşlem durumlarının (pending_user_transfer_start, pending_trust, on_hold vb.) her biri için kullanıcıya ne gösterileceği
9. SEP-38 teklifinin süresinin dolması durumunda yeniden teklif alınması
10. SEP-10 JWT süresi dolduğunda kullanıcıyı başa atmadan yeniden kimlik doğrulama
```

## T3. Yurt dışına para transferi

```
Stellar Raven'ı kullan.
Projem şu kullanıcıların sınır ötesi para gönderme sorununu çözmeyi hedefliyor: [kimin kime, hangi ülkeye, ayda ortalama ne kadar para gönderdiğini anlat, örneğin Almanya'daki bir işçinin Türkiye'deki ailesine gönderdiği para].
Bugünkü yöntemlerle (banka havalesi, SWIFT, döviz bürosu, para transfer uygulamaları) Stellar'ı maliyet, süre ve erişilebilirlik açısından karşılaştır.
Bu akışta path payment, SEP-31 ve anchor'ların nasıl bir rol oynayacağını adım adım göster.
Karşı ülkede Stellar'a bağlı bir anchor olup olmadığını ekosistem verisinden kontrol et. Bulamazsan tahmin yürütme, "bu kaynaklarda bulunamadı" de.
Uyumluluk (KYC/AML) açısından dikkat etmem gereken noktaları listele ve bunun hukuki bir tavsiye olmadığını belirt.
```

## T4. Altın günü ve ortak birikim

Altın günü, kura, ortak kasa gibi dönüşümlü birikim grupları Türkiye'de çok yaygın ve güvene dayalı çalışıyor. Blokzincirin gerçekten değer katabileceği bir alan, ama doğru kurgulanırsa.

```
Stellar Raven'ı kullan.
Dönüşümlü bir birikim grubu (altın günü) uygulaması yapmak istiyorum: [kaç kişi, ne sıklıkla, hangi varlıkla (USDC, altın temelli bir token vb.), sıranın nasıl belirlendiği].
Şunları değerlendir:
1. Bu mantığı Soroban kontratıyla mı kurmalıyım, yoksa claimable balance ve çoklu imza gibi yerleşik özellikler yeterli mi?
2. Bir üye ödemesini yapmazsa ne olur? Bu durumu kontrat mı çözmeli, yoksa grup içi sosyal kurallar mı?
3. Paranın hiçbir aşamada benim (uygulama sahibinin) kontrolüne geçmemesi için mimari nasıl olmalı?
4. Ekosistemde bunu daha önce deneyen projeler var mı? (scout.searchHackathonBuilds ile "rotating savings" ve "ROSCA" terimlerini ara)
Kontrat önerirsen depolama türlerini (instance, persistent, temporary) ve TTL uzatmayı nasıl ele alacağımı da yaz.
```

## T5. Kripto bilmeyen kullanıcıya uygun deneyim

```
Projem şu: [fikrini anlat] ve hedef kitlem kripto deneyimi olmayan Türkiye'deki kullanıcılar.
Stellar Raven'ı kullanarak, kullanıcının seed phrase, trustline, XLM rezervi gibi kavramlarla hiç karşılaşmadan uygulamamı kullanabilmesi için hangi seçeneklerim olduğunu söyle:
- Passkey tabanlı smart account'lar
- İşlem ücretinin kullanıcı yerine ödenmesi (fee sponsorship, fee bump)
- Hesap oluşturma ve trustline ekleme adımlarının arka planda yapılması
- Stellar Wallets Kit ile birden fazla cüzdan desteği
Her seçenek için: kullanıcı deneyimine etkisi, anahtarın kimde durduğu (kullanıcıda mı, sunucuda mı), hackathon süresinde uygulanabilirliği ve dokümantasyon bağlantısı.
Anahtarı sunucuda tutan (custodial) bir çözüm önerirsen bunun risklerini ayrıca belirt.
```

## T6. Türkçe arayüz metinleri

```
Uygulamamın arayüzündeki şu İngilizce Stellar terimlerini, kripto bilmeyen bir Türk kullanıcının anlayacağı şekilde Türkçeye çevir: [terimleri listele, örneğin trustline, memo, claimable balance, transaction pending, insufficient balance].
Her terim için: kısa arayüz metni (buton veya etiket için), bir cümlelik açıklama (yardım metni için) ve kaçınılması gereken yanıltıcı çeviri.
Özellikle hata mesajlarında kullanıcıyı suçlamayan, ne yapması gerektiğini söyleyen bir dil kullan.
```

[← Önceki: 03 · Ekosistem araştırması](03-ekosistem-arastirmasi.md) · [Sonraki: 05 · Güvenlik ve kod incelemesi →](05-guvenlik-ve-kod-inceleme.md)
