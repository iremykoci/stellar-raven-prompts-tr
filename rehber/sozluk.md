# Sözlük

[← Ana sayfa](../README.md)

Kitte kullandığımız Türkçe terimler ve İngilizce karşılıkları. Belgelerde ve kodda İngilizce hallerini göreceğin için ikisini birlikte verdik.

| Türkçe | İngilizce | Kısaca |
| :----- | :-------- | :----- |
| Hesap | Account | Stellar'daki temel kimlik. `G...` ile başlayan açık anahtarla gösterilir. |
| Gizli anahtar | Secret key | `S...` ile başlar. Hesabın tam kontrolünü verir, asla paylaşılmaz ve koda yazılmaz. |
| Taban rezerv | Base reserve | Bir hesabın ağda var olabilmesi için tutması gereken en az XLM miktarı. |
| Varlık | Asset | Stellar'da çıkarılan her türlü değer: sabit değerli kripto para, token, puan. Kodu ve çıkaranıyla tanımlanır. |
| Çıkaran | Issuer | Bir varlığı çıkaran hesap. `USDC` kodu tek başına yetmez, çıkaranla birlikte anlam kazanır. |
| Güven hattı | Trustline | Bir hesabın bir varlığı tutmayı kabul ettiğini gösteren kayıt. Olmadan o varlığı alamazsın. |
| Köprü kurum | Anchor | Banka parası ile Stellar varlıkları arasında giriş ve çıkış sağlayan, genellikle lisanslı kurum. |
| Giriş / Çıkış | On-ramp / Off-ramp | Banka parasından kriptoya geçiş ve tersi. |
| Stellar Ekosistem Önerisi | SEP | Cüzdan, köprü kurum ve uygulamaların birbiriyle konuşması için ortak standartlar. |
| Çekirdek Geliştirme Önerisi | CAP | Protokolün kendisinde yapılan değişiklikler. |
| Not | Memo | İşleme eklenen kısa bilgi. Ortak hesaplara yapılan ödemelerde kimin ödediğini belirlemek için zorunlu olabilir. |
| Yol ödemesi | Path payment | Gönderenin bir varlıkla ödeyip alıcının başka bir varlık almasını sağlayan tek işlem. |
| Stellar'ın yerleşik borsası | SDEX | Stellar protokolüne gömülü alım-satım emir defteri. |
| Talep edilebilir bakiye | Claimable balance | Alıcının sonradan, belirli koşullarla talep edebileceği şekilde bırakılan ödeme. |
| Geri alma | Clawback | Çıkaranın, izin verilmişse, bir varlığı hesaptan geri alabilmesi. |
| Soroban | Soroban | Stellar'ın akıllı sözleşme platformu. Sözleşmeler Rust ile yazılır. |
| Akıllı sözleşme | Smart contract | Zincir üzerinde çalışan ve kurallarını kodla uygulayan program. |
| Stellar Varlık Sözleşmesi | SAC (Stellar Asset Contract) | Klasik bir Stellar varlığını Soroban sözleşmelerinden kullanılabilir hale getiren yerleşik sözleşme. |
| Token arayüzü | SEP-41 | Soroban tokenlarının uyduğu standart arayüz. |
| Depolama türleri | Instance / Persistent / Temporary storage | Soroban'da verinin nerede ve ne kadar süre tutulacağını belirleyen üç tür: sözleşmeyle birlikte yüklenen, kalıcı ve geçici. |
| Yaşam süresi | TTL (Time to live) | Bir verinin arşivlenmeden önce ağda kalacağı süre. Uzatılmazsa veri arşivlenir. |
| Arşivlenme | Archival | Yaşam süresi dolan verinin etkin durumdan çıkarılması. |
| Yetki doğrulama | `require_auth()` | Bir sözleşme fonksiyonunun, ilgili adresin imzasını zorunlu kılması. |
| Stellar RPC | Stellar RPC | Soroban sözleşmeleriyle etkileşim ve güncel zincir verisi için önerilen arayüz. |
| Horizon | Horizon | Klasik Stellar verisi için web arayüzü (REST API). |
| Test ağı / Ana ağ | Testnet / Mainnet | Test ağında para gerçek değildir. Ana ağda her işlem gerçek değer taşır. |
| Friendbot | Friendbot | Test ağındaki hesaplara ücretsiz test XLM'i gönderen servis. |
| Freighter | Freighter | Stellar için tarayıcı eklentisi cüzdanı. |
| Geçiş anahtarı | Passkey | Face ID, Touch ID gibi cihaz doğrulamasıyla çalışan, şifresiz giriş yöntemi. |
| Akıllı hesap | Smart account | Kuralları sözleşmeyle belirlenen hesap. Geçiş anahtarı, harcama limiti gibi özellikler sunabilir. |
| Ücret sponsorluğu | Fee sponsorship / Fee bump | İşlem ücretini kullanıcı yerine başka bir hesabın ödemesi. |
| Kurtarma ifadesi | Seed phrase | Bir cüzdanı geri yüklemeye yarayan kelime dizisi. |
| Emanet | Escrow | Koşullar yerine gelene kadar parayı tutan düzenek. |
| Emanetçi | Custodial | Kullanıcının anahtarını uygulama sahibinin tuttuğu model. |
| Aracı | Facilitator | x402'de ödemeyi doğrulayıp zincire gönderen servis. |
| Aktarıcı | Relayer | Kullanıcının işlemini ücretini ödeyerek ağa ileten servis. |
| Veri sağlayıcı | Oracle | Zincir dışındaki bir veriyi (örneğin fiyatı) sözleşmelere taşıyan servis. |
| x402 | x402 | HTTP 402 koduna dayanan, API'lere istek başına ödeme protokolü. |
| Makine Ödeme Protokolü | MPP | Ajanlar arası ödemeler için, aracı gerektirmeyen alternatif protokol. |
| Sıfır bilgi ispatı | ZK proof | Bir bilgiyi açıklamadan doğru olduğunu kanıtlama yöntemi. |
| Stellar Topluluk Fonu | SCF | Stellar üzerinde geliştirme yapan projelere verilen hibe programı. |
| Instawards | Instawards | SCF'in küçük ve hızlı hibe programı. |
| Teklif çağrısı | RFP | Ekosistemin yapılmasını istediği ve fonladığı işler için açılan çağrı. |
| İstem | Prompt | Yapay zekâya verdiğin talimat ya da soru. |
| Beceri | Skill | Yapay zekâ asistanına belirli bir işi nasıl yapacağını anlatan talimat paketi. |
| Sürekli entegrasyon | CI | Her kod değişikliğinde testleri otomatik çalıştıran sistem. |
