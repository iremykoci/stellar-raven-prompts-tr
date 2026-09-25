# Beceri haritası

[← Ana sayfa](../README.md)

[skills.stellar.org](https://skills.stellar.org), Stellar üzerinde çalışan yapay zekâ asistanları için hazırlanmış becerilerin (skill) kataloğu. Beceri, asistanın belirli bir işi nasıl yapacağını anlatan bir talimat paketidir: bir kontrol listesi, bir geliştirme rehberi ya da bir araştırma yöntemi.

Becerileri iki yoldan kullanabilirsin:

- **Raven üzerinden:** Bazı beceriler Raven'ın içinde hazır gelir. İstemde becerinin adını yazman yeterli (örneğin "`stellar-project-dossier` becerisini kullan").
- **Editörüne kurarak:** Claude Code, Cursor gibi araçlarda becerileri kendi bilgisayarına kurabilirsin. Kurulum talimatları katalog sayfasında.

> **Dikkat:** Katalogdaki becerilerin bir kısmı Stellar Geliştirme Vakfı (SDF) tarafından resmi olarak yazıldı, bir kısmı ise topluluk tarafından yazıldı ve SDF tarafından incelenmedi. Özellikle gerçek para hareket ettiren (ödeme, hazine yönetimi, köprü) topluluk becerilerini kullanmadan önce içeriğini oku.

## Hangi istem, hangi beceri?

| Kit dosyası | İşine yarayacak beceriler | Resmi mi? |
| :---------- | :------------------------ | :-------- |
| [01 · Problem doğrulama](../istemler/01-problem-dogrulama.md) | `stellar-builder-quickstart` | Topluluk |
| [02 · Stellar'ı doğru kullanmak](../istemler/02-stellar-teknoloji.md) | `standards`, `assets`, `dapp`, `data`, `smart-contracts` | Resmi (SDF) |
| [03 · Ekosistem araştırması](../istemler/03-ekosistem-arastirmasi.md) | `stellar-scout`, `stellar-ecosystem-scout`, `stellar-integration-finder`, `stellar-project-dossier`, `stellar-ecosystem-digest` | Topluluk |
| [04 · Türkiye senaryoları](../istemler/04-turkiye-senaryolari.md) | `stellar-anchor-skill`, `standards`, `dapp` | Topluluk + Resmi |
| [05 · Güvenlik ve kod incelemesi](../istemler/05-guvenlik-ve-kod-inceleme.md) | `soroban-common-mistakes`, `smart-contracts` (security.md, testing.md), `setup-stellar-contracts` | Topluluk + Resmi |
| [06 · İleri konular](../istemler/06-ileri-konular.md) | `agentic-payments`, `zk-proofs`, `cross-chain`, `dapp` (smart-accounts.md), `agent-browser-webauthn` | Resmi + Topluluk |
| [07 · Sunum ve hibe](../istemler/07-sunum-ve-hibe.md) | `scf-submission-radar`, `stellar-content-auditor` (S1'deki öğretme yöntemi istemin içinde, ayrı bir beceri gerekmez) | Topluluk |

## Resmi SDF becerileri kısaca

| Beceri | Ne anlatır? |
| :----- | :---------- |
| `smart-contracts` | Soroban sözleşme geliştirme: kurulum, depolama ve yaşam süresi (TTL), yetkilendirme, testler, güvenlik |
| `dapp` | JavaScript SDK, Freighter, Stellar Wallets Kit, geçiş anahtarlı akıllı hesaplar, işlem oluşturma ve gönderme |
| `assets` | Klasik varlıklar, güven hatları, yetkilendirme bayrakları, geri alma (clawback), Stellar Varlık Sözleşmesi (SAC) |
| `data` | Stellar RPC ve Horizon ile zincir verisi okuma, canlı veri akışı, sayfalama, dizinleme |
| `standards` | SEP ve CAP haritası, ekosistem projeleri, resmi bağlantılar |
| `agentic-payments` | x402 ve MPP ile makineden makineye ödemeler |
| `zk-proofs` | BLS12-381, BN254, Poseidon ile Soroban'da sıfır bilgi ispatı doğrulama; Circom, Noir, RISC Zero |
| `cross-chain` | Circle CCTP, Axelar, zincirler arası takaslar |

> Beceri adları (`smart-contracts`, `dapp` gibi) katalogdaki gerçek adlardır. Raven'da ve editörde bu adlarla çağrıldıkları için değiştirilmedi.

## Beceriyi istemde kullanmak

Genel kalıp şöyle:

```
Stellar Raven'ın [beceri adı] becerisini kullan.
[Ne yapmak istediğini anlat].
Becerinin önerdiği adımları takip et ve her adımda dayandığın kaynağı göster.
```

Beceriyi editörüne kurduysan Raven'ı anmana gerek yok. Asistan, isteğin becerinin kapsamına girdiğinde onu kendiliğinden kullanır.
