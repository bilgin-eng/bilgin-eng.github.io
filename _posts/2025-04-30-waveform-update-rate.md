---
title: "Oscilloscope Waveform Update Rate"
date: 2025-04-30 14:00:00 +0300
categories: [Electronics, Oscilloscope]
tags: [Waveform Update Rate, Keysight Signal Capture]
---

## Oscilloscope Waveform Update Rate

Osiloskop alırken dikkat etmemiz gereken en önemli özelliklerden biri **waveform update rate (WUR)** değeridir.

Peki nedir bu waveform update rate?  
WUR, alınan sinyallerin işlenmesi ve görüntülenmesi sürecinin saniyede kaç kez gerçekleştiğini gösterir.  
Yani bir sinyali aldınız; önce donanımsal bileşenlerden geçirip işlenmeye hazır hale getirdiniz, ardından işlediniz ve ekrana yansıttınız. Bu sürecin tamamı saniyede kaç kez tekrarlanabiliyor?

Burada kritik bir soru ortaya çıkar:  
Bu işlemler sürerken **yeni bir sinyal gelirse** ve bu sinyal önemli bilgiler içeriyorsa, osiloskobunuz onu kaçırabilir mi?

---

## WUR Neden Önemlidir?

Saniyede ne kadar çok sinyal alıp işleyip görüntüleyebilirseniz, **anormallikleri**, **geçici olayları** ve **önemli detayları** yakalama ihtimaliniz o kadar artar.

Örnek:  
10 saniye boyunca her 1 saniyede bir gelen sinyali izlemek istiyorsunuz. Ancak her sinyalin işlenmesi 2 saniye sürüyorsa, her seferinde bir sinyali kaçırırsınız.

---

## Keysight Farkı

Keysight osiloskopları bu konuda oldukça başarılıdır.  
FFT gibi fonksiyonel özellikler aktifken bile WUR değerinde ciddi bir düşüş yaşanmaz, yani gelen çoğu sinyal doğru şekilde işlenir ve görüntülenir.

---

## Diğer Üreticilerle Kıyaslama

Bazı üretici firmaların datasheet’lerinde WUR değeri çok yüksek görünebilir (örneğin 5.000.000/s).  
Ancak bu genellikle sadece **varsayılan (default) modda** geçerlidir.

FFT gibi bir özellik açıldığında bu değer bir anda **1.000/s** gibi düşük bir seviyeye inebilir.  
Bu da sizi yanıltabilir. Keysight bu değerleri koruma konusunda çok daha stabil çalışır.

---

## Yüksek WUR Dezavantaj Olabilir mi?

Evet, bazı durumlarda olabilir:

- Çok fazla veri işlemek CPU’yu zorlayabilir.
- Buffer tükenmesi durumunda sadece kısa süreli sinyaller yakalanabilir.
- İşlemci yeterince güçlü değilse, aşırı sinyal yığılması **parazitlere** yol açabilir.

Yani **yüksek WUR tek başına yeterli değildir**. Sistem optimizasyonu ve denge de gerekir.

---

## Evinizde Deneyin

- Osiloskobunuzda **rise trigger** modunu aktif edin.
- Bir **sinüs sinyali** yollayın.
- External trigger bağlantısını başka bir osiloskopa verin.
- Karşıdaki osiloskopta **counter modunu** açarak gerçek WUR değerini gözlemleyin.

---

## Son Not

Osiloskopla gözlem yeteneğimiz ne kadar yüksek olursa o kadar fazla detay yakalayabiliriz.  
Bunu göz açıp kapamaya benzetebiliriz.  
Hayatınızda her göz kırptığınızda 4 saniyelik bir karanlık yaşasaydınız, neleri kaçırırdınız?

İşte bu yüzden WUR, fark yaratan kritik bir özelliktir.
