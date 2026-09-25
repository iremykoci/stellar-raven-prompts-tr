# 06 · İleri konular

[← Ana sayfa](../README.md)

Son dönem Stellar hackathon'larında öne çıkan alanlar: yapay zekâ ajanlarının kendi başına ödeme yapması, sıfır bilgi ispatlarıyla gizlilik, geçiş anahtarıyla (passkey) çalışan akıllı cüzdanlar ve zincirler arası köprüler. Bu dosya o alanlarda doğru kararı vermen için hazırlandı.

## Yapay zekâ ajanlarının ödemeleri: x402 ve MPP

Bir API'yi yapay zekâ ajanlarına ücretli sunmak ya da ajanın bir API için ödeme yapmasını sağlamak istiyorsan iki protokol var:

- **x402:** HTTP 402 durum koduna dayanır. İstemci işlemin tamamını değil, sadece sözleşme yetkilendirme kaydını imzalar. İşlemi bir aracı (facilitator, örneğin OpenZeppelin Channels) kurar ve ücretini öder. Bu yüzden istemcinin XLM tutmasına gerek kalmaz. Başlaması en kolay yol budur.
- **MPP (Makine Ödeme Protokolü):** Üçüncü taraf bir aracıya bağımlı olmak istemiyorsan kullanılır. Tekil ödeme (Charge) modunda her istek için ayrı ödeme yapılır. Oturum (Session) modunda ise çok sık istek atan ajanlar için bir ödeme kanalı üzerinden zincir dışı taahhütler kullanılır.

### İ1. x402 mi, MPP mi?

```
Stellar Raven'ı kullan ve agentic-payments becerisine ve resmi belgelere dayan.
Projem şu: [ne sattığını veya ajanın neye ödeme yaptığını anlat]. Bir ajan saatte yaklaşık [istek sayısı] istek atacak ve istek başına ücret [tutar] USDC olacak.
x402, MPP tekil ödeme (Charge) ve MPP oturum (Session) modları arasında benim durumum için hangisinin uygun olduğunu bir tabloyla karşılaştır: istemcinin XLM tutması gerekiyor mu, üçüncü taraf bağımlılığı, sık istekte maliyet, kurulum zorluğu.
Seçtiğin yol için test ağında çalışan en küçük satıcı ve alıcı örneğinin adımlarını yaz.
Sık yapılan hataları da ekle: USDC güven hattının eklenmemesi, test ağı ve ana ağ USDC adreslerinin karışması, x402 paket sürümlerinin karıştırılması, tarayıcıda sadece Node.js'te çalışan bir imzalayıcının kullanılmaya çalışılması.
```

### İ2. Ajana harcama sınırı koy

Yapay zekâya para hareket ettirme yetkisi vermek, jüri ve hibe değerlendiricilerinin en çok sorguladığı konu.

```
Stellar Raven'ı kullan.
Bir yapay zekâ ajanının benim adıma ödeme yapmasını istiyorum ama kontrolü kaybetmek istemiyorum. Ajanın yapacağı ödemeler şunlar: [ne için, kime, ne sıklıkla, ne kadar].
Bu sınırları sunucu tarafında basit bir kontrolle değil, zincir üzerinde zorunlu kılmak için hangi seçeneklerim var? (akıllı hesap politikaları, oturum anahtarları, harcama limitli sözleşmeler, izinli alıcı listesi)
Her seçenek için: ajanın anahtarı çalınırsa en kötü ihtimalle ne kadar kaybederim, limit nasıl güncellenir, insan onayı nerede devreye girer?
Hackathon demosunda "ajan limiti aşmaya çalışıyor ve reddediliyor" senaryosunu nasıl gösterebileceğimi de anlat.
```

## Gizlilik: sıfır bilgi ispatları

Stellar, Soroban sözleşmelerinde sıfır bilgi (ZK) ispatlarını doğrulamak için yerleşik kriptografik fonksiyonlar sunar: BLS12-381 (CAP-59), BN254 (CAP-74) ve Poseidon özetleme fonksiyonu (CAP-75). Hangisinin hangi protokol sürümünde geldiğini Raven'a doğrulat.

### İ3. Gerçekten sıfır bilgi ispatına ihtiyacım var mı?

