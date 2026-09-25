# Skill haritası

[← Ana sayfa](../README.md)

[skills.stellar.org](https://skills.stellar.org), Stellar üzerinde çalışan yapay zekâ asistanları için hazırlanmış skill'lerin kataloğu. Skill, asistanın belirli bir işi nasıl yapacağını anlatan bir talimat paketidir: bir kontrol listesi, bir inşa rehberi ya da bir araştırma yöntemi.

Skill'leri iki yoldan kullanabilirsin:

- **Raven üzerinden:** Bazı skill'ler Raven'ın içinde hazır gelir. Prompt'ta skill'in adını yazman yeterli (örneğin "`stellar-project-dossier` skill'ini kullan").
- **Editörüne kurarak:** Claude Code, Cursor gibi araçlarda skill'leri yerel olarak kurabilirsin. Kurulum talimatları katalog sayfasında.

> **Dikkat:** Katalogdaki skill'lerin bir kısmı SDF tarafından resmi olarak yazıldı, bir kısmı ise topluluk tarafından yazıldı ve SDF tarafından incelenmedi. Özellikle gerçek para hareket ettiren (ödeme, hazine yönetimi, köprü) topluluk skill'lerini kullanmadan önce içeriğini oku.

## Hangi prompt, hangi skill?

| Kit dosyası | İşine yarayacak skill'ler | Resmi mi? |
| :---------- | :------------------------ | :-------- |
| [01 · Problem doğrulama](../istemler/01-problem-dogrulama.md) | `stellar-builder-quickstart` | Topluluk |
| [02 · Stellar'ı doğru kullanmak](../istemler/02-stellar-teknoloji.md) | `standards`, `assets`, `dapp`, `data`, `smart-contracts` | Resmi (SDF) |
| [03 · Ekosistem araştırması](../istemler/03-ekosistem-arastirmasi.md) | `stellar-scout`, `stellar-ecosystem-scout`, `stellar-integration-finder`, `stellar-project-dossier`, `stellar-ecosystem-digest` | Topluluk |
| [04 · Türkiye senaryoları](../istemler/04-turkiye-senaryolari.md) | `stellar-anchor-skill`, `standards`, `dapp` | Topluluk + Resmi |
| [05 · Güvenlik ve kod incelemesi](../istemler/05-guvenlik-ve-kod-inceleme.md) | `soroban-common-mistakes`, `smart-contracts` (security.md, testing.md), `setup-stellar-contracts` | Topluluk + Resmi |
| [06 · İleri konular](../istemler/06-ileri-konular.md) | `agentic-payments`, `zk-proofs`, `cross-chain`, `dapp` (smart-accounts.md), `agent-browser-webauthn` | Resmi + Topluluk |
| [07 · Sunum ve hibe](../istemler/07-sunum-ve-hibe.md) | `scf-submission-radar`, `stellar-content-auditor` (S1'deki öğretme yöntemi prompt'un içinde, ayrı bir skill gerekmez) | Topluluk |

## Resmi SDF skill'leri kısaca

| Skill | Ne anlatır? |
| :---- | :---------- |
| `smart-contracts` | Soroban kontrat geliştirme: kurulum, depolama ve TTL, yetkilendirme, testler, güvenlik |
| `dapp` | JavaScript SDK, Freighter, Stellar Wallets Kit, passkey'li smart account'lar, işlem oluşturma ve gönderme |
| `assets` | Klasik varlıklar, trustline'lar, yetkilendirme bayrakları, clawback, SAC |
| `data` | Stellar RPC ve Horizon ile zincir verisi okuma, akış, sayfalama, indeksleme |
| `standards` | SEP ve CAP haritası, ekosistem projeleri, resmi bağlantılar |
| `agentic-payments` | x402 ve MPP ile makineden makineye ödemeler |
| `zk-proofs` | BLS12-381, BN254, Poseidon ile Soroban'da ZK doğrulama; Circom, Noir, RISC Zero |
| `cross-chain` | Circle CCTP, Axelar, zincirler arası takaslar |

## Skill'i prompt'ta kullanmak

Genel kalıp şöyle:

```
Stellar Raven'ın [skill adı] skill'ini kullan.
[Ne yapmak istediğini anlat].
Skill'in önerdiği adımları takip et ve her adımda dayandığın kaynağı göster.
```

Skill'i editörüne kurduysan Raven'ı anmana gerek yok. Asistan, isteğin skill'in kapsamına girdiğinde onu kendiliğinden kullanır.
