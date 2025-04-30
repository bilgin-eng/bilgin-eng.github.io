---
title: "FFT with 3000T Keysight Oscilloscope"
date: 2025-04-30 13:00:00 +0300
categories: [Electronics, Oscilloscope]
tags: [FFT, Keysight, Sampling Rate, Frequency Domain]
---

## FFT with 3000T Keysight Oscilloscope

Öncelikle osiloskopun temel özelliklerinden bahsederken genellikle **sampling rate** ve **deep memory** kavramlarını konuşuruz.  
Peki bu özelliklerin bir sinyalin FFT'sini alırken — yani time domain'den frequency domain'e geçerken — etkileri nelerdir?

Hepimiz şu temel formülü biliriz:  
**Alınan yol = Hız × Zaman**  
Bunun gibi bir başka formülümüz ise:  
**Örnek Sayısı = Sampling Rate × Ayarlanan Zaman Aralığı**

Osiloskop kullanırken zaman aralığını artırdıkça sampling rate’in düştüğünü fark etmişsinizdir. Bunun nedeni bellekle ilgilidir çünkü osiloskobun kullanılabilir belleği sınırlıdır.  
Toplam bellek ihtiyacını hesaplarken şunu kullanırız:  
**ADC çözünürlüğü × Örnek Sayısı**

> “ADC nereden çıktı?” derseniz, açıklayalım:  
Kullanılan ADC’ye göre elimizdeki çözünürlük değişir. Elde ettiğimiz değerler genellikle 16-bit integer, 32-bit integer, double veya float gibi veri türlerinde olabilir. Bu da temsili ölçümün kaç digit içerdiğini belirler.

---

## FFT Alırken Zaman Alanı Neden Geniş Olmalı?

Osiloskoplarda FFT alırken **zaman alanını mümkün olduğunca geniş tutmalısınız**.  
Eğer sinyalinizin periyodu 1 saniye ise, FFT işlemi sırasında zaman aralığını örneğin **10 saniye gibi daha geniş bir değere** ayarlamanız gerekir.

Bunun nedeni Fourier Transform'un **time record** yapısıdır. Eğer time record düşükse, frekans domaininde frekanslar arasındaki boşluk artar ve sinyal daha kaba görünür.  
**İki frekans arası uzaklık = 1 / Time Record (TR)**

---

## FFT Gösterim Platformları Nelerdir?

FFT analizinde osiloskop arayüzünde karşınıza çıkabilecek bazı temel ayarlar şunlardır:

- **Start / Stop Frequency**
- **Center Frequency**
- **Span** (Stop - Start)

---

Bu yazıda osiloskopla FFT alma konusuna kısa bir giriş yaptık.  
İlerleyen yazılarda hem FFT hem de spektrum analizörlerinde FFT uygulamaları hakkında daha detaylı konuşacağız.
