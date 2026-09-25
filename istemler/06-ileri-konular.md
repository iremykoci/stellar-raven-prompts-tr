# 06 · İleri konular

[← Ana sayfa](../README.md)

Son dönem Stellar hackathon'larında öne çıkan alanlar: yapay zekâ ajanlarının kendi başına ödeme yapması, sıfır bilgi ispatlarıyla gizlilik, passkey ile çalışan akıllı cüzdanlar ve zincirler arası köprüler. Bu dosya o alanlarda doğru kararı vermen için hazırlandı.

## Ajan ödemeleri: x402 ve MPP

Bir API'yi yapay zekâ ajanlarına ücretli sunmak ya da ajanın bir API için ödeme yapmasını sağlamak istiyorsan iki protokol var:

- **x402:** HTTP 402 durum koduna dayanır. İstemci tam işlem değil, sadece kontrat yetkilendirme kaydı imzalar. İşlemi bir facilitator (örneğin OpenZeppelin Channels) kurar ve ücretini öder. Bu yüzden istemcinin XLM tutmasına gerek kalmaz. Başlaması en kolay yol budur.
- **MPP (Machine Payments Protocol):** Üçüncü taraf facilitator'a bağımlı olmak istemiyorsan kullanılır. Charge modunda her istek için ayrı ödeme yapılır. Session modunda ise çok sık istek atan ajanlar için ödeme kanalı üzerinden zincir dışı taahhütler kullanılır.

### İ1. x402 mi, MPP mi?

```
Stellar Raven'ı kullan ve agentic-payments skill'ine ve resmi dokümantasyona dayan.
Projem şu: [ne sattığını veya ajanın neye ödeme yaptığını anlat]. Bir ajan saatte yaklaşık [istek sayısı] istek atacak ve istek başına ücret [tutar] USDC olacak.
x402, MPP Charge ve MPP Session arasında benim durumum için hangisinin uygun olduğunu bir tabloyla karşılaştır: istemcinin XLM tutması gerekiyor mu, üçüncü taraf bağımlılığı, sık istekte maliyet, kurulum zorluğu.
Seçtiğin yol için testnet'te çalışan en küçük satıcı (seller) ve alıcı (buyer) örneğinin adımlarını yaz.
Sık yapılan hataları da ekle: USDC trustline'ının eklenmemesi, testnet ve mainnet USDC adreslerinin karışması, x402 paket sürümlerinin karıştırılması, tarayıcıda Node'a özel imzalayıcı kullanılmaya çalışılması.
```

### İ2. Ajana harcama sınırı koy

Yapay zekâya fon hareket ettirme yetkisi vermek, jüri ve hibe değerlendiricilerinin en çok sorguladığı konu.

```
Stellar Raven'ı kullan.
Bir yapay zekâ ajanının benim adıma ödeme yapmasını istiyorum ama kontrolü kaybetmek istemiyorum. Ajanın yapacağı ödemeler şunlar: [ne için, kime, ne sıklıkla, ne kadar].
Bu sınırları sunucu tarafında bir if kontrolüyle değil, zincir üzerinde zorunlu kılmak için hangi seçeneklerim var? (smart account politikaları, oturum anahtarları, harcama limitli kontratlar, izinli alıcı listesi)
Her seçenek için: ajanın anahtarı çalınırsa en kötü ihtimalle ne kadar kaybederim, limit nasıl güncellenir, insan onayı nerede devreye girer?
Hackathon demo'sunda "ajan limiti aşmaya çalışıyor ve reddediliyor" senaryosunu nasıl gösterebileceğimi de anlat.
```

## Gizlilik: sıfır bilgi ispatları

Stellar, Soroban kontratlarında ZK ispatlarını doğrulamak için yerleşik kriptografik fonksiyonlar sunar: BLS12-381 (CAP-59), BN254 (CAP-74) ve Poseidon hash (CAP-75). Hangisinin hangi protokol sürümünde geldiğini Raven'a doğrulat.

### İ3. Gerçekten ZK'ya ihtiyacım var mı?

