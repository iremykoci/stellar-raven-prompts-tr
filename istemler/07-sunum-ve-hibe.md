# 07 · Sunum ve hibe

[← Ana sayfa](../README.md)

İyi bir proje, anlatılamadığı için kaybedebilir. Bu dosya iki şey için var: kendi ürününü ezberlemeden, gerçekten anlayarak anlatabilmen ve projeni hackathon sonrasında Stellar Community Fund (SCF) gibi fonlara taşıyabilmen.

## S1. Kendi ürününü adım adım öğren

Sunumda en çok zorlanılan an, jürinin hazırlanmadığın bir soruyu sormasıdır. Bunun çaresi ezber değil, ürünün nasıl çalıştığını gerçekten anlamaktır. Bu prompt, yapay zekâyı sana her seferinde tek bir kavramı öğreten bir öğretmene dönüştürür.

```
Benim ürünümü, bir yatırımcıya ya da jüriye kendi cümlelerimle anlatabileceğim kadar iyi anlamama yardım et.
Projem şu: [fikrini ve teknik akışını anlat].
Kurallar:
- Her seferinde sadece BİR kavramı anlat, sonra dur ve bir sonrakine geçmek isteyip istemediğimi sor.
- Önce 1-3 cümlelik doğrudan cevap ver. Sonra kavramı jargonsuz, neden var olduğundan başlayarak, benim ürünümden gerçek sayılarla bir örnekle açıkla.
- İşe yarıyorsa alternatifle karşılaştır: "Şunu değil de bunu yapıyoruz, çünkü..."
- Projemde neyin GERÇEK (çalışıyor), neyin TAKLİT (mock), neyin PLANLANAN, neyin VARSAYIM olduğunu her seferinde açıkça ayır. Emin olmadığın bir şeyi emin gibi söyleme.
- Her kavramın sonunda "Sunum cümlesi:" başlığıyla, jüriye aynen söyleyebileceğim 1-3 cümle yaz.
İlk kavram olarak şununla başla: [örneğin "kullanıcı parayı yatırdığında ne oluyor?"].
```

## S2. Jüri simülasyonu

```
Titiz bir Stellar hackathon jürisi gibi davran. Jüride bir teknik uzman, bir ürün uzmanı ve bir yatırımcı var.
Projem şu: [fikrini anlat], şu problemi çözüyor: [problemi anlat] ve Stellar'ı şunun için kullanıyor: [kullanımı anlat]. Demoda gerçekten çalışan kısım: [çalışan kısmı anlat].
Her jüri üyesi bana en zor iki sorusunu sorsun. Sorulardan sonra dur ve cevaplarımı bekle.
Cevaplarımı verdikten sonra her birini 1'den 5'e kadar puanla, zayıf cevapları nasıl güçlendirebileceğimi söyle.
```

## S3. Son öz değerlendirme

```
Projem şu: [fikrini anlat], şu problemi çözüyor: [problemi anlat] ve Stellar'ı şunun için kullanıyor: [kullanımı anlat].
Üç konuya 1'den 5'e kadar puan ver:
1. Gerçek bir problemi çözüyor muyum?
2. Stellar teknolojisini doğru kullanıyor muyum?
3. Demo'da gösterdiğim şey iddia ettiğim şeyi kanıtlıyor mu?
Her puan için neden o puanı verdiğini açıkla ve sunumdan önce puanı yükseltmek için yapmam gereken en önemli tek adımı söyle.
```

## S4. Sunum metnimi doğrula

Sunumunda ya da tanıtım yazında başka projelerden, rakamlardan veya ekosistemden bahsediyorsan:

```
Stellar Raven'ın stellar-content-auditor skill'ini kullan.
Aşağıdaki sunum metnimde geçen proje adlarını, rakamları ve iddiaları ekosistem verisiyle karşılaştır.
Yanlış yazılmış proje adlarını ve X (Twitter) hesaplarını düzelt, kaynağı olmayan iddiaları işaretle ve her doğrulanan bilgi için kaynak bağlantısı ekle.
Metnin Türkçe kalmasını istiyorum, sadece düzeltmeleri ve kaynakları ekle.

[sunum metnini buraya yapıştır]
```

## S5. SCF başvurusu için konumlan

