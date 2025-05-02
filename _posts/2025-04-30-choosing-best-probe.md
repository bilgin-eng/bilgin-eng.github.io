---
title: "Choosing the Best Passive or Active Probe"
date: 2025-04-30 16:00:00 +0300
categories: [Electronics, Probes]
tags: [Passive Probe, Active Probe, Oscilloscope, Impedance Matching, Signal Measurement]
---

## Choosing the Best Passive or Active Probe

Osiloskop ile sinyal ölçmeye başlarken bu işlemin probunuzun en ucundan başladığını unutmamak gerekir.  
**Pasif probunuz** ile **osiloskopunuzun empedans uyumsuzluğu**, ölçmek istediğiniz sinyalin genliğini büyük ölçüde etkileyebilir.

Probunuzun ve osiloskopunuzun empedans değerlerine göre osiloskopa aktarılan sinyal miktarını hesaplamak için şu basit formülü kullanabiliriz:

```
V_scope = V_probe × (Osc Input / (Probe + Osc Input))
```

Bu hesaba göre, osiloskop üzerindeki channel ayarlarından **1:10**, **1:5**, **1:100** gibi oranları seçerek doğru ölçüm yapabilirsiniz.  
Aynı marka ürünleri kullandığınızda osiloskop, bağlı olan probu tanır ve oranı otomatik olarak belirler.

---

## Aktif Prob Kullananlar İçin Uyarı

Eğer diferansiyel ölçüm yapan bir **aktif probe** kullanıyorsanız, probun ucu ile ground noktası **birbirine mümkün olduğunca yakın** olmalıdır.  
Aksi takdirde, yüksek frekanslı ölçümlerde performansınız **dörtte bire kadar** düşebilir.

---

## Probun Yük Etkisi (Probe Loading)

Probun iç yapısına baktığınızda, genellikle bir direnç ve bir kapasitör görürsünüz — bunlar paralel bağlıdır.  
“**Probe load**” dediğimiz etki, buradaki **kapasitans** değerinden kaynaklanır.

Formül:
```
Z = 1 / (2πfC)
```

Bu denklemden anlaşılacağı üzere, ölçmek istediğiniz sinyalin frekansı arttıkça, probunuz düşük empedanslı davranır ve **neredeyse kısa devre gibi çalışır**.  
Bu durumda sinyal **doğrudan ground'a akar**, dolayısıyla voltaj ölçümünüz geçersiz hale gelir.

---

Bu yüzden ölçüm yaparken probun tipini, empedans uyumunu ve frekans aralığını mutlaka göz önünde bulundurmalısınız.