```
Stellar Raven'ı kullan ve zk-proofs skill'ine dayan.
Projemde gizlemek istediğim bilgi şu: [neyin, kimden gizleneceğini anlat, örneğin kimin ne kadar ödediği, kullanıcının yaşı, oy tercihi].
Önce ZK kullanmadan bu gizliliği sağlamanın daha basit bir yolu var mı, onu söyle.
ZK gerçekten gerekliyse: Circom, Noir ve RISC Zero arasında benim durumum için hangisi uygun? Hangi eğri (BN254 veya BLS12-381) ve hangi ispat sistemi (Groth16 vb.) Soroban'da doğrulanabiliyor? Her birinin gerektirdiği protokol sürümünü ve CAP numarasını yaz.
Hackathon süresinde ispat devresi, doğrulayıcı kontrat ve arayüzden hangilerini gerçekten bitirebileceğimi gerçekçi bir şekilde söyle.
```

### İ4. ZK projesini anlaşılır kıl

ZK projeleri teknik olarak etkileyici olur ama jüri ne işe yaradığını anlamazsa puan alamaz.

```
ZK kullanan projem şu: [projeyi anlat].
Bunu kriptografi bilmeyen bir jüriye 30 saniyede anlatmama yardım et. "Sıfır bilgi ispatı" terimini kullanmadan önce, kullanıcının neyi kanıtladığını ve neyi göstermediğini somut bir örnekle anlat.
Sonra demo sırasında ekranda neyin görünmesi gerektiğini öner: ispatın doğrulandığını gösteren işlem, gizli kalan verinin gerçekten zincirde görünmediğinin kanıtı.
```

## Passkey ve akıllı cüzdanlar

### İ5. Passkey ile giriş

```
Stellar Raven'ı kullan ve dapp skill'inin smart account bölümüne dayan.
Kullanıcılarımın seed phrase yerine Face ID, Touch ID veya Windows Hello ile (passkey) hesap açıp işlem imzalamasını istiyorum. Uygulamam: [web, mobil, ikisi de].
Passkey tabanlı bir smart account'un nasıl çalıştığını, hangi CAP'in (secp256r1 doğrulaması) bunu mümkün kıldığını ve hangi kütüphaneyle başlamam gerektiğini anlat.
Kullanıcı cihazını kaybederse hesabı nasıl kurtarır? Birden fazla cihaz nasıl eklenir?
İşlem ücretlerini kim öder ve bunun için bir relayer'a ihtiyacım var mı?
```

### İ6. Passkey akışını test et

```
Passkey kullanan bir Stellar uygulamam var ve hesap oluşturma, giriş ve imzalama akışını otomatik test etmek istiyorum.
Gerçek bir cihaza ihtiyaç duymadan, tarayıcının sanal WebAuthn doğrulayıcısıyla (Chrome DevTools Protocol) bu akışları nasıl test edebileceğimi anlat.
CI'da çalışacak en küçük test senaryosunu yaz: hesap oluştur, sayfayı yenile, aynı passkey ile tekrar giriş yap, bir testnet işlemi imzala.
```

## Zincirler arası

### İ7. Başka bir zincirle konuşmam gerekiyor mu?

```
Stellar Raven'ı kullan ve cross-chain skill'ine dayan.
Projemde şunu yapmam gerekiyor: [örneğin Ethereum'daki USDC'yi Stellar'a getirmek, Stellar'daki bir kontratın başka zincirdeki bir kontratı çağırması, bir tokenı birden fazla zincirde yaşatmak].
Circle CCTP, Axelar (GMP ve Interchain Token Service) ve intent tabanlı takas çözümlerinden hangisinin benim durumuma uyduğunu bir karar tablosuyla göster.
USDC'yi Stellar'a köprülüyorsam alıcı tarafta dikkat etmem gereken özel bir gereksinim var mı?
Bunu hackathon demo'sunda testnet üzerinde gösterebilir miyim, yoksa sadece mimari olarak mı sunmalıyım?
```

[← Önceki: 05 · Güvenlik ve kod incelemesi](05-guvenlik-ve-kod-inceleme.md) · [Sonraki: 07 · Sunum ve hibe →](07-sunum-ve-hibe.md)
