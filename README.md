# Stellar Raven İstem Kiti

> Stellar üzerinde bir şey geliştirenler için kopyala-yapıştır Türkçe istemler (prompt). **Stellar Raven**'ı (Stellar ekosisteminin resmi MCP sunucusu) fikrini sınayan, teknik kararlarını kaynağa bağlayan ve sunumuna hazırlayan bir yardımcı pilot olarak kullanman için hazırlandı.

Kit üç soru etrafında kurulu:

1. **Gerçek bir problemi mi çözüyorum?**
2. **Stellar'ı doğru mu kullanıyorum?**
3. **Bunu güvenle yayına alıp anlatabilir miyim?**

İlk iki soru hackathon'larda en çok sorulanlar. Üçüncüsü ise projeyi hackathon sonrasına, yani hibe başvurusuna, güvenlik incelemesine ve gerçek kullanıcıya taşıyan kısım.

## Kitin haritası

| Dosya | Ne işe yarar? | Ne zaman kullanılır? |
| :---- | :------------ | :------------------- |
| [01 · Problem doğrulama](istemler/01-problem-dogrulama.md) | Fikrin gerçek bir acıya dokunuyor mu? | İlk saatlerde, kod yazmadan önce |
| [02 · Stellar'ı doğru kullanmak](istemler/02-stellar-teknoloji.md) | Doğru özellik, doğru SEP, Soroban mı klasik mi? | Mimari kararlarında |
| [03 · Ekosistem araştırması](istemler/03-ekosistem-arastirmasi.md) | Raven'ın canlı verisiyle rakip, boşluk ve önceki hackathon projeleri | Fikri seçerken ve konumlandırırken |
| [04 · Türkiye senaryoları](istemler/04-turkiye-senaryolari.md) | TL giriş-çıkış, havale, altın günü, kripto bilmeyen kullanıcı | Türkiye'deki kullanıcıya bir şey yapıyorsan |
| [05 · Güvenlik ve kod incelemesi](istemler/05-guvenlik-ve-kod-inceleme.md) | Soroban sözleşmesi ve köprü kurum entegrasyonu için hata avı | Demo öncesi ve yayına almadan önce |
| [06 · İleri konular](istemler/06-ileri-konular.md) | Yapay zekâ ajanlarının ödemeleri (x402, MPP), sıfır bilgi ispatları, geçiş anahtarları | Bu alanlarda yarışıyorsan |
| [07 · Sunum ve hibe](istemler/07-sunum-ve-hibe.md) | Kendi ürününü sade anlatmak, jüri canlandırması, SCF ve Instawards | Son saatlerde ve hackathon sonrasında |
| [Raven nasıl çalışır?](rehber/raven-nasil-calisir.md) | Raven'ın veri kaynakları ve cevaplarını okuma kuralları | İlk kullanımdan önce bir kez |
| [Beceri haritası](rehber/beceri-haritasi.md) | Hangi istemi hangi Stellar becerisiyle (skill) birlikte kullanmalı? | Claude Code, Cursor vb. kullanıyorsan |
| [Sözlük](rehber/sozluk.md) | Stellar terimlerinin Türkçe karşılıkları | Takılınca |

## Başlamadan önce: Raven'a bağlan

**1. Yol: tarayıcıdaki deneme alanı (playground).** Hiçbir şey kurmana gerek yok. Sayfaya gir, oturum aç ve sormaya başla.

```
https://raven.stellar.buzz/playground
```

**2. Yol: editörüne bağla.** Claude Code, Cursor veya VS Code kullanıyorsan Raven'ı tek komutla ekleyebilirsin. Claude Code için:

```bash
claude mcp add --transport http stellar-raven "https://raven.stellar.buzz/mcp"
```

Ardından `/mcp` komutunu çalıştır ve tarayıcı açıldığında oturum aç. Diğer istemciler için aynı adresi (`https://raven.stellar.buzz/mcp`) HTTP türünde bir MCP sunucusu olarak ekle.

## İstemler nasıl kullanılır?

1. Haritadan o anki ihtiyacına uyan dosyayı aç.
2. Köşeli parantez içindeki yerleri (`[fikrini anlat]` gibi) kendi projenin bilgileriyle doldur.
3. İstemi Raven'a yapıştır. Cevabı okurken [Raven nasıl çalışır?](rehber/raven-nasil-calisir.md) sayfasındaki kurallara göz at.

Projeni ne kadar somut anlatırsan (kim kullanıyor, hangi para birimi, hangi ağ, kaç kullanıcı) cevap o kadar işe yarar olur.

## Hızlı başlangıç: hackathon'un ilk saati

Vaktin azsa bu dört istemi sırayla çalıştır:

1. [03 · E1 Hackathon özeti](istemler/03-ekosistem-arastirmasi.md#e1-tek-seferde-hackathon-özeti): Fikrin daha önce yapılmış mı, nereden başlayabilirsin?
2. [01 · A1 Problemi netleştir](istemler/01-problem-dogrulama.md#a1-problemi-tanımla-ve-netleştir): Problemi tek cümleye indir.
3. [02 · B3 Soroban mı, klasik mi?](istemler/02-stellar-teknoloji.md#b3-soroban-mı-klasik-stellar-mı): Mimari kararını ver.
4. [02 · B5 Süre planı](istemler/02-stellar-teknoloji.md#b5-hackathon-süresinde-yapılabilir-mi): Canlı gösterilebilecek en küçük kapsamı belirle.

## Kaynaklar

| Kaynak | Bağlantı |
| :----- | :------- |
| Stellar Raven deneme alanı | https://raven.stellar.buzz/playground |
| Stellar Raven kod deposu | https://github.com/kalepail/stellar-raven |
| Stellar belgeleri: Yapay Zekâ ile Geliştirme | https://developers.stellar.org/docs/build/building-with-ai |
| Stellar resmi belgeleri | https://developers.stellar.org |
| Stellar beceri kataloğu | https://skills.stellar.org |
| SEP'ler (Stellar Ekosistem Önerileri) | https://github.com/stellar/stellar-protocol/tree/master/ecosystem |
| Stellar Lab (test ağında hesap ve işlem denemeleri) | https://lab.stellar.org |
| TR Mock Anchor (test ağında TRY ⇄ USDC deneme ortamı) | https://tr-mock-anchor.fly.dev |
| Stellar Topluluk Fonu (SCF) | https://communityfund.stellar.org |
| SCF El Kitabı: Instawards | https://stellar.gitbook.io/scf-handbook/scf-awards/instawards |
| Stellar geliştirici topluluğu (Discord) | https://discord.gg/stellardev |

## Katkı

Yeni bir istem, bir düzeltme ya da Türkiye'ye özel bir senaryo önermek istersen konu (issue) açabilir ya da değişiklik isteği (pull request) gönderebilirsin. Önerdiğin istemi Raven'da en az bir kez denemiş olman ve çıkan cevabın kaynak gösterdiğini kontrol etmen yeterli.

## Teşekkür

Bu kitin çıkış noktası, Alex Hernández'in Şili'deki Find Your Way hackathon'u için İspanyolca hazırladığı [Kit de Prompts para Stellar Raven](https://github.com/alex0tico/stellar-raven-prompts) çalışması. 01, 02 ve 07 numaralı dosyalardaki bazı istemler oradan uyarlandı. Geri kalanı Türkiye'deki geliştiriciler, Raven'ın canlı ekosistem araçları ve [skills.stellar.org](https://skills.stellar.org) becerileri düşünülerek yazıldı.
