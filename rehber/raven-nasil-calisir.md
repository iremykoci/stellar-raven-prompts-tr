# Raven nasıl çalışır?

[← Ana sayfa](../README.md)

Stellar Raven, SDF (Stellar Development Foundation) tarafından işletilen bir MCP (Model Context Protocol) sunucusu. Yapay zekâ asistanını Stellar'ın resmi dokümantasyonuna ve ekosistemin canlı verisine bağlar. Böylece asistanın cevapları tahmine değil, gerçek ve güncel kaynaklara dayanır.

## İki araç, dört kaynak ailesi

Raven dışarıya iki araç açar:

- **`search`**: Hangi veri kaynağında hangi işlemin (operation) ya da skill'in bulunduğunu arar.
- **`execute`**: Bulunan işlemleri, güvenli bir ortamda çalışan küçük bir JavaScript betiğiyle birleştirip çalıştırır.

Sen bu araçları doğrudan kullanmazsın. Asistanın, senin prompt'una göre hangi kaynağa bakacağına kendisi karar verir. Ama hangi kaynakların olduğunu bilirsen daha iyi soru sorarsın:

| Kaynak ailesi | İçinde ne var? | Ne zaman işe yarar? |
| :------------ | :------------- | :------------------ |
| **stellarDocs** | developers.stellar.org resmi dokümantasyonu: protokol, SDK, CLI, kontratlar, RPC, anchor, cüzdan | "Bu nasıl yapılır?", "Bu fonksiyon ne döndürür?" |
| **scout** | Canlı ekosistem grafiği: projeler, repolar, hackathon projeleri, SCF fonlamaları, RFP'ler, güvenlik denetimleri, stablecoin'ler | "Bu daha önce yapıldı mı?", "Bu alan kalabalık mı?", "Bu protokol denetlendi mi?" |
| **lumenloop** | Topluluk ve editoryal içerik: proje dizini, haberler, konuşmalar, araştırmalar, SCF geçmişi | "Son zamanlarda ne oldu?", "Bu proje hakkında ne söylendi?" |
| **skills** | Test edilmiş inşa, entegrasyon ve güvenlik rehberleri (skills.stellar.org'daki skill'lerin bir kısmı) | "Bunu adım adım nasıl kurarım?", "Neye dikkat etmeliyim?" |

## Bu kitte sık kullanılan araçlar

| Araç | Ne yapar? |
| :--- | :-------- |
| `scout.hackathonBrief` | Bir fikir için rakipler, önceki hackathon projeleri, başlangıç repoları, canlı kontratlar, açık fonlama ve "iddia etmemen gerekenler" tek seferde |
| `scout.vetIdea` | Fikrin rakiplerini, olgunluklarını, boşluğu ve fonlamayı gösterir |
| `scout.getClusters` | Ekosistemi konu kümelerine ayırıp her birine 1-10 arası kalabalık puanı verir |
| `scout.analyzeEcosystem` | Hackathon, fonlama, kategori, TVL, boşluk, geliştirici ve araç zinciri istatistikleri |
| `scout.searchHackathonBuilds` | Stellar hackathon'larında yapılmış tüm projelerde arama |
| `scout.getRfps` | Açık ve kapalı RFP'ler ile güncel SCF turunun başvuru penceresi |
| `scout.listAudits` | Yayımlanmış güvenlik denetim raporları |
| `lumenloop.search_content_semantic` | Haber, yazı ve araştırmalarda anlamsal arama |

## Cevapları okurken beş kural

1. **Kaynak iste.** Raven'ın gücü kaynak gösterebilmesi. Bir cevap kaynak göstermiyorsa ya da genel geçer geliyorsa tekrar sor: "Bunu hangi sayfaya dayanarak söylüyorsun?"
2. **Tarih iste.** Proje sayıları, fonlama tutarları, TVL, açık başvuru tarihleri gibi değişken bilgiler mutlaka bir tarihle gelmeli.
3. **"Bulunamadı" ile "yok" aynı şey değil.** Raven bir şey bulamadığında bu, o şeyin olmadığını göstermez, sadece bu kaynaklarda olmadığını gösterir. Özellikle "rakibim yok" sonucuna varmadan önce farklı kelimelerle bir kez daha arat.
4. **Ad benzerliğine aldanma.** Bir projeyle ilgili bilgi, ancak ad ve kaynak birebir eşleşiyorsa o projeye aittir. Benzer adlı başka bir projenin bilgisini sunumuna taşıma.
5. **Son karar senin.** Raven teknik fizibiliteyi ve Stellar'a uyumu kontrol eder. İş modelinin sürdürülebilirliğini ya da sunumunun kalitesini değerlendirmez. Önemli bir şeyi bir cevabın üzerine inşa etmeden önce resmi dokümantasyonla karşılaştır.

## Daha iyi sonuç için ipuçları

- **Arama ifadesini İngilizce, cevabı Türkçe iste.** Ekosistem verisinin büyük kısmı İngilizce. "`rotating savings circle` için ara, sonucu Türkçe özetle" gibi bir kalıp daha iyi sonuç verir.
- **Aracın adını yaz.** "`scout.vetIdea` aracını kullan" demek, Raven'ın doğru kaynağa gitmesini sağlar.
- **Birden fazla aileyi birleştir.** "Dokümantasyona göre nasıl yapılır, ekosistemde kim yapmış?" gibi iki kaynağı birden kullanan sorular daha sağlam cevaplar üretir.
- **Çıktı biçimini belirt.** Tablo, madde listesi, tek cümle gibi.
