---
title: "Sampling Rate"
date: 2025-04-30 15:00:00 +0300
categories: [Electronics, Oscilloscope]
tags: [Sampling Rate, Nyquist, ADC, Interleave Distortion, Signal Processing]
---

## Sampling Rate

Osiloskopların ekranının üst kısmında genellikle şöyle bir ifade görürüz: **X Sa/s**  
Gözümüzün önüne bu kadar sık yazılan bu değer neden bu kadar önemlidir?

Bir probu osiloskopa bağladıktan sonra sinyal üzerinde birçok işlem gerçekleştirebiliriz. Bu işlemler toplama, çıkarma, türev, FFT ve daha karmaşık analizler olabilir. Hatta sinyalin bazı özelliklerini depolayabiliriz.  
Peki analog bir sinyali doğrudan CPU’da işleyebilir miyiz veya depolayabilir miyiz? Bu işlemleri analog sinyal üzerinde gerçekleştirebilecek donanımı tasarlamak kolay mı?  
Cevap: **Hayır.**

Bu karmaşıklığı aşmak için mühendisler analog sinyali dijital hale getirmek adına örnekleme (sampling) yöntemini geliştirmiştir.  
Bir analog sinyali **discrete time** sinyale çevirmek ve daha sonra ADC ile dijitale dönüştürmek bu sorunu çözer.

---

## Sampling Rate Neden Bu Kadar Önemli?

Sampling işlemini yapan donanımın en önemli özelliği **sampling rate**’idir.  
Analog sinyalden ne kadar fazla örnek alırsak, sinyali o kadar iyi analiz edebilir, daha güvenilir sonuçlar elde ederiz.

Hayal edin:  
Elinizde 3 saniye periyotlu bir sinyal var ve siz her 1 saniyede bir örnek alıyorsunuz. Sinyal geldiği anda örnekleme yaptığınızı varsayalım.  
Sonuçta bu örnekleri birleştirince dümdüz bir DC sinyali elde edersiniz.  
Yani sinyalin karakteristiğini ortaya çıkaramazsınız!  
Bu nedenle **yüksek sampling rate**, sinyalin tüm detaylarını yakalamak için şarttır.

---

## Evde Deneyin

- Osiloskopa bir sinüs sinyali iletin.
- Zaman tabanını geniş bir şekilde ayarlayın.
- **Single sweep** atın ve sinyali yakınlaştırın.

Garip şekiller fark ederseniz, sebebi düşük sampling rate olabilir.

---

## Sampling Rate ve Glitch Tespiti

Yüksek sampling rate, sinyaldeki **ani sıçramaları (glitch)** ve **anormallikleri** yakalamak açısından da kritiktir.  
Eğer örnekleme sırasında bu noktaları atladıysanız, sisteminizin düzgün çalıştığını sanabilirsiniz — bu büyük bir yanılgıdır.

---

## Ne Kadar Sampling Rate Gerekir?

Bu sorunun cevabı duruma göre değişir. Filtre tipi, frekans tepkisi, bant genişliği gibi birçok parametre etkilidir.  
Ama temel bir formül verelim:

**Sampling Rate ≈ 4 × Bandwidth**

Nyquist bize 2×BW demişti, ancak pratikte ideal filtreler yoktur, bu yüzden daha yüksek oranlar tercih edilir.

> Not: Osiloskoplarda birden fazla kanal kullanıldığında sampling rate genellikle **paylaştırılır.**

---

## Çok Yüksek Sampling Rate ve Interleave Distortion

Yüksek sampling rate elde etmek için bazen birden fazla sampler ve ADC kullanılır.  
Ancak bu yöntem **interleave distortion** denen bir bozulmayı getirebilir.

Örnekleme işlemi saat darbeleri (clock) ile yapılır.  
Nyquist’in bir uyarısı vardı: “Her iki örnek arasındaki zaman farkı eşit olmalı.”

Farklı clock’lar kullanırken bu zaman farklarını korumak zor olabilir. Clock kaymaları, sinyalde bozulmalara neden olur.

---

## Bozulmayı Anlamanın Yolu

- FFT alın
- Harmonik bileşenleri inceleyin
- 2., 3. ve 4. harmonik dışında büyük sıçramalar varsa
- Ve bu sıçramalar sinyalinizle benzer büyüklükteyse

Bu, interleave distortion olabilir. Dikkatli olmanızda fayda var.
