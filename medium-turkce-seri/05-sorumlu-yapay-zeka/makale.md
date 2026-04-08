# 5. Ders — Sorumlu Yapay Zekâ: Güçlü Sistemler Yetmez, Güvenilir Sistemler Gerekir

## Giriş

Serinin son dersi teknik olmaktan çok önemsiz değil; tam tersine, üretime çıkan AI sistemlerinin en kritik katmanını ele alıyor. Bir modeli çalıştırmak mümkündür. Ama onu güvenli, adil ve denetlenebilir hale getirmek gerçek mühendislik işidir.

## Neden bu konu ayrı bir makale olmalı?

Çünkü çoğu ekip üretken yapay zekâ projelerinde şu sırayı izliyor:
1. Önce prototip çıkar.
2. Sonra kullanıcı gelir.
3. En son güvenlik ve etik düşünülür.

Oysa doğru sıra bunun tersine daha yakındır. Özellikle karar destek, içerik üretimi, müşteri etkileşimi ve ajan senaryolarında sorumlu AI baştan tasarlanmalıdır.

## Bu dersteki dört ana başlık

- bias ve adalet
- content safety
- transparency / explainability
- responsible agents

## Bias neden yalnızca veri problemi değildir?

Önyargı yalnızca eğitim verisinden gelmez. Prompt tasarımı, tool kullanımı, değerlendirme biçimi ve insan geri bildirimi döngüsü de sistemi belirler. Bu yüzden makalede “bias kontrolü tek seferlik temizlik değil, yaşam döngüsü disiplini” mesajı verilmelidir.

## Content safety ve guardrail yaklaşımı

Repo bu derste Azure OpenAI filtreleri, Azure AI Content Safety, Prompt Shields ve groundedness gibi başlıkları öne çıkarıyor. Medium makalesi için burada verilebilecek en net mesaj şu olabilir: “LLM çıktısı uygulama çıktısıdır; sorumluluk modelde değil, üründedir.”

## Şeffaflık neden güven üretir?

Kullanıcılar üç şeyi bilmeli:
- AI ile konuştuklarını
- cevabın ne kadar güvenilir olduğunu
- sistemin neye dayanarak bu cevabı ürettiğini

Özellikle RAG tabanlı sistemlerde kaynak gösterimi, agent tabanlı sistemlerde ise karar izi tutmak güvenin temelidir.

## Ajanlarda risk neden daha yüksek?

Bir chatbot yanlış cevap verebilir. Bir ajan ise yanlış işlem yapabilir. Bu yüzden insan onayı, yetki sınırları, geri alınabilir aksiyonlar ve acil durdurma mekanizmaları opsiyon değil gerekliliktir.

Bu dersi Medium'da yayınlarken, önceki makalelerde anlatılan bütün teknik gücün burada kontrollü hale getirildiği vurgulanmalı.

## Sonuç

Serinin finalinde okuyucunun alacağı mesaj net olmalı: iyi AI uygulaması sadece çalışan değil, güven veren uygulamadır. Eğer bu seri Türkçe yayımlanacaksa, son makale teknik bir kapanıştan çok bir mühendislik manifestosu gibi konumlandırılabilir.