```
Stellar Raven'ı kullan ve zk-proofs becerisine dayan.
Projemde gizlemek istediğim bilgi şu: [neyin, kimden gizleneceğini anlat, örneğin kimin ne kadar ödediği, kullanıcının yaşı, oy tercihi].
Önce sıfır bilgi ispatı kullanmadan bu gizliliği sağlamanın daha basit bir yolu var mı, onu söyle.
Sıfır bilgi ispatı gerçekten gerekliyse: Circom, Noir ve RISC Zero arasında benim durumum için hangisi uygun? Hangi eğri (BN254 veya BLS12-381) ve hangi ispat sistemi (Groth16 vb.) Soroban'da doğrulanabiliyor? Her birinin gerektirdiği protokol sürümünü ve CAP numarasını yaz.
Hackathon süresinde ispat devresi, doğrulayıcı sözleşme ve arayüzden hangilerini gerçekten bitirebileceğimi gerçekçi bir şekilde söyle.
```

### İ4. Sıfır bilgi projesini anlaşılır kıl

Sıfır bilgi projeleri teknik olarak etkileyici olur ama jüri ne işe yaradığını anlamazsa puan alamaz.

```
Sıfır bilgi ispatı kullanan projem şu: [projeyi anlat].
Bunu kriptografi bilmeyen bir jüriye 30 saniyede anlatmama yardım et. "Sıfır bilgi ispatı" terimini kullanmadan önce, kullanıcının neyi kanıtladığını ve neyi göstermediğini somut bir örnekle anlat.
Sonra demo sırasında ekranda neyin görünmesi gerektiğini öner: ispatın doğrulandığını gösteren işlem, gizli kalan verinin gerçekten zincirde görünmediğinin kanıtı.
```

## Geçiş anahtarı ve akıllı cüzdanlar

### İ5. Geçiş anahtarıyla giriş

```
Stellar Raven'ı kullan ve dapp becerisinin akıllı hesap (smart account) bölümüne dayan.
Kullanıcılarımın kurtarma ifadesi yerine Face ID, Touch ID veya Windows Hello ile, yani geçiş anahtarıyla (passkey) hesap açıp işlem imzalamasını istiyorum. Uygulamam: [web, mobil, ikisi de].
Geçiş anahtarıyla çalışan bir akıllı hesabın nasıl işlediğini, hangi CAP'in (secp256r1 doğrulaması) bunu mümkün kıldığını ve hangi kütüphaneyle başlamam gerektiğini anlat.
Kullanıcı cihazını kaybederse hesabı nasıl kurtarır? Birden fazla cihaz nasıl eklenir?
İşlem ücretlerini kim öder ve bunun için bir aktarıcı servise (relayer) ihtiyacım var mı?
```

### İ6. Geçiş anahtarı akışını test et

```
Geçiş anahtarı kullanan bir Stellar uygulamam var ve hesap açma, giriş ve imzalama akışını otomatik test etmek istiyorum.
Gerçek bir cihaza ihtiyaç duymadan, tarayıcının sanal WebAuthn doğrulayıcısıyla (Chrome DevTools Protocol) bu akışları nasıl test edebileceğimi anlat.
Sürekli entegrasyonda (CI) çalışacak en küçük test senaryosunu yaz: hesap aç, sayfayı yenile, aynı geçiş anahtarıyla tekrar giriş yap, test ağında bir işlem imzala.
```

## Zincirler arası

### İ7. Başka bir zincirle konuşmam gerekiyor mu?

```
Stellar Raven'ı kullan ve cross-chain becerisine dayan.
Projemde şunu yapmam gerekiyor: [örneğin Ethereum'daki USDC'yi Stellar'a getirmek, Stellar'daki bir sözleşmenin başka zincirdeki bir sözleşmeyi çağırması, bir tokenı birden fazla zincirde yaşatmak].
Circle CCTP, Axelar (GMP ve Interchain Token Service) ve niyet tabanlı (intent) takas çözümlerinden hangisinin benim durumuma uyduğunu bir karar tablosuyla göster.
USDC'yi Stellar'a köprülüyorsam alıcı tarafta dikkat etmem gereken özel bir gereksinim var mı?
Bunu hackathon demosunda test ağında gösterebilir miyim, yoksa sadece mimari olarak mı sunmalıyım?
```

[← Önceki: 05 · Güvenlik ve kod incelemesi](05-guvenlik-ve-kod-inceleme.md) · [Sonraki: 07 · Sunum ve hibe →](07-sunum-ve-hibe.md)
