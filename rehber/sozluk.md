# Sözlük

[← Ana sayfa](../README.md)

Stellar dünyasında sık geçen terimler ve Türkçe karşılıkları. Kodda ve dokümantasyonda İngilizce hallerini göreceğin için ikisini birlikte verdik.

| Terim | Türkçe karşılığı | Kısaca |
| :---- | :--------------- | :----- |
| Account | Hesap | Stellar'daki temel kimlik. `G...` ile başlayan açık anahtarla gösterilir. |
| Secret key | Gizli anahtar | `S...` ile başlar. Hesabın tam kontrolünü verir, asla paylaşılmaz ve koda yazılmaz. |
| Base reserve | Taban rezerv | Bir hesabın ağda var olabilmesi için tutması gereken en az XLM miktarı. |
| Asset | Varlık | Stellar'da çıkarılan her türlü değer: stablecoin, token, puan. Kod ve çıkaran (issuer) ile tanımlanır. |
| Issuer | Çıkaran | Bir varlığı çıkaran hesap. `USDC` kodu tek başına yetmez, çıkaranla birlikte anlam kazanır. |
| Trustline | Güven hattı | Bir hesabın bir varlığı tutmayı kabul ettiğini gösteren kayıt. Olmadan o varlığı alamazsın. |
| Anchor | Anchor (köprü kurum) | Banka parası ile Stellar varlıkları arasında giriş ve çıkış sağlayan, genellikle lisanslı kurum. |
| On-ramp / Off-ramp | Giriş / Çıkış | Banka parasından kriptoya geçiş ve tersi. |
| SEP | Stellar Ekosistem Önerisi | Cüzdan, anchor ve uygulamaların birbiriyle konuşması için ortak standartlar. |
| CAP | Çekirdek Geliştirme Önerisi | Protokolün kendisinde yapılan değişiklikler. |
| Memo | Not | İşleme eklenen kısa bilgi. Ortak hesaplara yapılan ödemelerde kimin ödediğini belirlemek için zorunlu olabilir. |
| Path payment | Yol ödemesi | Gönderenin bir varlıkla ödeyip alıcının başka bir varlık almasını sağlayan tek işlem. |
| SDEX | Merkeziyetsiz borsa | Stellar'ın protokole gömülü emir defteri. |
| Claimable balance | Talep edilebilir bakiye | Alıcının sonradan, belirli koşullarla talep edebileceği şekilde bırakılan ödeme. |
| Clawback | Geri alma | Çıkaranın, izin verilmişse, bir varlığı hesaptan geri alabilmesi. |
| Soroban | Soroban | Stellar'ın akıllı kontrat platformu. Kontratlar Rust ile yazılır. |
| SAC (Stellar Asset Contract) | Stellar Varlık Kontratı | Klasik bir Stellar varlığını Soroban kontratlarından kullanılabilir hale getiren yerleşik kontrat. |
| SEP-41 | Token arayüzü | Soroban tokenlarının uyduğu standart arayüz. |
| Storage (instance / persistent / temporary) | Depolama (örnek / kalıcı / geçici) | Soroban'da verinin nerede ve ne kadar süre tutulacağını belirleyen üç tür. |
| TTL (Time to live) | Yaşam süresi | Bir verinin arşivlenmeden önce ağda kalacağı süre. Uzatılmazsa veri arşivlenir. |
| Archival | Arşivlenme | TTL'i dolan verinin aktif durumdan çıkarılması. |
| `require_auth()` | Yetki doğrulama | Bir kontrat fonksiyonunun, ilgili adresin imzasını zorunlu kılması. |
| RPC | Stellar RPC | Soroban kontratlarıyla etkileşim ve güncel zincir verisi için önerilen arayüz. |
| Horizon | Horizon | Klasik Stellar verisi için REST API. |
| Testnet / Mainnet | Test ağı / Ana ağ | Testnet'te para gerçek değildir. Mainnet'te her işlem gerçek değer taşır. |
| Friendbot | Friendbot | Testnet hesaplarına ücretsiz test XLM'i gönderen servis. |
| Freighter | Freighter | Stellar için tarayıcı eklentisi cüzdanı. |
| Passkey | Geçiş anahtarı | Face ID, Touch ID gibi cihaz doğrulamasıyla çalışan, şifresiz giriş yöntemi. |
| Smart account | Akıllı hesap | Kuralları kontratla belirlenen hesap. Passkey, harcama limiti gibi özellikler sunabilir. |
| Fee sponsorship / Fee bump | Ücret sponsorluğu | İşlem ücretini kullanıcı yerine başka bir hesabın ödemesi. |
| x402 | x402 | HTTP 402 koduna dayanan, API'lere istek başına ödeme protokolü. |
| MPP | Makine Ödeme Protokolü | Ajanlar arası ödemeler için, facilitator gerektirmeyen alternatif protokol. |
| ZK proof | Sıfır bilgi ispatı | Bir bilgiyi açıklamadan doğru olduğunu kanıtlama yöntemi. |
| SCF | Stellar Topluluk Fonu | Stellar üzerinde inşa eden projelere verilen hibe programı. |
| Instawards | Instawards | SCF'in küçük ve hızlı hibe programı. |
| RFP | Teklif çağrısı | Ekosistemin inşa edilmesini istediği ve fonladığı işler için açılan çağrı. |
