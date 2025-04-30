---
title: "Vertical Accuracy"
date: 2025-04-30 12:00:00 +0300
categories: [Electronics, Measurement]
tags: [Vertical Accuracy, Oscilloscope]
---

Vertical accuracy dediğimiz zaman aklımıza temel bir formül gelmeli. 

**ADC resolution Bit + Lowest Noise floor = Vertical accuracy**

ADC bitleri ve resolution'dan bahsedecek olursak eğer şu şekilde örnek vererek tanımlayabiliriz:

Elimizde 8 bitlik bir ADC olsun. Bu ADC'nin quantization level sayısı = 2^8'dir. Bu şu anlama gelir: vertical olarak biz 256 parçaya bölerek işlem gerçekleştirebiliriz. Eğer ADC bitimizi arttırırsak örneğin 14 bits, 2^14'ten 16384 quantization level'ımız olur. Burada bize sağladığı avantaj şu olur: Bir sinus dalgasını düşünelim, bu sinus dalgasının tepe değeri 2V olsun. Eğer 8 bitlik ADC kullanırsak 2V/256'lık bir çözünürlüğe sahip oluruz. 14 bitlik ADC kullanırsak 2V/16384 olarak çözünürlüğümüz olur. Bu da sinyali analiz etmemizde ve ufak değişimleri gözlemlememizde büyük olanak sağlar. Elbette ki bu sayede ölçebileceğimiz minimum sinyal değeri de değişmiş olur. Örneğin 8 bitlik ADC'de minimum 2/256 V'luk sinyali ölçebilirken, 14 bit ADC'de ise 2/16384 V'luk sinyali ölçebiliyoruz.

Örneğin osiloskopta sinyali ölçerken input amplifier/attenuator yapısı sinyal analizi için önemli bir yer tutmaktadır. Peki nasıl? Ölçmek istediğimiz sinyal düşük genlikli bir sinyal olabilir. Biz bu sinyali amplify etmezsek eğer ADC'yi tam olarak besleyemeyiz. Bizim ölçüm yaparken tam verimlilik istiyorsak ADC'nin bütün bitlerini efektif bir şekilde kullanmamız gerekir. Bunu ise gelen sinyali ADC kapasitemize göre attenuator ya da amplifier yardımı ile ADC'nin bitlerini efektif kullanabilmek adına sinyal üzerinde işlem gerçekleştiririz. Diğer bir konu ise osiloskoplardaki yazılımsal ve donanımsal olarak amplify etmedir. Eğer elinizde Keysight HD3 varsa ve küçük bir sinyal ölçmeye çalışıyorsanız osiloskop bu sinyali ölçebilmek için amplify etmeye çalışacaktır. Peki bunu donanımsal olarak mı sağlayacak yoksa yazılımsal olarak mı? Keysight HD3 2mV/div’e kadar donanımsal olarak çalışıyor fakat diğer osiloskop firmalarında bu sınır 7mV’tur. 7mV’tan daha küçük sinyallerde yazılımsal olarak büyütmeye çalışır. Bu da bir resolution karakteristiğidir aslında.

Gelelim şimdi osiloskopun kendi iç gürültüsüne. Biliyoruz ki sinyaller dış ortamlarda bozulmaya uğrar ve gürültü eklenmiş hale gelir. Peki osiloskop içerisinde her şey ideal mi? Hayır. Bu yüzden Keysight osiloskopları cihaz içi donanım tasarımından ön uç ve problarına kadar her şeyi sinyale en az gürültü ekleneceği şekilde tasarlamaya çalışır. 

Bu cihaz gürültüsü bize neye mal olur? Örneğin biz bir zayıf sinyal tasarladığımız sistemde negatif etkilere sebep oluyor ve bizim bunu tespit etmemiz lazım ki bu sinyal ne zaman nerede oluşuyor. Burada bu zayıf sinyali ölçerken bir limitation devreye giriyor: **Noise floor!**

Diyelim ki tespit etmek istediğimiz sinyal 2µV seviyesinde fakat bizim osiloskobumuzun kendi içerisinde gürültü tabanı 20µV yani ölçmek istediğimiz sinyalden daha büyük. Siz uzun boylu birisinin arkasındaki kısa boylu birisini görebilir misiniz? Keysight osiloskoplarında noise tabanı diğer satıcılara göre çok daha aşağıda olduğu için zayıf sinyalleri görebilir ve teşhis edebilirsiniz.

---

### QUIZ:

**ENOB (Effective Number of Bits) nedir ve vertical accuracy üzerindeki etkisi nasıldır?**

ENOB yani effective number of bit cihaz içerisinde tasarlanan ADC'nin ölçüm için kullanılabilen bit sayısıdır. Şu şekilde örnek verecek olursak eğer: ADC'ye gelen sinyaliniz noise içermiyorsa ADC'nin bütün bitlerini efektif bir şekilde kullanabilirsiniz. Gerçek dünyada bu mümkün değildir; o yüzden sinyal gürültü içerecektir ve biz bu sinyali ADC'ye çözümlemesi için gönderdiğimizde ADC bitlerinin bir kısmı bu gürültü ile meşgul olacaktır.

Total bit sayısından gürültü ile ilgilenen bit sayılarını çıkartırsak eğer ENOB değerini elde etmiş oluruz. Keysight, ENOB değeri en yüksek osiloskoptur. Çünkü iç gürültüsü çok azdır ve ölçmek istediğiniz sinyali gönül rahatlığı ile analiz edebilirsiniz.

---

**Noise floor ile sinyal seviyesinin ilişkisini bir grafikle gösterecek olsan, nasıl çizerdin?**



---

**Yazılımsal gain'in sınırlamaları nelerdir?**

Bir sinyali yazılımsal olarak büyütmek demek, SNR (Signal to Noise Ratio) değerinin sabit kalması demektir. Ama biz bunu donanım tabanlı gerçekleştirirsek SNR değerini daha doğru ölçmüş oluruz.

---

**Donanımsal gain kullanılırken dikkat edilmesi gereken bir risk var mı?**


