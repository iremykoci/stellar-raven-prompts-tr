# Stellar Raven Prompt Kit (Turkish)

> A collection of ready-to-use, copy-and-paste prompts **in Turkish** for **Stellar Raven**, the official MCP server of the Stellar ecosystem. Use it as a copilot to build and validate your project, whether you are at a hackathon or shipping your first Stellar app.

Every prompt in this kit helps you answer two questions:

1. Am I solving a real problem?
2. Am I using Stellar's technology well?

The prompts are written in Turkish so Turkish-speaking builders can use them as-is. The rest of this README is in English so anyone can understand and contribute to the kit.

## Table of contents

1. [What is this kit?](#what-is-this-kit)
2. [Before you start: connecting Raven](#before-you-start-connecting-raven)
3. [How to use the prompts](#how-to-use-the-prompts)
4. [Block A. Am I solving a real problem?](#block-a-am-i-solving-a-real-problem)
5. [Block B. Am I using Stellar well?](#block-b-am-i-using-stellar-well)
6. [Block C. Scenarios for Türkiye](#block-c-scenarios-for-türkiye)
7. [Final self-assessment prompt](#final-self-assessment-prompt)
8. [How to read Raven's answers](#how-to-read-ravens-answers)
9. [Pre-pitch checklist](#pre-pitch-checklist)
10. [Resources](#resources)
11. [Credits and contributing](#credits-and-contributing)

## What is this kit?

Stellar Raven is an MCP (Model Context Protocol) server run by the SDF (Stellar Development Foundation). In plain terms, it connects your AI assistant to Stellar's official documentation and to live ecosystem data, so its answers are backed by real, up-to-date sources instead of guesses.

This kit helps you get the most out of that with well-structured questions. Instead of improvising prompts from scratch, you get tested templates you can adapt to your project in seconds.

Keep in mind: Raven helps you check technical feasibility and fit with Stellar. It does not replace a jury's evaluation or your own judgment.

## Before you start: connecting Raven

There are two options, depending on how much you want to install.

**Option 1: the browser playground.**
Nothing to install. Open Raven's chat, sign in, and start asking.

```
https://raven.stellar.buzz/playground
```

**Option 2: connect Raven to your editor.**
If you use Claude Code, Cursor, or VS Code, you can add Raven with a single command and use it inside your development environment. Example for Claude Code:

```bash
claude mcp add --transport http stellar-raven "https://raven.stellar.buzz/mcp"
```

Then run your client's authentication command (`/mcp` in Claude Code) and sign in when the browser opens.

## How to use the prompts

Three steps:

1. Pick the prompt that matches what you need to figure out right now.
2. Replace the text in square brackets (for example `[fikrini anlat]`, "describe your idea") with your project's real details.
3. Paste the prompt into the Raven playground or your editor and read the answer carefully.

Tip: the more specific you are about your project, the more useful the answer will be.

## Block A. Am I solving a real problem?

These prompts help you confirm your project starts from a concrete need, not from a technology looking for an excuse.

### A1. Define and sharpen the problem

```
Projemi anlatacağım, gerçek bir problemi çözüp çözmediğini değerlendirmeni istiyorum.
Projem şu: [fikrini iki üç cümleyle anlat].
Eleştirel bir gözle analiz et:
1. Problem tam olarak ne ve kimi etkiliyor?
2. Bu sık yaşanan ve can yakan bir problem mi, yoksa küçük bir rahatsızlık mı?
3. Bu problemi yaşayanlar bugün onu çözmek için para ya da emek harcıyor mu?
Kısa bir liste halinde cevap ver ve problemin tek cümlelik, geliştirilmiş bir tanımıyla bitir.
```

### A2. Is it a solution looking for a problem?

```
Fikrimin problem arayan bir çözüm olup olmadığını öğrenmek istiyorum.
Fikrim şu: [çözümünü anlat].
Çözdüğümü düşündüğüm problem şu: [problemi anlat].
Problemin bu çözümü gerçekten gerektirip gerektirmediğini, yoksa teknolojiden yola mı çıktığımı dürüstçe söyle.
Eğer çözümden başladığımı fark edersen, projeyi probleme odaklamak için iki farklı yol öner.
```

### A3. Find similar solutions in the Stellar ecosystem

```
Stellar Raven'ı kullanarak dokümantasyonda ve ekosistem verilerinde arama yap.
Projem şu problemi çözmeyi hedefliyor: [problemi anlat].
Stellar ekosisteminde buna benzer bir şeyi ele alan projeler, araçlar veya standartlar var mı, söyle.
Her biri için fikrime nerede benzediğini ve nerede ayrıldığını belirt, varsa resmi kaynağı da göster.
```

### A4. Describe the user and their journey

```
Ana kullanıcımı tarif etmeme yardım et.
Projem şu: [fikrini anlat].
Kullanıcı için kısa bir profil çıkar (kim, neye ihtiyacı var, benim çözümüm olmadan bugün ne yapıyor).
Sonra projemi baştan sona nasıl kullanacağını basit adımlarla anlat.
Stellar'ın başka bir teknolojinin veremeyeceği bir değer kattığı adımı işaretle.
```

### A5. The "what if Stellar didn't exist?" test

```
Stellar'a gerçekten ihtiyacım var mı, yoksa süs olarak mı kullanıyorum, bunu anlamak istiyorum.
Projem şu: [fikrini anlat] ve Stellar'ı şunun için kullanmayı planlıyorum: [kullanımı anlat].
Aynı problemi blokzincir olmadan, klasik bir veritabanıyla çözseydim ne olurdu, açıkla.
Sonra somut argümanlarla Stellar'ı kullanmanın bana ne kazandırdığını (örneğin ödemeler, varlıklar, şeffaflık veya birlikte çalışabilirlik) ve bu değerin benim durumum için gerçek olup olmadığını söyle.
```

## Block B. Am I using Stellar well?

These prompts help you check that Stellar fits your solution correctly and that you are picking the right building blocks.

### B1. Find the right technical fit

```
Stellar Raven'ı kullan ve resmi dokümantasyona dayan.
Projem şu: [fikrini anlat] ve Stellar üzerinde yapmak istediğim şey şu: [işlevi anlat].
Hangi Stellar özelliğinin en iyi uyduğunu söyle (örneğin ödemeler, varlık veya token çıkarma, path payment, merkeziyetsiz borsa (SDEX), anchor'lar ya da Soroban akıllı kontratları).
Önerini gerekçelendir ve dayandığın dokümantasyon bölümünü göster.
```

### B2. Identify the relevant standards (SEPs)

```
Stellar Raven'ı kullanarak ekosistem standartlarını (SEP) incele.
Projemin ihtiyacı şu: [ihtiyacı anlat, örneğin yerel parayla bağlantı kurmak, kullanıcı doğrulamak veya token çıkarmak].
Benim durumum için hangi SEP'lerin geçerli olduğunu, her birinin ne işe yaradığını ve hangi sırayla incelemem gerektiğini söyle.
Var olmayan ya da işime yaramayan bir SEP'ten bahsedersem beni düzelt.
```

### B3. Soroban or classic Stellar?

```
Mimariye karar vermeme yardım et.
Projemin ana mantığı şu: [ana mantığı anlat].
Stellar dokümantasyonuna dayanarak bunu klasik Stellar işlemleriyle mi çözmem gerektiğini, yoksa Soroban akıllı kontratlarına mı ihtiyacım olduğunu söyle.
Zamanı kısıtlı bir hackathon ekibi için iki yolun avantajlarını ve maliyetlerini açıkla.
```

### B4. Design a minimal architecture

```
Stellar Raven'ı kullanarak bana minimum bir mimari çıkar.
Projem şu: [fikrini anlat].
Bir prototip için gereken parçaları listele (örneğin testnet, uygun SDK, Horizon veya RPC, Freighter gibi bir cüzdan) ve her birini tek cümleyle anlat.
İlk çalışan versiyona ulaşmak için adımları sırasıyla yazarak bitir.
```

### B5. Is it feasible in the hackathon timeframe?

```
Kalan süreme göre gerçekçi bir plan istiyorum.
Projem şu: [fikrini anlat] ve elimde [kalan saati veya günü yaz] var.
Bu sürede Stellar üzerinde gerçekten hangi kısmı inşa edebileceğimi, hangi kısmı ise sadece fikir olarak sunmamın daha doğru olacağını söyle.
Canlı demo yapılabilecek minimum bir kapsam öner.
```

### B6. Avoid common mistakes

```
Stellar Raven'ı kullanarak iyi uygulamaları gözden geçir.
Stellar'daki teknik yaklaşımım şu: [Stellar'ı nasıl kullanmayı planladığını anlat].
Kaçınmam gereken yaygın hataları, yaklaşımımda gördüğün kötü uygulamaları ve bunları nasıl düzelteceğimi söyle; uygun olan yerlerde dokümantasyonu kaynak göster.
```

## Block C. Scenarios for Türkiye

If you are building for users in Türkiye, these prompts help you map local needs to Stellar's building blocks.

### C1. Turkish lira on/off-ramp

```
Stellar Raven'ı kullan ve anchor'larla ilgili resmi dokümantasyona dayan.
Projemde kullanıcıların Türk lirası ile Stellar'a girip çıkabilmesi gerekiyor: [akışı anlat, örneğin TL yatırıp USDC almak].
Bu akış için hangi SEP'leri (örneğin SEP-10, SEP-24, SEP-6, SEP-31) kullanmam gerektiğini, kullanıcı tarafında adımların nasıl ilerleyeceğini ve testnet'te bunu nasıl deneyebileceğimi anlat.
Ekosistemde TL destekleyen anchor'lar hakkında bilgi varsa kaynağıyla birlikte göster, doğrulanamıyorsa bunu açıkça belirt.
```

### C2. Cross-border transfers and remittances

```
Stellar Raven'ı kullan.
Projem şu kullanıcıların sınır ötesi para gönderme sorununu çözmeyi hedefliyor: [kimin kime, hangi ülkeye para gönderdiğini anlat].
Bugünkü yöntemlerle (banka havalesi, SWIFT, döviz bürosu, uygulamalar) kıyaslayınca Stellar'ın hangi noktada gerçek fark yarattığını açıkla.
Path payment ve anchor'ların bu akışta nasıl bir rol oynayacağını adım adım göster ve yasal uyumluluk (KYC/AML) açısından dikkat etmem gereken noktaları listele.
```

### C3. A user experience for non-crypto users

```
Projem şu: [fikrini anlat] ve hedef kitlem kripto deneyimi olmayan Türkiye'deki kullanıcılar.
Stellar Raven'ı kullanarak, kullanıcının seed phrase veya cüzdan kavramlarıyla boğulmadan uygulamamı kullanabilmesi için hangi seçeneklerim olduğunu söyle (örneğin passkey tabanlı smart account'lar, ücret sponsorluğu, cüzdan kitleri).
Her seçeneğin hackathon süresinde uygulanabilirliğini ve dokümantasyondaki yerini belirt.
```

## Final self-assessment prompt

Use this once your project is well underway, right before you prepare your pitch. It combines both questions into a single evaluation.

```
Titiz bir hackathon jürisi gibi davran.
Projem şu: [fikrini anlat], şu problemi çözüyor: [problemi anlat] ve Stellar'ı şunun için kullanıyor: [kullanımı anlat].
İki konuya 1'den 5'e kadar puan ver: gerçek bir problemi çözüp çözmediğim ve Stellar teknolojisini doğru kullanıp kullanmadığım.
Her puan için neden o puanı verdiğini açıkla ve sunumdan önce puanı yükseltmek için yapmam gereken en önemli adımı söyle.
```

## How to read Raven's answers

To get the most out of Raven, keep these in mind:

- Raven relies on official documentation and ecosystem data, so always ask it to cite its sources. If an answer cites nothing or sounds generic, ask again and request the source.
- Raven checks technical feasibility and fit with Stellar. It does not judge your business viability or the quality of your pitch.
- Before building anything important on top of an answer, cross-check it against the official documentation. AI speeds up your work, but the final call is yours.

## Pre-pitch checklist

Tick each item once you can answer it with confidence.

- [ ] I can explain the problem in one sentence and I know who it hurts.
- [ ] I checked whether something similar already exists in the Stellar ecosystem.
- [ ] I know which Stellar feature or standard my project uses, and why.
- [ ] I know whether I need Soroban or whether classic Stellar is enough.
- [ ] I defined a minimum scope I can demo live.
- [ ] I can justify why Stellar adds real value and is not just decoration.
- [ ] My next steps after the hackathon are ready.

## Resources

| Resource                                         | Link                                                               |
| :----------------------------------------------- | :----------------------------------------------------------------- |
| Stellar Raven (browser playground)               | https://raven.stellar.buzz/playground                              |
| Stellar docs, Building with AI section           | https://developers.stellar.org/docs/build/building-with-ai         |
| Official Stellar documentation                   | https://developers.stellar.org                                     |
| Stellar Raven repository                         | https://github.com/kalepail/stellar-raven                          |
| SEPs (Stellar Ecosystem Proposals)               | https://github.com/stellar/stellar-protocol/tree/master/ecosystem  |
| Soroban smart contracts                          | https://developers.stellar.org/docs/build/smart-contracts/overview |
| Community (Stellar Developer Discord)            | https://discord.gg/stellardev                                      |

## Credits and contributing

This kit is inspired by Alex Hernández's Spanish [Kit de Prompts para Stellar Raven](https://github.com/alex0tico/stellar-raven-prompts). It adapts the prompts to Turkish and extends them with scenarios for builders in Türkiye.

Suggestions for new prompts and corrections are welcome. Feel free to open an issue or a pull request.