```
Stellar Raven'ın scf-submission-radar skill'ini ve scout.getRfps aracını kullan.
Projem şu: [fikrini anlat]. Başvurmayı düşündüğüm program: [Instawards, Build Award, RFP].
1. SCF'e daha önce benzer bir proje başvurmuş mu? Fonlananlar ve fonlanmayanlar neler, aralarındaki fark ne?
2. Şu an açık bir SCF turu var mı, başvuru penceresi ne zaman kapanıyor? Tarihi kaynağıyla yaz.
3. Projemi önceki başvurulardan ayıran şeyi tek paragrafta yaz.
4. Başvurumda öne çıkarmam ve kaçınmam gereken şeyleri listele.
Resmi kurallar için SCF El Kitabı'na (stellar.gitbook.io/scf-handbook) bağlantı ver, kendi yorumunu resmi kural gibi sunma.
```

## S6. Başvurumu reddedilme riskine karşı tara

Aşağıdaki liste, topluluk içinde incelenen Instawards değerlendirmelerinden derlenmiş **gözlemlerdir, resmi kriter değildir**. Resmi kurallar için [SCF El Kitabı](https://stellar.gitbook.io/scf-handbook/scf-awards/instawards) esastır.

**Sık görülen ret nedenleri:**
- Kullanıcı anahtarlarının sunucuda saklanması (şifreli olsa bile)
- Stellar'da zaten yerleşik olan bir şeyi (claimable balance, SEP-24, yerleşik yetkilendirme) yeniden yazan özel kontratlar
- Fon hareket ettirme yetkisi insan onayı olmadan yapay zekâya bırakılmış sistemler
- Bütçede mühendislik dışı kalemler (barındırma, pazarlama, denetim, iş geliştirme)
- Ödeme adresinin Stellar dışında olması
- Süreye göre gerçekçi olmayan kapsam

**Sık görülen onay nedenleri:**
- Denetlenmiş, hazır yapı taşlarının üzerine inşa etmek
- İmzalamanın kullanıcının cihazında (passkey vb.) yapılması ve bunun bir testle kanıtlanması
- Yapay zekânın sadece öneri veren konumda tutulması, insan onayı olmadan fon hareket ettirememesi
- Ajan harcamalarına zincir üzerinde zorunlu sınırlar konması
- Bütçenin tamamının mühendislik emeğine ayrılması ve kapsam dışı kalemlerin açıkça yazılması
- Benzer projelerden farkın açıkça ortaya konması

Bir gözlem daha var: Aynı mimariyle önce reddedilen bazı projeler, sadece testnet ile sınırlandırılıp mainnet geçişi için açık bir plan ve koruma taahhüdü eklendiğinde onaylandı. Yani risk sınırlandırılıp kanıtlanırsa kural esneyebiliyor, sadece beyan etmek yetmiyor.

```
Aşağıda hibe başvurumun taslağı var. Şu risklere karşı tara ve her biri için "risk yok", "risk var" veya "belirsiz" yaz, risk varsa nasıl düzelteceğimi öner:
1. Kullanıcı anahtarları sunucuda mı tutuluyor?
2. Stellar'da yerleşik olan bir şeyi yeniden mi yazıyorum?
3. Yapay zekâ insan onayı olmadan fon hareket ettirebiliyor mu?
4. Bütçede mühendislik dışı kalem var mı?
5. Kapsam, verilen sürede gerçekçi mi?
6. Benzer projelerden farkım açıkça yazılmış mı?
7. Riskli bir kısım varsa, onu testnet ile sınırlayan ve sonradan nasıl genişleyeceğini anlatan bir plan var mı?

[başvuru taslağını buraya yapıştır]
```

## Sunumdan önce kontrol listesi

- [ ] Problemi tek cümleyle anlatabiliyorum ve kimin canını yaktığını biliyorum.
- [ ] Ekosistemde benzer bir şeyin olup olmadığını Raven'la kontrol ettim ve farkımı söyleyebiliyorum.
- [ ] Projemin Stellar'ın hangi özelliğini veya standardını kullandığını ve nedenini biliyorum.
- [ ] Soroban'a mı ihtiyacım olduğu, yoksa klasik Stellar'ın yeterli mi olduğu konusunda netim.
- [ ] Demo'da neyin gerçek, neyin taklit olduğunu açıkça söyleyebiliyorum.
- [ ] Stellar'ın bir süs değil, gerçek bir değer kattığını gerekçelendirebiliyorum.
- [ ] Repomda gizli anahtar yok ve kullanıcı anahtarları sunucuda tutulmuyor.
- [ ] Hackathon sonrası için sonraki adımlarım ve olası fon kaynağım belli.

[← Önceki: 06 · İleri konular](06-ileri-konular.md) · [Ana sayfa](../README.md)
